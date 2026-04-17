In this lesson, you'll add a reset button using the callback functionality.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_14_2025__06_50_28.png)

**Reset Button**



How does the restart functionality work?🤔

When the player clicks on this button:

1. The timer starts again
2. The board is reset
3. All cells reset -> Default state and value

Your gameplay works with a nice UI showing the timer and mine count. 

But what happens when you lose? 🤔

Right now, players need to close and reopen the game to try again. 
Let's fix that by adding a restart button!



Updated `GameplayManager.h `, `Board.h` and `Cell.h`

> **Summary📃**
> Here's what is added in the GameplayManager, Board and Cell classes:

> 🔸Helper functions to restart the game



`GameplayManager.h`

```cpp
#pragma once
#include "../../header/GameLoop/Gameplay/Board.h"
#include "../../header/Event/EventPollingManager.h"
#include "../../header/UI/GameplayUI/GameplayUI.h"
#include <SFML/Graphics.hpp>

namespace Gameplay
{
    using namespace UI;

    class GameplayManager
    {
    //previous code
    public:
				//previous code
        void restartGame();
    };
}
```



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
        void reset();
        //previous code
    };
}
```



`Cell.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>
#include "../../header/UI/UI Elements/Button/Buttons.h"
#include "../../header/Event/EventPollingManager.h"

using namespace UIElements;

namespace Gameplay
{
    //previous code

    class Cell
    {
    //previous code

    public:
        //previous code
        void reset();
        //previous code
    };
}


```





## Create the Restart Button


---

First, let's add the restart button to our UI. We'll need:

- A button texture
- A specific position on the screen.
- Dimensions of the Button



`GameplayUI.cpp`

```cpp
void GameplayUI::initializeButton() {
    restartButton = new Button(restartButtonTexturePath,
                             sf::Vector2f(restartButtonLeftOffset, restartButtonTopOffset),
                             buttonWidth, buttonHeight);
}
```

Make sure all the variables are initialized and register the callback for the button:

`GameplayUI.cpp`

```cpp
void GameplayUI::initialize(GameplayManager* gameplay_manager) {
    this->gameplay_manager = gameplay_manager;
    loadFonts();
    initializeTexts();
    initializeButton();  // Initialize Restart Button
    registerButtonCallback();  // Register callback for the button
}
```



> **TODO**: 
> ✅ Add the button initialization in the `GameplayUI` class.
> ✅ Run the code to make sure there are no errors



Now, let's write the logic for the restart button's callback function.



## Handle Button Clicks


---

What should happen when the button is clicked? 🤔

- Play a click sound
- Reset the game state
- Start a new game

Here's how we'll handle that:

`GameplayUI.cpp`

```cpp
void GameplayUI::registerButtonCallback() {
    restartButton->registerCallbackFunction([this](UIElements::MouseButtonType buttonType) {
        RestartButtonCallback(buttonType);
    });
}

void GameplayUI::RestartButtonCallback(MouseButtonType mouse_button_type) {
    if (mouse_button_type == MouseButtonType::LEFT_MOUSE_BUTTON) {
        Sound::SoundManager::PlaySound(Sound::SoundType::BUTTON_CLICK);
        gameplay_manager->restartGame();  // Restart the game
    }
}
```



> **TODO**: 
> ✅ Implement the `registerButtonCallback` and `RestartButtonCallback` methods in the `GameplayUI` class.
> ✅ Run the code to make sure there are no errors.



Now, let's write the restart logic.



## Reset the Game State


---

When restarting, we need to reset everything! 

- Set the game result to NONE
- Reset the Board
- Restart the timer.

`GameplayManager.cpp`

```cpp
void GameplayManager::restartGame() {
    game_result = GameResult::NONE;  // Clear previous result
    board->reset();  // Reset the board
    Time::TimeManager::initialize();  // Reset timer
    remaining_time = max_level_duration;  // Full time again
}
```



Then, the board needs to reset all cells and its state to `FIRST_CELL`:

`Board.cpp`

```cpp
void Board::reset() {
    for (int row = 0; row < numberOfRows; ++row) {
        for (int col = 0; col < numberOfColumns; ++col) {
            cell[row][col]->reset();  // Reset each cell
        }
    }

    flaggedCells = 0;  // No flags placed
    boardState = BoardState::FIRST_CELL;  // Ready for first click
}
```



Then, each cell needs to return to its initial state and reset mine count to 0:

`Cell.cpp`

```cpp
void Cell::reset() {
    current_cell_state = CellState::HIDDEN;  // Back to hidden
    cell_type = CellType::EMPTY;            // Back to empty
}
```



> **TODO**: 
> ✅ Implement the `restartGame()` method in the `GameplayManager` class
> ✅ Implement the reset methods in the `Cell` and `Board`. 
> ✅ Play the game to make sure there are no errors.



Finally, we need to update the lifecycle functions.



## Render and Update the Button


---

We need to make sure our button renders and responds to clicks:



`GameplayUI.cpp`

```cpp
void GameplayUI::render(sf::RenderWindow& window) {
		window.draw(mineText);
		window.draw(timeText);
		//render the restart button:
    restartButton->render(window);
}

void GameplayUI::update(int remaining_mines, int remaining_time,
                       EventPollingManager& eventManager, sf::RenderWindow& window) {
    mineText.setString(std::to_string(remaining_mines));
    timeText.setString(std::to_string(remaining_time));
    //handle restart button interaction
    restartButton->handleButtonInteractions(eventManager, window);
}
```



> **TODO**: 
> ✅ Update the `render` and `update` methods in the `GameplayUI.cpp` file.
> ✅ Play the game and test restart functionality.



> 💡 **PRO TIP:** 
> When resetting game state, it's important to reset EVERYTHING - a single forgotten variable can cause strange behavior in the next game!



You've successfully added:

- A restart button
- Complete game state reset
- A way for players to try again immediately

In the next lesson, we'll create a main menu to make our game even more polished! 🎮
