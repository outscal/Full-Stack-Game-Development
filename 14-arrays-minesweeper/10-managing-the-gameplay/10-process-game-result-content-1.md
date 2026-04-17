In this lesson, let's add proper win and loss handling to our Minesweeper game!



Update `Board.h` and `GameplayManager.h` files.

> **Summary📃**
> Here's what is added in the Board class:
> **🔸**`areAllCellsOpen` function to check if all the cells are open
> 🔸`flagAllMines` function to flag all mines



`Board.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>
#include <random>
#include "../../header/GameLoop/Gameplay/Cell.h"
#include "../../header/Event/EventPollingManager.h"
#include "../../header/Sound/SoundManager.h"

namespace Gameplay
{
		//previous code
    class Board
    {
    //previous code
    public:
				//previous code

        bool areAllCellsOpen();
        void flagAllMines();
        
        //previous code
    };
}


```





> **Summary📃**
> Here's what is added in the `GameplayManager` class:
> 🔸`gameWon` and `gameLost` functions to handle game win and loss.
> 🔸`checkGameWin` function to check the game win condition.
> 🔸`processGameResult` function to handle the `game_result`



`GameplayManager.h`

```cpp
#pragma once
#include "../../header/GameLoop/Gameplay/Board.h"
#include "../../header/Event/EventPollingManager.h"

#include <SFML/Graphics.hpp>

namespace Gameplay
{
    //previous code
    class GameplayManager
    {
    private:
				//previous code
        void gameWon();
        void gameLost();

				//previous code
    public:
			//previous code
        void checkGameWin();
        void processGameResult();
    };
}
```





Now we can update our gameplay loop:

If the game has ended but the board is not in a completed state, then implement the logic for game win and game loss.



`GameplayManager.cpp`

```cpp
void GameplayManager::update(EventPollingManager& eventManager, sf::RenderWindow& window) {
    if (!hasGameEnded())
        handleGameplay(eventManager, window);
    else if (board->getBoardState() != BoardState::COMPLETED)
        processGameResult();  // Handle win/loss
}
```



> **TODO**: 
> ✅ Update the `update` method in the `GameplayManager` class.



Now, before processing the game result, you need to figure out a win condition.



## Checking the Win Condition


---



We already have two conditions for game loss but none for game won.

When can the player win the game?🤔

When the player has opened all the non-mine cells, the player Wins!

So we need to check if the player has won the game after the board is updated:



`GameplayManager.cpp`

```cpp
void GameplayManager::handleGameplay(EventPollingManager& eventManager, sf::RenderWindow& window) {
    updateRemainingTime();
    board->update(eventManager, window);
    checkGameWin();  // See if player has won
}

void GameplayManager::checkGameWin() {
    if (board->areAllCellsOpen()) {
        game_result = GameResult::WON;  // Victory!
    }
}
```



**Note: **We are checking for win at every frame because we never know when the player has opened all the cells, hence we always need to check if the player has opened all the cells.



We need to know if all non-mine cells are open:

- Traverse through the board and track the number of all the non-mine cells that are open.
- Then compare the number of open cells with (**total cells** - **number of mines**).
- - If both are equal then all the non-mine cells are open.(Game Win)

`Board.cpp`

```cpp
bool Board::areAllCellsOpen() {
    int total_cells = numberOfRows * numberOfColumns;
    int open_cells = 0;

    for (int row = 0; row < numberOfRows; ++row) {
        for (int col = 0; col < numberOfColumns; ++col) {
            if (cell[row][col]->getCellState() == CellState::OPEN &&
                cell[row][col]->getCellType() != CellType::MINE) {
                open_cells++;
            }
        }
    }

    return open_cells == (total_cells - minesCount);
}
```



> **TODO**: 
> ✅ In `GameplayManager.cpp` implement the `handleGameplay`, and `checkGameWin` methods. 
> ✅ In `Board.cpp` implement `areAllCellsOpen` method.



You have a win condition now!

Now, let’s implement the logic of win and loss conditions.



# Process Game Result


---



Now, to handle the results, you need to implement `processGameResult()` method:

- Call the `gameWon()` method for `WON` result
- Call the `gameLost()` method for `LOST` result.



`GameplayManager.cpp`

```cpp
void GameplayManager::processGameResult() {
    switch (game_result) {
    case GameResult::WON:
        gameWon();    // Victory! 🎉
        break;
    case GameResult::LOST:
        gameLost();   // Game Over! 💥
        break;
    default:
        break;
    }
}
```

Let’s start with the game-win condition!



## Game Win


---



Now, think about what should happen when a player wins the game 🤔

- Play a game win sound
- Flag All Mines to confirm that the player has WON.
- Stop the game Or Wait for the Player’s next input.



`GameplayManager.cpp`

```cpp
void GameplayManager::gameWon() {
    Sound::SoundManager::PlaySound(Sound::SoundType::GAME_WON);  // Play victory sound
    board->flagAllMines();  // Show all mines
    board->setBoardState(BoardState::COMPLETED);  // Stop the game
}

```



You need to implement the `flagAllMines` method in the `Board` class.

- You can use the same approach to traverse the array.
- Then for each cell confirm that it is a mine and is not already flagged by the player:



`Board.cpp`

```cpp
void Board::flagAllMines() {
    for (int row = 0; row < numberOfRows; ++row) {
        for (int col = 0; col < numberOfColumns; ++col) {
            if (cell[row][col]->getCellType() == CellType::MINE &&
                cell[row][col]->getCellState() != CellState::FLAGGED) {
                cell[row][col]->setCellState(CellState::FLAGGED);
            }
        }
    }
}
```



> **TODO**: 
> ✅ In `GameplayManager.cpp` implement `processGameResult` and `gameWon` methods. 
> ✅ In `Board.cpp` implement `flagAllMines` method.



The game-win condition is ready!!

Now, you need to implement the game loss condition.



## Game Loss


---



You know the drill,

Think about:

What happens when the player loses the game?🤔

- Play the explosion sound 💥
- Show All Mines
- Stop the game/ Wait for the player’s next input



> **TODO**: 
> ✅ In `GameplayManager.cpp` implement `gameLost` method. 
> ✅ In `Board.cpp` make the `revealAllMines` method public and remove it from `Board::processMineCell` 
> ✅ Play the game.



Click here to see the solution.

`GameplayManager.cpp`

```cpp
void GameplayManager::gameLost() {
    Sound::SoundManager::PlaySound(Sound::SoundType::EXPLOSION);  // Boom!
    board->setBoardState(BoardState::COMPLETED);  // Game over
    board->revealAllMines();  // Show where the mines were
}
```



**Note: **You need to update the `processMineCell` function of the `Board` class:

`Board.cpp`

```cpp
//Handling Mine Cell
void Board::processMineCell(sf::Vector2i cell_position) {
gameplay_manager->setGameResult(GameResult::LOST); // Game Over!
}
```

Earlier, we were playing an explosion sound and all the mines were revealed. Now, you can just remove those lines, because it is being handled in the `gameLost` function.





Your gameplay is complete! 👏🏼

You have almost completed your first game with arrays!

Almost? 🤔

Well, there are still a few important pieces missing in our game:

1. Currently, if the game gets over, there’s no way to restart the game.
2. There’s no way of player knowing about the timer or the number of mines on the board.
3. And lastly, there’s no Main Menu, from where the player can choose to start or exit the game.



In the next two chapters, you’ll solve these 3 problems!

You have solved similar problems in pong, so you can do the next two chapters as a sprint 🏃🏼‍➡️

You’ll start by creating the gameplay UI to wrap up the gameplay state completely.

See you in the next chapter! 👋🏼
