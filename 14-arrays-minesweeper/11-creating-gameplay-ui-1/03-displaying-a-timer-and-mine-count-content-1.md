In this lesson, you will add two crucial UI elements to your Minesweeper game:

- A mine counter to show unflagged mines
- A timer to show the remaining time

These elements will help players track their progress during gameplay!



# Adding Mine Count


---

First, let's think about what the mine counter needs to do 🤔

- Display the total number of unflagged mines
- Update when mines are flagged or unflagged



## Create Mine Count Text


---

Let's start by setting up the text element:

1. Call the `initialize` function in the constructor of the GameplayUI class.
2. Initializing the variables and loading the fonts:

`GameplayUI.cpp`

```cpp
GameplayUI::GameplayUI(GameplayManager* gameplay_manager) 
{ 
		initialize(gameplay_manager); 
}

void GameplayUI::initialize(GameplayManager* gameplay_manager)
{
    this->gameplay_manager = gameplay_manager;
    loadFonts();
    initializeTexts();
}

void GameplayUI::loadFonts()
{
    if (!bubbleBobbleFont.loadFromFile("assets/fonts/bubbleBobble.ttf"))
        std::cerr << "Error loading bubbleBobble font!" << std::endl;
    
    if (!dsDigibFont.loadFromFile("assets/fonts/DS_DIGIB.ttf"))
        std::cerr << "Error loading DS_DIGIB font!" << std::endl;
}

```



1. Setup the text elements:

`GameplayUI.cpp`

```cpp
void GameplayUI::initializeTexts() {
    // Mine Text
    mineText.setFont(dsDigibFont);
    mineText.setCharacterSize(fontSize);
    mineText.setFillColor(textColor);
    mineText.setPosition(mineTextLeftOffset, mineTextTopOffset);
    mineText.setString("000");  // Default display
}
```

Try to set the `timeText` on your own, it will be the same as the `mineText`.



> **TODO**: 
> ✅ Implement the `initialize` and `loadFonts` methods. 
> ✅ Initialize the `mineText` and `timeText` in the `GameplayUI` class.
> ✅ Run the code to make sure that there are no errors



Click here to see the solution.

`GameplayUI::initializeTexts()`

```cpp
void GameplayUI::initializeTexts()
{
    // Mine Text
    mineText.setFont(dsDigibFont);
    mineText.setCharacterSize(fontSize);
    mineText.setFillColor(textColor);
    mineText.setPosition(mineTextLeftOffset, mineTextTopOffset);
    mineText.setString("000");

    // Time Text
    timeText.setFont(dsDigibFont);
    timeText.setCharacterSize(fontSize);
    timeText.setFillColor(textColor);
    timeText.setPosition(timeTextLeftOffset, timeTextTopOffset);
    timeText.setString("000");
}

```





The mine text and the timer text are initialized.

Now, you need to update them.

Let’s start with the mine count.



## Track Mine Count


---

How do we know how many mines are left? 🤔

Well, just subtract the `flaggedCells` from the `minesCount`! 



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_29_2025__14_27_31.png)



The board class stores the number of mines and flagged cells, so you can add a getter function in the `Board.h` file for calculating the remaining mines:

Updated `Board.h`

`Board.h`

```cpp
namespace Gameplay
{
    //previous code
    class Board
    {
    //previous code

    public:
    		//previous code
        int getRemainingMinesCount() const;
        //previous code
    };
}
```





`Board.cpp`

```cpp
int Board::getRemainingMinesCount() const {
    return minesCount - flaggedCells;  // Unflagged mines remaining
}
```



The `GameplayManager` needs to access this information, as the mine count will be updated by the gameplay manager:

Updated `GameplayManager.h`

`GameplayManager.h`

