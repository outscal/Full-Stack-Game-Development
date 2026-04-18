![    ](/Full-Stack-Game-Development/images/a08a30624a361fe2.png)



The above image shows the buttons on the Main Menu screen.

Currently, clicking on these buttons does not do anything.

Until and unless these buttons work, the gameplay screen won't appear.



That brings us to what you will be doing in this lesson:

- You will make sure that the Gameplay screen opens when the buttons are clicked.
- You will also be adding a background image to the game screen!



Let's go through the structure for this project before you dive into the tasks.



## Gameplay MVC


---

![      ](/Full-Stack-Game-Development/images/9527f1d930ac6199.png)

***Gameplay Hierarchy***



`**GameplayController**` takes care of the game's logic, while `**GameplayView**` handles the gameplay UI.

`**GameplayService**` enables the management of the gameplay, which also includes the logic for Button.



So, to make that button work, you need to create and implement the hierarchy.



## implementing gameplay


---

As you know, `**GameplayView**` handles the gameplay UI, which means it takes care of everything that will be rendered on the UI.



Starting from the Background to the Sticks, the `**View**` handles what you see.

But you also need the `**Controller**` to manage interactions and logic. 

In your visualizer, the Gameplay has nothing to do with data, so there is no need for a `**Model**`.



> ✅**TODO: **

> 1. Create a new folder in your project directory named `Gameplay`.

> 2. Create `GameplayView` and `GameplayController` inside this folder.

> 3. Define empty lifecycle functions for them.

> 4. Define empty reset function in `GameplayController`.



Click here for `GameplayController.h`

```cpp
#pragma once

namespace Gameplay
{
    
    class GameplayView;

    class GameplayController
    {
    private:
       
        GameplayView* gameplay_view;


        void destroy();

    public:
        GameplayController();
        ~GameplayController();

        void initialize();
        void update();
        void render();

        void reset();

    };
}

```



Click here for `GameplayView.h`

```cpp
#pragma once

namespace Gameplay
{
    class GameplayController;

    class GameplayView
    {

    public:
        GameplayView();
        ~GameplayView();

        void initialize(GameplayController* gameplay_controller);
        void update();
        void render();
    };
}

```





Now that you have created the View-Controller files, you must also connect them to **ServiceLocator**.

How will you be doing it? 

By connecting `GameplayService` to `ServiceLocator`.



Therefore, you need to create `**GameplayService**`.



> ✅**TODO: **

> 1. Create `GameplayService` with empty lifecycle methods and `reset()`. Follow proper structure and use `namespace Gameplay`



Click here for `GameplayService.h`

```cpp
#pragma once
#include <SFML/System/String.hpp>

namespace Gameplay
{
	class GameplayController;

	class GameplayService
	{
	private:
		GameplayController* gameplay_controller;

	public:
		GameplayService();
		~GameplayService();

		void initialize();
		void update();
		void render();

		void reset();
		
	};
}

```



Click here for `GameplayService.cpp`

```cpp
#include "Gameplay/GameplayService.h"
#include "Gameplay/GameplayController.h"

namespace Gameplay
{
	GameplayService::GameplayService()
	{
		gameplay_controller = new GameplayController();
	}

	GameplayService::~GameplayService()
	{
		delete (gameplay_controller);
	}

	void GameplayService::initialize()
	{
		gameplay_controller->initialize();
	}

	void GameplayService::update()
	{
		gameplay_controller->update();
	}

	void GameplayService::render()
	{
		gameplay_controller->render();
	}

	void GameplayService::reset()
	{
		gameplay_controller->reset();
	}
```





## gamestate and gameplay


---

Whenever you start the visualizer, there are many states that take place in it. 

The screen boots first. Then, the splash screen appears, and right after it, the main menu screen appears.

To handle these different states, `enum class GameState` is already created in `GameService.h`



The code snippet is given below:-

```cpp
// . . some code

namespace Main
{
	enum class GameState
	{
		BOOT,
		SPLASH_SCREEN,
		MAIN_MENU,
	};
	
//	. . some code

```



To display the Gameplay screen, you need to add a new state called `GAMEPLAY`.



