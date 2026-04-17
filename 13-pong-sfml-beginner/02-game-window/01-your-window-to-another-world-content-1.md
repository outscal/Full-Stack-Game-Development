Every masterpiece needs a canvas! 

For a painter, it's their blank canvas. 

For a sculptor, it's their raw marble. 

And for us game developers? It's our game window! 

This is where all your creative ideas will come to life.

But, how can you create this magical window? 🤔



## Setting Up Game Window


---



> **TODO**:
> ✅ Create a new folders `Header/Core` and `Source/Core` in your project directory. 
> ✅ Inside the `Header/Core` folder, create `GameWindowManager.h` 
> ✅ In the `Source/Core` folder create `GameWindowManager.cpp`



> 💡**PRO TIP**:
>  Keep all your core game systems in the `Core` folder. This organization will save you hours of headaches as your game grows!





Expected Folder Structure.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/12_20_2024__08_28_35.png)

**Folder Structure**







## Creating Your First Game Window


---



Let's build it piece by piece:

`GameWindowManager.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>

using namespace sf;
```

This is our foundation. But what does each line do?

- `#pragma once` tells our compiler "Hey, only include this file once!"
- We're including SFML's graphics capabilities!
- `using namespace sf` lets us use SFML's tools without writing `sf::` every time

Now, let's add our class structure:

```cpp
namespace Core {
    class GameWindowManager {
    private:
        int game_window_width = 1280;
        int game_window_height = 720;
        std::string game_title = "SFML-Pong!";

        RenderWindow* game_window;

        void createGameWindow();
```



> 📖 🎮 **GAME DEV DICTIONARY** 
> ***RenderWindow***: "`sf::RenderWindow` is derived from `sf::Window`, thus it inherits all its features: events, window management, OpenGL rendering, etc."



Think about why we chose these numbers:

1280(`game_window_width`)x720(`game_window_height`) is HD resolution!

The `game_title` displays on the top of the `game_window`

Lastly, the pointer object of the `RenderWindow` and `createGameWindow()` to create the game window with the above properties.

Why private variables? You don’t want them to be modified or accessed by other classes!



Let's add our public members:

```cpp
    public:
        void initialize();
        RenderWindow* getGameWindow();
        bool isGameRunning();
        void render();
    };
}
```



What are these random functions?!🤨

Don’t worry. These are not random.

Let's understand each method's purpose:

The `initialize()` method:

1.  Creates the game window instance

2.  Sets up initial window properties

The `getGameWindow()` method:

1.  Getter function for the `game_window`

The `isGameRunning()` method:

1.  Checks if the window is closed

The `render()` method:

1.  Handles all drawing operations

2.  Updates the display each frame

3.  Manages what players see on screen

> **TODO**: `GameWindowManager.h` 
> ✅ Implement the `GameWindowManager.h` file.



You have created all the required variables and functions to create a game window!

Let's understand how you can implement it.



## Implementing Game Window Manager




---



It’s time to implement the game window manager step by step.

First, let's understand the initialization logic:

`GameWindowManager.cpp`

```cpp
#include "../../Header/Core/GameWindowManager.h"

namespace Core
{
void GameWindowManager::initialize() {
// Allocate memory for the render window object
    game_window = new RenderWindow();
// Set up the window with configured properties
    createGameWindow();
}
}
```

This allocates a memory for the object of the `RenderWindow()` class!

What next?🤔

Game window creation:

`GameWindowManager.cpp`

```cpp
void GameWindowManager::createGameWindow() {
// Create the window with specified dimensions and title
    game_window->create(
        VideoMode(game_window_width, game_window_height),
        game_title
    );
}
```

Let's understand what's happening here:

- `VideoMode` sets up the display configuration(width and height).
- First parameter combines our width and height
- Second parameter sets the window's title bar text



Now, check the  window status:

> 💡**PROTIP**: 
> Always check if the window is running before performing any window operations!



`GameWindowManager.cpp`

```cpp
bool GameWindowManager::isGameRunning() {
// Return true if window is open, false if closed
    return game_window->isOpen();
}
```

Then, the render function:

`GameWindowManager.cpp`

```cpp
void GameWindowManager::render() {
// This will handle all the drawing operations
//It'll be used in future lessons
}
```

Lastly, the getter function for the game window:

`GameWindowManager.cpp`

```cpp
RenderWindow* GameWindowManager::getGameWindow() {
    return game_window;
}
```



> **TODO**: 
> ✅Implement each function in `GameWindowManager.cpp` 
> ✅Play the game.



The logic for creating the game window is complete!

But the game window will not appear if you don't implement the logic in the `main()` function 🤷🏼

 

## Creating the Game Entry Point


---



This is where you'll bring everything together.

Let's break it down:

1. Initialize and create the game window.
2. Check if the window is still open (`isGameRunning()`)
3. If open, call render to update the display and Repeat until the window is closed.

```cpp
// main.cpp
#include "Core/GameWindowManager.h"

int main() {
// Create our window manager instance
    Core::GameWindowManager gameWindowManager;

// Initialize the window
    gameWindowManager.initialize();

    while (gameWindowManager.isGameRunning()) {
        gameWindowManager.render();
    }

    return 0;
}
```



**Note**: You’ll implement the render() function in the next lesson.



> **TODO**: `Main.cpp`
> ✅ Include the `GameWindowManager.h` file 
> ✅ Create and Initialze `gameWindowManager`



You’ve successfully created your own game window!!🥳

In the next lesson, you’ll learn how to customize the color and size of the window.
