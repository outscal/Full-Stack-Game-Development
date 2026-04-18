You have already created a ball in Pong using a sprite.

Similarly, you need to render the board!



For rendering the board, you should start with `Board.h` 



Here is the folder structure:

Create the header and source files for the Board class. 

`source/GameLoop/Gameplay/Board.cpp`

`header/GameLoop/Gameplay/Board.h`



Board.h

> **Summary📃**

> In the `Board.h` class, you need to add the following to render a board:

> 🔸Board's Dimensions and Position

> 🔸Board's texture and sprite

> 🔸Helper Functions to initialize the variables

> 🔸Board Constructor

> 🔸A helper function to draw the board



Here's the `Board.h` file after adding the above points:



`Board.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>

namespace Gameplay
{
    class Board
    {
    private:

        const float boardWidth = 866.f;
        const float boardHeight = 1080.f;
        const float boardPosition = 530.f;

				const std::string boardTexturePath = "assets/textures/board.png";
        sf::Texture boardTexture;
        sf::Sprite boardSprite;

        void initializeBoardImage();
        void initialize();

    public:
    		
        Board();
        
        void render(sf::RenderWindow& window);
    };
}
```





Reminder⏱️

In the `Board.cpp` file, don't forget to include the `Board.h` file and write the function definitions in the `Gameplay` namespace.

`Board.cpp`

```cpp
#include "../../header/GameLoop/Gameplay/Board.h"

namespace Gameplay
{
	//Function definitions
}
```





## Drawing the Board


---

Now that the header file is setup, 
it’s time to implement the functions and render the board!



Start with the constructor and `Initialize()` method to initialize the board's image:

`Board.cpp`

```cpp
Board::Board()
{
   initialize();
}

void Board::initialize()
{
    initializeBoardImage();
}
```



Now, how to implement the `initializeBoardImage()` method? 🤔

First, you need to load the board image’s texture.

Then, set the `boardSprite`’s texture, position, and scale.

After finishing the `initializeBoardImage()` method, you can draw the board in the `render()` function



`Board.cpp`

```cpp
void Board::initializeBoardImage() {
    if (!boardTexture.loadFromFile(boardTexturePath)) {
        std::cerr << "Failed to load board texture!" << std::endl;
        return;
    }
    
    boardSprite.setTexture(boardTexture);
    boardSprite.setPosition(boardPosition, 0);
    boardSprite.setScale(boardWidth / boardTexture.getSize().x,
                        boardHeight / boardTexture.getSize().y);
}

    void Board::render(sf::RenderWindow& window)
    {
        window.draw(boardSprite);
    }
```

Why this particular way of calculating the scale?🤔

```txt
boardSprite.setScale(boardWidth / boardTexture.getSize().x,
                        boardHeight / boardTexture.getSize().y);

```

You can use this calculation to scale the board’s sprite to a desired scale.

How?🤔

Let’s say, you want to render a board of 800 pixels in width, and the width of the board’s texture in pixels is 252 pixels.

Then, you’ll need to scale the board texture so that the 252 pixels(Actual Width) becomes 800 pixels(desired width).

This is how you can do it.

**800/252 = 3.17**

So, if you set the scale on the x-axis to **3.17** the width of the sprite will be:** 3.17(Scale in x-axis) X 252(Actual Width) = 800(Desired Width)**



> **TODO:** 
> ✅ In the `Board()` constructor call `initialize()` method.
> ✅ Implement `initialize()` method.
> ✅ Implement `initializeBoardImage()` method.  
> ✅ in `Board::render()` draw the `boardSprite`



Now, to render the board, the Gameplay Manager will call the `render` method of the board class.

Here's how the render method of the Board class is called:

![ ](//outscal.github.io/Full-Stack-Game-Development/images/c0c3f53ec02e13f0.png)



- The main function calls the GameLoop class's `run()` method, which handles the overall flow of the game loop.
- `GameLoop` calls the render method of the `GameplayManager` class.
- `GameplayManager` calls the render method of the `Board` class.
- And lastly, the `Board` class draws the board on the game window.



To follow this architecture, you need to create the `GameplayManager` class.

Here’s the header file of the gameplay manager class that you need to create to render a board:



Here is the folder structure:

Create the header and source files for the GameplayManager class. 

`source/GameLoop/Gameplay/GameplayManager.cpp`

`header/GameLoop/Gameplay/GameplayManager.h`



GameplayManager.h

> **Summary📃**
> In the gameplay manager class you need to add the following to render a board:

> 🔸Create an object of the Board class.

> 🔸Initialize variables like the board object.

> 🔸Constructor and Destructor of the Gameplay Manager to handle the creation and deletion of the object of the Gameplay Manager class.

> 🔸A function to handle the rendering.



Here's the `GameplayManager.h` file after adding the above points:



`GameplayManager.h`

```cpp
#pragma once
#include "../../header/GameLoop/Gameplay/Board.h"
#include <SFML/Graphics.hpp>

namespace Gameplay
{
    class GameplayManager
    {
    private:
        Board* board;
        
        void initialize();
        void initializeVariables();

    public:
        GameplayManager();
        ~GameplayManager() = default;

        void render(sf::RenderWindow& window);
    };
}
```





Reminder⏱️

In the `GameplayManager.cpp` file, don't forget to:

- Include the `GameplayManager.h` file 
- Write the function definitions in the `Gameplay` namespace.



`GameplayManager.cpp`

```cpp
#include "../../header/GameLoop/Gameplay/GameplayManager.h"

namespace Gameplay
{
	//Function definitions
}
```





Now, you need to initialize the board object.

Then, render the board on the game window!

This is straightforward, you can do it on your own 💪🏼



> **TODO:** 
> ✅ In `Board.cpp` implement the `initialize()` and `initializeVariables()`function. 
> ✅ In `GameplayManager::render()` call the `render()` function of the `Board` class.
> ✅Initialize private `board` object pointer with new Board object in the `initializeVariables()` function.
> ✅Call the `render()` function of the board class iniside `render()` function of GameplayManager





Click here to see the solution.

> **Summary📃**
> Here are the things we are doing:

> 🔸Calling the `initialize` method in GameplayManager's constructor.

> 🔸Defining the `initialize` and `initializeVariables` methods.

> 🔸Calling the `render` function of the Board class.



`GameplayManager.cpp`

```cpp
GameplayManager::GameplayManager()
{
    initialize();
}

void GameplayManager::initialize()
{
    initializeVariables();
}

void GameplayManager::initializeVariables()
{
    board = new Board();
}

void GameplayManager::render(sf::RenderWindow& window)
{
    board->render(window);
}

```





Finally,

in the render method of the GameLoop class,

call the render method of the Gameplay Manager class.



> **TODO:** 
> ✅ In `GameLoop.h` file create a private pointer object of the `GameplayManager`.(include essential header file and use essential namespace in `GameLoop.h`)



Now, you need to initialize the `gameplay_manager` object in the `initialize()` function:

`GameLoop.cpp`

```cpp
void GameLoop::initialize()
{
		window_manager = new GameWindowManager();
		game_window = window_manager->getGameWindow();
		event_manager = new EventPollingManager(game_window);
    gameplay_manager = new GameplayManager(); 	//initialize gameplay_manager
	
		Sound::SoundManager::Initialize();
		Sound::SoundManager::PlayBackgroundMusic();
		Time::TimeManager::initialize();
}
```

You have created an instance of `GameplayManager`, but you also need to delete it in the destructor of the `GameLoop` class:

`GameLoop.cpp`

```cpp
GameLoop::~GameLoop()
{
    delete window_manager;
    delete event_manager;
    delete splash_screen_manager;
    delete gameplay_manager; //delete gameplay manager
}
```

Now it’s time to update the `render` method of `GameLoop` class

You already have a switch case in place, now just check for the `GAMEPLAY` state in the switch case and call the render function of `gameplay_manager`

`GameLoop.cpp`

```cpp
void GameLoop::render()
{
    game_window->clear();
    window_manager->render();

    switch (current_state)
    {
		case GameState::SPLASH_SCREEN:
    		splash_screen_manager->render();
    		break;
		case GameState::MAIN_MENU:
   	 		break;
		//gamepaly state
    case GameState::GAMEPLAY:
        gameplay_manager->render(*game_window);
        break;
    }
    
    game_window->display();
}
```



Play the game to see the rendered board.

That board looks great!👌🏼

But something looks missing 🤔

I think a background image would look nice 😌

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/8c9f7b97-3438-434a-b8ca-0a53eb7262ea/a7d6668a-5568-4edf-8a73-f36478984998/image.png)



![ ](//outscal.github.io/Full-Stack-Game-Development/images/fd39e0d99155956c.png)



You can render a `background_sprite` in the Gameplay manager itself.



Updated `GameplayManager.h`

> **Summary📃**
> Here's what you need to add to the `GameplayManager.h` file to render the background image:

> 🔸Alpha value to set the transparency of the background image.

> 🔸Background texture and sprite.

> 🔸Helper function to initialize the background image.



Here's the `GameplayManager.h` file after adding the above points:



`GameplayManager.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>

namespace Gameplay
{
	class GameplayManager {
	private:
	    //previous code
	    const float background_alpha = 85.f;
	    
	    sf::Texture background_texture;
	    sf::Sprite background_sprite;
	    std::string background_texture_path = "assets/textures/minesweeper_bg.png";
			
	    void initializeBackgroundImage();
	
	    //previous code
	};
}
```





Using these variables and functions, you can render the background sprite

You have already done this for the board image, similarly background image also can be rendered.



> **TODO:**
> ✅ Implement `initializeBackgroundImage()` method.
> ✅ In the `initialize()` method call the `initializeBackgroundImage()`
> ✅ In `GameplayManager::render()` draw the `background_sprite`



Click here to see the solution.

> **Summary📃**
> Here we are doing three things:

> 🔸Defining the `initializeBackgroundImage()` method.

> 🔸Calling `initializeBackgroundImage()` in the `initialize()` method.

> 🔸In the `render()` method, we are drawing the background sprite.



`GameplayManager.cpp`

```cpp
#include <iostream>
#include "../../header/GameLoop/Gameplay/GameplayManager.h"
#include "../../../header/Time/TimeManager.h"

namespace Gameplay
{
	void GameplayManager::initialize()
	{
		//initialize background image
    initializeBackgroundImage();
    initializeVariables();
	}


	void GameplayManager::initializeBackgroundImage() {
	    if (!background_texture.loadFromFile(background_texture_path)) {
	        std::cerr << "Failed to load background texture!" << std::endl;
	    }
	    background_sprite.setTexture(background_texture);
	    background_sprite.setColor(sf::Color(255, 255, 255, background_alpha));
	}

	void GameplayManager::render(sf::RenderWindow& window)
	{
			//Render the background
			window.draw(background_sprite);
			
			//Render the board
			board->render(window);
	}
}
```



**Note:  **The `background_sprite` is rendered before the board.

Why?🤔

Well, because if you render the board first and then the background image, then the background image is rendered on the board's image, making the board disappear.





Now it looks better!

But the Cells are still missing.

In the next chapter, you’ll render the cells as well!

**See you there! 👋🏼**