> ✅**TODO: In **`**GameService.h**`

> 1. Update the `GameState enum class` to include a new member called `GAMEPLAY` at the end of the list.



Now, connect `GameplayService` to the `ServiceLocator`.



**Connecting **`**GameplayService **`**to **`**ServiceLocator.h**`

You have already integrated many services into **ServiceLocator**. Similarly, you have to integrate `GameplayService` into `ServiceLocator`.



> ✅**TODO: In **`**ServiceLocator.cpp**`

> 1. Integrate `GameplayService` into `ServiceLocator` by creating its property.
> 2. Calling all its lifecycle functions, creating a getter function, and finally deleting it. 
> 
> Remember: only update and render the `GameplayService` when the game's state is `GameState::GAMEPLAY`



Now, go run the code!

Did anything happen yet? Did the buttons work?

Unfortunately no!

This is because you didn't update the `MainMenuUIController`. 

When the linear search button is clicked, the `GameState` should change to `GAMEPLAY`.



## **Updating Main Menu UI Controller**


---

> ✅**TODO: MainMenuUIController.cpp**

> 1. Inside `linearSearchButtonCallback()`, set the game state to `GAMEPLAY` using `**GameService**`.



`**linearSearchButtonCallBack()**` in `MainMenuUIController.cpp` ( Click here! )

```cpp
void MainMenuUIController::linearSearchButtonCallback()
{
    ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::BUTTON_CLICK);
    GameService::setGameState(GameState::GAMEPLAY);
    ServiceLocator::getInstance()->getGameplayService()->searchElement(Gameplay::Collection::SearchType::LINEAR_SEARCH);
}
```





So, all the necessary creation and connections have been done. 

Now, it's time for the final step of the lesson!



## **Adding and rendering the background image**


---

You have already created a background image in previous projects, and the method for creating this background image is exactly the same. 



> ✅**TODO: **`**GameplayView**`** **
> 1. Create `ImageView* background_image` and `ImageView* background_image = 55.f` 
> 2. Use these properties to draw the background image in `GameplayView.h` and `GameplayView.cpp`

> 3. Initialize, update, render the background image and don't forget to delete it.



Click here for `GameplayView.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "UI/UIElement/ImageView.h"

namespace Gameplay
{
    class GameplayController;

    class GameplayView
    {
    private:
        const float background_alpha = 55.f;

        GameplayController* gameplay_controller;
        UI::UIElement::ImageView* background_image;

        sf::Font font;

        void initializeBackgroundImage();

    public:
        GameplayView();
        ~GameplayView();

        void initialize(GameplayController* gameplay_controller);
        void update();
        void render();
    };
}



```



Click here for `GameplayView.cpp`

```cpp
#include "Gameplay/GameplayView.h"
#include "Gameplay/GameplayController.h"
#include "Global/ServiceLocator.h"
#include "Global/Config.h"

namespace Gameplay
{
	using namespace UI::UIElement;
	using namespace Global;

	GameplayView::GameplayView() { background_image = new ImageView(); }

	GameplayView::~GameplayView() { delete (background_image); }

	void GameplayView::initialize(GameplayController* gameplay_controller)
	{
		this->gameplay_controller = gameplay_controller;
		initializeBackgroundImage();
	}

	void GameplayView::initializeBackgroundImage()
	{
		sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

		background_image->initialize(Config::background_texture_path,
			game_window->getSize().x,
			game_window->getSize().y,
			sf::Vector2f(0, 0));

		background_image->setImageAlpha(background_alpha);
	}


	void GameplayView::update() { background_image->update(); }

	void GameplayView::render() { background_image->render(); }
}

```





The background on the screen will look like this:-



![background image](/Full-Stack-Game-Development/images/bbba114c575baeba.png)



> Please note that the image's alpha value is set to half, which makes the pattern look faint.





By following the above steps, you’ve successfully created the `GameplayService`, set up the corresponding `View-Controller` structure, and managed the updating and rendering of the `GameState` and also rendered the background image.



In the next chapter, you'll learn about the implementation and eventually bring your project to life!
