Our Minesweeper game is coming along nicely!

But a game isn't exciting without a bit of pressure - let's add a timer to make it more challenging! ⏰

You need to update the `GameplayManager.h` file before starting this lesson:



Updated `GameplayManager.h` file

> **Summary📃**
> Here's what is added in the Board class:
> 🔸Variables related to timer.
> 🔸`processTimeOver` function to process time over.
> 🔸`updateRemainingTime` function to update the time.
> 🔸`handleGameplay` function to handle the Gameplay



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
        const float max_level_duration = 150.0f;
        const float game_over_time = 11.0f;
        float remaining_time;

        //previous code

        void updateRemainingTime();
        void processTimeOver();

        void handleGameplay(EventPollingManager& eventManager, sf::RenderWindow& window);
        //previous code
     };
}

```





Before we add the timer, let's clean up our code a bit.



## Organizing the Code


---



Currently, we update the board directly in the `update` method.

Let's organize this better:

`GameplayManager.cpp`

```cpp
void GameplayManager::update(EventPollingManager& eventManager, sf::RenderWindow& window) {
				if (!hasGameEnded())
        		handleGameplay(eventManager, window);
   }
   
void GameplayManager::handleGameplay(EventPollingManager& eventManager, sf::RenderWindow& window) {
    board->update(eventManager, window); // update the board
}
```



Now, let's complete our new `handleGameplay` method to manage the timer as well.



## Adding a Timer


---



You need to initialize the timer to a maximum duration. 

When starting the game:

`GameplayManager.cpp`

```cpp
void GameplayManager::initializeVariables() {
    board = new Board(this);
    remaining_time = max_level_duration;  // Start with full time
}
```

update the remaining time every frame:

`GameplayManager.cpp`

```cpp
void GameplayManager::handleGameplay(EventPollingManager& eventManager, sf::RenderWindow& window) {
    updateRemainingTime();              // Update timer first
    board->update(eventManager, window); // Then update board
}
```



> **TODO**: 
> ✅ Update the `update` method and add `handleGameplay` in the `GameplayManager` class.
> ✅ Run the code to make sure there are no errors.



Now for the actual timer logic:

- Reduce the remaining time
- Handle Time Over Condition
- - Reset the timer to 0
  - Set the game result to LOST

Reminder ⏱️

Outscal has implemented the TimeManager class already, you can use it to implement the timer.

Include the `TimeManager.h` file in the `GameplayManager.h` file:

```cpp
#pragma once
#include "../../header/GameLoop/Gameplay/Board.h"
#include "../../header/Event/EventPollingManager.h"
#include "../../../header/Time/TimeManager.h" // include time manager
#include <SFML/Graphics.hpp>

namespace Gameplay
{
    using namespace Event;
    using namespace Time; //use the Time namespace

//previous code
}


```





```cpp
void GameplayManager::updateRemainingTime() {
    remaining_time -= TimeManager::getDeltaTime();  // Decrease time
    processTimeOver();  // Check if time's up
}

void GameplayManager::processTimeOver() {
    if (remaining_time <= 0) {
        remaining_time = 0; // Don't go negative
        game_result = GameResult::LOST; // Game over!
    }
}
```



> **TODO**: 
> ✅ Implement the `updateRemainingTime` and  `processTimeOver` methods in  the `GameplayManager` class.
> ✅ Run the code to make sure there are no errors.



> 💡 **PRO TIP:** 
> Notice how we separate different types of updates? The `update` method handles high-level game flow, while `handleGameplay` manages active gameplay elements. This makes our code easier to understand and modify!



You cannot see the timer yet, you’ll add it in the next chapter.

But, currently, there's a problem in our game.

Can you identify the problem?🤔

HINTPlay the game and try to win the game (you can reduce the no. of mines to do this faster)



Now, do you see the problem?

Even if the players win the game, there's no chance for the players to know that they have won the game.

Also, we can organize our code better.



You'll implement this in the next lesson.

See you in the next lesson!👋🏼
