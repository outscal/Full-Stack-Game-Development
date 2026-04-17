In this lesson, you'll create the `GameLoop` class.



Click here to see the `GameLoop.h` file.

`GameLoop.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "../../Header/Core/GameWindowManager.h"
#include "../../Header/Event/EventManager.h"

using namespace sf;
using namespace Core;
using namespace Event;
using namespace std;

namespace Core
{
	class GameLoop
	{
	private:
		GameWindowManager* game_window_manager;
		EventManager* event_manager;

	public:
		void initialize();

		bool isGameRunning();
		void pollEvent();
		void update();
		void render();
	};
}
```





**Note: **

- In `GameLoop.cpp` make sure that you include the `GameLoop.h` file.
- Make sure all the functions are in the Core namespace.

`GameLoop.cpp`

```cpp
#include "../../Header/Core/GameLoop.h"

namespace Core
{
		//Functions
}
```



## Initialize Game Environment


---



The `GameLoop` manages different classes’ initialization while main function only communicates with the game loop.

`GameLoop.cpp`

```cpp
void GameLoop::initialize() {
    game_window_manager = new GameWindowManager();
    event_manager = new EventManager();

    game_window_manager->initialize();
}
```



## Is Game Running?


---



We need a way to know if our game should continue running:

This function keeps checking if your game window is still open.

`GameLoop.cpp`

```cpp
bool GameLoop::isGameRunning() {
    return game_window_manager->isGameRunning();
}
```



## Process Player Inputs


---



Now you need to handle player actions:

You have already done this in the event manager.

`GameLoop.cpp`

```cpp
void GameLoop::pollEvent() {
    event_manager->pollEvents(game_window_manager->getGameWindow());
}
```



## Update


---



Now you need to add the update method:

There’s nothing to update for now, but you’ll add logic further in this module.

`GameLoop.cpp`

```cpp
void GameLoop::update() {
    
    }
```



## Render Updates


---



Let's add functions to show everything on the screen:

Note: You can remove the `render()` from `GameWindowManager` class.

`GameWindowManager.cpp`

```cpp
void GameWindowManager::clearGameWindow()
{
    game_window->clear();
}

void GameWindowManager::displayGameWindow()
{
    return game_window->display();
}
```

And bring it all together:

`GameLoop.cpp`

```cpp
void GameLoop::render() {
    game_window_manager->clearGameWindow();
    game_window_manager->displayGameWindow();
}
```

Now that `GameLoop` is handling all the lifecycle functions, the main function just needs to communicate with the `GameLoop` class.



> **TODO**: 
> ✅In `GameLoop.h` create objects of `GameWindowManager` and `EventManager` 
> ✅Implement `clearGameWindow` and `displayGameWindow` functions in the `GameWindowManager` class 
> ✅Remove `render` from `GameWindowManager` 
> ✅In `GameLoop.cpp` implement all the Lifecycle functions



## Updating The Main Function


---



Here's how we put all these pieces together:

`main.cpp`

```cpp
#include <SFML/Graphics.hpp>
#include "../../Header/Core/GameLoop.h"
using namespace sf;
using namespace Core;

int main()
{
    // Step 1: Create the GameLoop object
    GameLoop* game_loop_manager = new GameLoop();

    // Step 2: Initialize the game environment
    game_loop_manager->initialize();

    // Step 3: Run the game loop
    while (game_loop_manager->isGameRunning())
    {
        game_loop_manager->pollEvent();
        game_loop_manager->update();
        game_loop_manager->render();
    }

    return 0;
}
```



> **TODO**: 
> ✅ Create the Game Loop object 
> ✅ Initialize the game loop
> ✅ Implement the game loop in `main`



Your game loop is successfully setup to handle the gameplay!

In the next lesson, you’ll start creating the actual gameplay! 

Starting with rendering a ball and two paddles.🏓