```cpp
#pragma once
#include "../../header/GameLoop/Gameplay/Board.h"
#include "../../header/Event/EventPollingManager.h"
#include <SFML/Graphics.hpp>

namespace Gameplay
{
		using namespace UI;
    //previous code

    class GameplayManager
    {
    private:
        //previous code

        int getRemainingMinesCount() const;

    //previous code
    };
}
```





`GameplayManager.cpp` 

```cpp
int GameplayManager::getMinesCount() const {
    return board->getRemainingMinesCount();
}
```

Now, you need to update the mine text.

The mine text will be updated in the `GameplauUI` class.



## Update Mine Count


---



Now, in the update function, update the `mineText` every frame with the value of `remaining_mines`

`GameplayUI.cpp`

```cpp
void GameplayUI::update(int remaining_mines, int remaining_time, EventPollingManager& eventManager, sf::RenderWindow& window) {
    mineText.setString(std::to_string(remaining_mines));
}
```



## Render Mine Count


---

We need to draw the mine count text to see it on screen:

`GameplayUI.cpp`

```cpp
void GameplayUI::render(sf::RenderWindow& window) {
    window.draw(mineText);
}
```



Just like the `mineText`, you need to update and render the `timeText` as well.

Again, it follows the same process, try to do it on your own.



> **TODO**: 
> ✅ Add `getRemainingMinesCount` to both the `Board` and `GameplayManager` classes. 
> ✅ Update the `mineText` and `timeText` in `GameplayUI::update()` 
> ✅ Render the `mineText` and `timeText` in `GameplayUI::render()`
> ✅ Run the code to make sure there are no errors



Solution.

`GameplayUI.cpp`

```cpp
void GameplayUI::update(int remaining_mines, int remaining_time, EventPollingManager& eventManager, sf::RenderWindow& window)
{
    mineText.setString(std::to_string(remaining_mines));
    timeText.setString(std::to_string(remaining_time));
}

void GameplayUI::render(sf::RenderWindow& window)
{
    window.draw(mineText);
    window.draw(timeText);
}
```





Lastly, to render and update the texts on the board,
you need to call the render and update methods of the `GameplayUI` class in `GameplayManager`’s render and update methods respectively.



## Connect Everything


---

Finally, let's make sure our GameplayManager keeps everything updated:

Updated `GameplayManager.h`

```cpp
#pragma once
#include "../../header/GameLoop/Gameplay/Board.h"
#include "../../header/Event/EventPollingManager.h"
#include "../../header/UI/GameplayUI/GameplayUI.h"
#include <SFML/Graphics.hpp>

namespace Gameplay
{
    //previous code
		using namespace UI;
    class GameplayManager
    {
    private:
        //previous code
				GameplayUI* gameplay_ui;

    //previous code
    };
}
```



Then, you need to update the lifecycle methods accordingly:



`GameplayManager.cpp`

```cpp
void GameplayManager::initializeVariables()
{
        board = new Board(this);
        gameplay_ui = new GameplayUI(this); //initialize gameplay UI
        
        remaining_time = max_level_duration;
}
    
void GameplayManager::update(EventPollingManager& eventManager, sf::RenderWindow& window) {
        if (!hasGameEnded())
            handleGameplay(eventManager, window);
        else if (board->getBoardState() != BoardState::COMPLETED)
            processGameResult();
		    
		    //update the UI
		    gameplay_ui->update(getRemainingMinesCount(),
		                       static_cast<int>(remaining_time),
		                       eventManager, window);
		}

void GameplayManager::render(sf::RenderWindow& window)
{
        window.draw(background_sprite);
        board->render(window);
    		
    		// render UI
    		gameplay_ui->render(window);
}
```



> **TODO**: 
> ✅ Update the `GameplayManager`’s initializeVariables, update and render methods. 
> ✅ Play the game.



You have successfully added the timer and the mine count!

Next is to restart the game.

Restarting the game is the last feature of the Gameplay state.

In the next lesson, we'll add a restart button so players can try again after winning or losing! 🔄

Let’s finish the gameplay state! 💪🏼
