It's time to add some danger to our game - let's handle what happens when a player clicks on a mine! 💣



Updated `GameplayManager.h` and `Board.h`

> **Summary📃**
> Here's what is added in the `GameplayManager` class:

> 🔸Enum to keep track of the game result
> 🔸Variable for `GameResult` enum.
> 🔸Setter function for `game_result`



`GameplayManager.h`

```cpp
namespace Gameplay
{
    enum class GameResult
    {
        NONE,
        WON,
        LOST
    };
    class GameplayManager
    {
    private:
    		GameResult game_result;
    		//previous code
    		bool hasGameEnded();
   	public:
   				//previous code
        void setGameResult(GameResult gameResult);
     };
}    
```



> **Summary📃**
> Here's what is added in the `Board` class:
> 🔸`processMineCell` function to process a mine cell
> 🔸`revealAllMines` function to reveal all mines



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

    class Board
    {
    private:
    //previous code
        void processMineCell(sf::Vector2i cell_position);
        
   //previous code
   public:
   //previous code
   	void revealAllMines();
   };
}
```





# Processing Mine Cell


---



Where will we handle the Mine cell?🤔

In the `processCellType` method of the `Board` class, we have a case to handle the `MINE` cells:

`Board.cpp`

```cpp
void Board::processCellType(sf::Vector2i cell_position)
{
    switch (cell[cell_position.x][cell_position.y]->getCellType())
    {
    case CellType::EMPTY:
        processEmptyCell(cell_position);
        break;
    case CellType::MINE: // Handle mine cells
        processMineCell(cell_position);
        break;
    default:
        cell[cell_position.x][cell_position.y]->open();
        break;
    }
}
```

Now, let's implement what happens when a mine is clicked.

When a mine is clicked, four things need to happen:

1. The game ends (you lost!)
2. Play the explosion sound.
3. All mines are revealed



It looks simple, but there’s a catch!

In the Board class, you need the reference of the gameplay manager to change the game result.

That sounds straightforward. 

What’s the catch here 🤔

Well, you’ll need to include the `GameplayManager.h` file in the `Board.h` file. And `GameplayManager.h` already has the `Board.h` file!

Sounds like a familiar problem from ***C++ Intermediate(Pokemon)***?

Refer to this content to understand the [Circular Dependency Problem](https://outscal.com/course/full-stack-game-development/c-intermediate-pokemon/let-the-battle-begin/file-organization-content-1)

To solve the circular dependency problem, you need to forward declare the `GameplayManager` class in the Board class.

How to do that?🤔

[Forward Declaration](https://outscal.com/course/full-stack-game-development/c-intermediate-pokemon/code-organization/forward-declaration-content-1)



Updated `Board.h`, `Board.cpp` and `GameplayManager.cpp` files after forward declaration.

> **Summary📃**
> Here's what is added in the `Board` class:

> 🔸Forward declared the Gameplay Manager in the `Board.h` file.
> 🔸Update signatures of the `initialize()`, `initializeVariables()` and `Board()`
> 🔸Initialized `gameplay_manager`
> 🔸Included `GameplayManager.h` file in `Board.cpp` file.



`Board.h`

```cpp
//previous code

namespace Gameplay
{
    class GameplayManager; //Forawrd Declare
    //previous code

    class Board
    {
    private:
        GameplayManager* gameplay_manager; 
        //previous code
        
        void initialize(GameplayManager* gameplay_manager);
        void initializeVariables(GameplayManager* gameplay_manager);
        
        //previous code
		 public:
		     Board(GameplayManager* gameplayManager);
		     //previoud code
    }
}

```

`Board.cpp`

```cpp
#include "../../header/GameLoop/Gameplay/Board.h"
#include "../../header/GameLoop/Gameplay/GameplayManager.h"
#include <iostream>

namespace Gameplay
{
	Board::Board(GameplayManager* gameplayManager)
	{ 
			initialize(gameplayManager); 
	}

	void Board::initialize(GameplayManager* gameplayManager)
	{
	    initializeVariables(gameplayManager);
	    //previous code
	}

	void Board::initializeVariables(GameplayManager* gameplay_manager)
	{
	    this->gameplay_manager = gameplay_manager;
	    //previous code
	}
	
	//other functions
}
```



You also need to update the `initializeVariables` method of the GameplayManager class:

> **Summary📃**
> Here's what is updated in the GameplayManager class:
> 🔸Initialized `board` variable.



`GameplayManager.cpp`

```cpp
void GameplayManager::initializeVariables()
{
		board = new Board(this);
}
```









Now, before implementing the `ProcessMineCell`, you need to implement the `setGameResult` method.

> **TODO**: 
> ✅ Implement the `setGameResult` method in the `GameplayManager` class.



Click here to see the solution.

`GameplayManager.cpp`

```cpp
    void GameplayManager::setGameResult(GameResult gameResult) 
    { 
    			this->game_result = gameResult; 
    }
```





Now, the `processMineCell` function is ready to implement.

Let's start with setting the game result to LOST and revealing all mines on the board:

`Board.cpp`

```cpp
//Handling Mine Cell
void Board::processMineCell(sf::Vector2i cell_position) {
    gameplay_manager->setGameResult(GameResult::LOST);  // Game Over!
    Sound::SoundManager::PlaySound(Sound::SoundType::EXPLOSION);
    revealAllMines();                                   // Show all mines
}
```



> **TODO**: 
> ✅ Update the `processCellType` method in the `Board` class. 
> ✅ Add the `processMineCell` method in the `Board` class.



Finally, we need a way to reveal all mines on the board.



## Reveal All Mines


---



You just need to traverse over the 2D array and set all Mine cells’ states to open!

This is straightforward, you can implement this on your own 💪🏼

> **TODO**: 
> ✅ Implement the `revealAllMines` method in the `Board` class. 
> ✅ Play the game and click on a mine cell.



Click here to see the solution.

`Board.cpp`

```cpp
void Board::revealAllMines() {
    for (int row = 0; row < numberOfRows; row++) {
        for (int col = 0; col < numberOfColumns; col++) {
            if (cell[row][col]->getCellType() == CellType::MINE) {
                cell[row][col]->setCellState(CellState::OPEN);  // Show the mines
            }
        }
    }
}
```





You have **almost **handled the mine cell correctly.

Almost?!🤨

Well, you still have to Implement the `setGameResult` function in the `GameplayManager` class.

And..

Currently, there’s a problem in our game.

Can you identify the problem?🤔

HINTTry to open the cells even after opening a mine.

Now, you see the problem?

The cells can be opened even after a mine is opened!



You need to make the board unclickable after a mine is opened.

How to make the board unclickable?🤔

Well, this is quite straightforward.

If the `game_result` is either WON or LOST, the game has ended and the board should **stop updating**.

Let's start with checking if the game has ended:

When does the game end?🤔

- When the result is either won or lost (basically `result != NONE`).

`GameplayManager.cpp`

```cpp
bool GameplayManager::hasGameEnded() {
return game_result != GameResult::NONE;
}
```

Now, update the board only if the game has not ended:

`GameplayManager.cpp`

```cpp
void GameplayManager::update(EventPollingManager& eventManager, sf::RenderWindow& window)
{
        if (!hasGameEnded()) //Check if the game has ended
						board->update(eventManager, window);
}
```



> **TODO**: 
> ✅ Implement the `hasGameEnded` method in the `GameplayManager` class.
> ✅ Update the `update` method of the `GameplayManager` class.



Great! Now, your game is playable!👏🏼

Before you get lost in your own game, we have another problem to fix!

Let’s discuss and solve the problem in the next lesson!
