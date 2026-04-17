Your game is playable now, but players just jump straight into gameplay! 

Every good game needs a proper Main Menu. 🎮

Let's think about what a Main Menu needs to do 🤔

- Let players start the game when they're ready
- Allow players to quit the game



## Understanding the Main Menu


---

The Main Menu will be the first thing players see when they open your game. 

It needs:



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_14_2025__07_04_07.png)



- A nice background
- Clear buttons for actions

We'll manage all of this with a dedicated `MainMenuManager` class.



## Creating the Manager


---

First, let's create our menu files in the right place:

1. Create a new folder: `UI/MainMenu/`
2. Add these files:
3. - `MainMenuManager.h`
  - `MainMenuManager.cpp`



`MainMenuManager.h` 

> **Summary📃**

> Here's what is added in the **MainMenuManager** class:

> 🔸 **Window and Background Elements:**

> 🔹 Manages the game window (`game_window`).
> 🔹 Sets up the menu background using `background_texture` and `background_sprite`.

> 🔸 **Menu Buttons:**

> 🔹 `play_button` → Starts the game.
> 🔹 `quit_button` → Exits the game.

> 🔸 **Asset Paths and Dimensions:**

> 🔹 Defines paths for background and button textures.
> 🔹 Sets button sizes, positions, and background transparency.

> 🔸 **Initialization Methods:**

> 🔹 `initialize()` → Sets up the main menu.
> 🔹 `initializeBackground()` → Loads and configures the menu background.
> 🔹 `initializeButtons()` → Initializes and positions the menu buttons.

> 🔸 **Callback System:**

> 🔹 `registerButtonCallbacks()` → Registers button click handlers.
> 🔹 `playButtonCallback()` → Handles play button click.
> 🔹 `quitButtonCallback()` → Handles quit button click.

> 🔸 **Utility Method:**

> 🔹 `getButtonPosition()` → Computes button positions based on offsets.

> 🔸 **Lifecycle Functions:**

> 🔹 `update()` → Processes events and updates UI elements.
> 🔹 `render()` → Draws the menu elements onto the window.
> 🔹 `show()` → Displays the main menu.

> 🔸 **Event Handling:**

> 🔹 `checkForButtonClicks()` → Detects and processes button click events.





```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "../../header/UI/UIElements/Button/Button.h"
#include "../../header/Event/EventPollingManager.h"

namespace UI {
    using namespace UIElements;

    class MainMenuManager {
    private:
        // Window and background elements
        sf::RenderWindow* game_window;
        sf::Texture background_texture;
        sf::Sprite background_sprite;

        // Menu buttons
        Button* play_button;
        Button* quit_button;

        // Asset paths and dimensions
        const std::string background_texture_path = "assets/textures/minesweeper_bg.png";
        const std::string play_button_texture_path = "assets/textures/play_button.png";
        const std::string quit_button_texture_path = "assets/textures/quit_button.png";

        const float button_width = 300.f;
        const float button_height = 100.f;
        const float play_button_y_position = 600.f;
        const float quit_button_y_position = 750.f;
        const float background_alpha = 85.f;

        // Private methods for setup and handling
        void initialize();
        void initializeBackground();
        void initializeButtons();

        void playButtonCallback(MouseButtonType mouse_button_type);
        void quitButtonCallback(MouseButtonType mouse_button_type);
        void registerButtonCallbacks();

        sf::Vector2f getButtonPosition(float offsetX, float offsetY);

    public:
        MainMenuManager(sf::RenderWindow* window);
        ~MainMenuManager();

        void update(Event::EventPollingManager eventManager);
        void render();
        void show();

        void checkForButtonClicks(Event::EventPollingManager& eventManager);
    };
}
```





Reminder ⏱️

In the `MainMenuManager.cpp` file, don't forget to include the `MainMenuManager.h` and `GameLoop.h` files and write the function definitions in the `UI` namespace.



`MainMenuManager.cpp`

```cpp
#include "../../header/UI/MainMenu/MainMenuManager.h"
#include "../../../header/GameLoop/GameLoop.h"
#include <iostream>



namespace UI {
		//Function Implementations
}

```





> **TODO**: 
> ✅ Create the `UI/MainMenu` folder. 
> ✅ Add the `MainMenuManager.h` and `MainMenuManager.cpp` files with the provided code.



Let's break down what this class will do:

1. Display a background image
2. Show two buttons: Play and Quit
3. Handle button clicks
4. Transition to gameplay state when the Play button is clicked
5. Close the game when the Quit button is clicked



In the next lesson, we'll implement all these features and bring our menu to life! 🎨
