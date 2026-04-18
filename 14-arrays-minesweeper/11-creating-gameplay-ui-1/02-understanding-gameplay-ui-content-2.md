In this lesson, you'll understand the purpose of the UI Elements that you'll add in the next lesson.



## **GAMEPLAY UI ELEMENTS**


---



![ ](/Full-Stack-Game-Development/images/8fae717a2f140c45.png)

**Gameplay UI Elements**

In the above image, all the UI elements are marked that need to be implemented



**TIMER TEXT**

A Text field that shows the remaining time.

**FLAG COUNT TEXT**

A Text field that shows how many flags are yet to be hosted -> `MineCount - FlagCount`

**RESET BUTTON**

A Button that resets the board. Basically restarts the game.



> **TODO: In **`**header/UI/GameplayUI**`** & **`**source/UI/GameplayUI**`
> **✅ **Create header and source files for GamplayUI class.
> ✅ Update the `GameplayUI.h` file.



This is the complete header file, as you have already implemented a text and a button feature before.

Update `GameplayUI.h`

> **Summary📃**

> Here's what is added in the **GameplayUI** class:

> 🔸 **Text Elements:** Displays mine count (`mineText`) and remaining time (`timeText`).
> 🔸 **Button Element:** A `restartButton` that triggers game restart logic.
> 🔸 **Fonts:** Uses `bubbleBobbleFont` and `dsDigibFont` for UI text.
> 🔸 **Constants:** Defines positioning offsets, button size, and text color.
> 🔸 **Gameplay Manager Reference:** Interacts with `GameplayManager` for game state updates.

> 🔸 **Initialization Methods:**

> 🔹 `initialize()` → Sets up UI with `GameplayManager`.
> 🔹 `initializeTexts()` → Configures text elements.
> 🔹 `initializeButton()` → Sets up the restart button.
> 🔹 `loadFonts()` → Loads fonts for UI text.

> 🔸 **Callback System:**

> 🔹 `registerButtonCallback()` → Registers the restart button callback.
> 🔹 `RestartButtonCallback()` → Handles restart button clicks.

> 🔸 **Lifecycle Functions:**

> 🔹 `update()` → Updates UI elements based on game state changes.
> 🔹 `render()` → Renders UI elements in the SFML window.



`GameplayUI.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "../../header/UI/UIElements/Button/Button.h"
#include "../../header/Event/EventPollingManager.h"

namespace Gameplay
{
    class GameplayManager;
}

namespace UI
{
    using namespace Gameplay;
    using namespace UIElements;
    using namespace Event;
    
    class GameplayUI {
    private:
        sf::Font bubbleBobbleFont;
        sf::Font dsDigibFont;

        // Text elements
        sf::Text mineText;
        sf::Text timeText;

        // Button element
        Button* restartButton = nullptr;
        bool restartButtonClicked = false;

        // Constants
        const std::string restartButtonTexturePath = "assets/textures/restart_button.png";
        const int fontSize = 110;

        const float mineTextTopOffset = 65.f;
        const float mineTextLeftOffset = 660.f;

        const float timeTextTopOffset = 65.f;
        const float timeTextLeftOffset = 1090.f;

        const float restartButtonTopOffset = 100.f;
        const float restartButtonLeftOffset = 920.f;

        const float buttonWidth = 80.f;
        const float buttonHeight = 80.f;
        const sf::Color textColor = sf::Color::Red;

        GameplayManager* gameplay_manager;
        
        // Private methods for initialization
        void initialize(GameplayManager* gameplay_manager);
        void initializeTexts();
        void initializeButton();
        void loadFonts();
				
				//Callback System
        void registerButtonCallback();
        void RestartButtonCallback(MouseButtonType mouse_button_type);

    public:
        GameplayUI(GameplayManager* gameplay_manager);
        ~GameplayUI() = default;

        void update(int remaining_mines, int remaining_time, EventPollingManager& eventManager, sf::RenderWindow& window);
        void render(sf::RenderWindow& window);
    };
}
```





Reminder ⏱️

In the `GameplayUI.cpp` file, don't forget to include the `GameplayUI.h` and `GameplayManager.h` files and write the function definitions in the `UI` namespace.



`GameplayUI.cpp`

```cpp
#include <iostream>
#include "../../header/UI/GameplayUI/GameplayUI.h"
#include "../../../header/GameLoop/Gameplay/GameplayManager.h"

namespace UI {
		//Function Implementations
}

```





Let’s start by displaying the timer and mine count in the next lesson!
