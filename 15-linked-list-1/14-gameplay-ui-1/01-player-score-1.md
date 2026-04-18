**It's time for Gameplay UI !! 💯**



Every game needs a way to track progress, and what's better than a score?

Scores make the game more fun! You can see how well you're doing and try to beat your own score or compete with friends.



In your snake game, you'll implement a logic that increases the player's score each time the snake eats food. 🍎🐍



Take a look at what you're aiming for. In this chapter, you'll focus on the Gameplay UI.


![gif](/Full-Stack-Game-Development/images/a71e0c74e904bd72.gif)

***Top-Bar showing: Current**** ****Level, Point, Last Operation & Time Complexity***



> **🧠 Fun Fact: **Did you know that the original arcade version of **Pac-Man** has a maximum score of **3,333,360** points? This score can only be achieved if the player completes all 256 levels without losing a single life and eating every possible point along the way, including all dots, fruits, and ghosts.



Like in many classic games, your snake game will also increase the player's score whenever the snake eats food. 





## **player score and current level**


---

Every time the snake eats food, the player's score should increase. Simple, right? 

Here's how you'll go about it.



> **TODO: SnakeController**
> ✅ Create a property `int player_score` for score
> ✅ Inside `processFoodCollision()` , add `player_score++` whenever there is successful collision i.e inside `if` condition
> ✅ Inside `reset()` method, set `player_score = 0`
> ✅ Create a getter `getPlayerScore()` for score in `SnakeController` and `PlayerService`



Showing the player's score on the screen is crucial to provide immediate feedback and enhance the gaming experience.

At the end of this section, your screen should look like this:



![Image](/Full-Stack-Game-Development/images/c9c96dab2a4efe81.png)

***Level & Score Visible on Screen***



To get this UI, you'll set up a `GameplayUIController` class that updates in real-time to show the current level and current score.

To make it happen, set the properties for both Level text and Score text and create methods to initialize and update these texts. 



> **TODO: GameplayUIController**
> ✅ Create `GameplayUIController` using `IUIController` interface in `Gameplay` file under `UI` file using nested namespaces
> ✅ Override methods from `IUIController` interface
> ✅ Add the following properties:

> `const float font_size = 60.f;`
> `const float text_y_position = 7.f;`
> `const float level_number_text_x_position = 65.f;`
> `const float score_text_x_position = 800.f;`
> `UI::UIElement::TextView* level_number_text;`
> `UI::UIElement::TextView* score_text;`

> ✅ Create the following methods:

> `void createTexts();`
> `void initializeTexts();`
> `void initializeLevelNumberText();`
> `void initializeScoreText();`
> `void updateLevelNumberText();`
> `void updateScoreText();`



**Click here to see **`GameplayUIController.h````cpp
#pragma once
#include "UI/Interface/IUIController.h"
#include "UI/UIElement/TextView.h"

namespace UI
{
	namespace GameplayUI
	{
		class GameplayUIController : public Interface::IUIController
		{
		private:
			// Constants:
			const float font_size = 60.f;

			const float text_y_position = 7.f;
			const float level_number_text_x_position = 65.f;
			const float score_text_x_position = 800.f;

			UI::UIElement::TextView* level_number_text;
			UI::UIElement::TextView* score_text;

			void createTexts();
			void initializeTexts();
			void initializeLevelNumberText();
			void initializeScoreText();

			void updateLevelNumberText();
			void updateScoreText();

			void destroy();

		public:
			GameplayUIController();
			~GameplayUIController();

			void initialize() override;
			void update() override;
			void render() override;
			void show() override;
		};
	}
}

```



Implement a skeleton for logic building in the `**GameplayUIController**`.



> **TODO: GameplayUIController**
> ✅ Inside constructor, call `createTexts()`
> ✅ Inside destructor, call `destroy()`
> ✅ Inside `createTexts()`, create`TextView` for `level_number_text` & `score_text`
> ✅ Inside `initialize()`, call `initializeTexts()`
> ✅ Inside `initializeTexts()`, call `initializeLevelNumberText()` & `initializeScoreText()`
> ✅ Inside `update()`, call `updateLevelNumberText()` & `updateScoreText()`
> ✅ Inside `show()`, call `level_number_text->show()` & `score_text->show()`
> ✅ Inside `render()`, call `level_number_text->render()` & `score_text->render()`
> ✅ Don't forget to delete `level_number_text` & `score_text` inside `destroy()`





## understanding methods of **Gameplay UI Controller**


---

- In `initializeLevelNumberText()` and `initializeScoreText()` you're initializing the `TextView` of the particular text passing the necessary parameters.



- In `updateLevelNumberText()`, you fetch the current level data from `LevelService`, then setting the text according to the current level and then updating the `TextView`.



- `updateScoreText()` fetches the latest player score form `PlayerService`, ensuring your score display stays in sync with the player's score. 


Have a look at the implementation:

```cpp
// Initialize text for level number display
void GameplayUIController::initializeLevelNumberText()
        {
            level_number_text->initialize("Level : 1", sf::Vector2f(level_number_text_x_position, text_y_position), FontType::BUBBLE_BOBBLE, font_size, sf::Color::Black);
        }
// Initialize text for score display
        void GameplayUIController::initializeScoreText()
        {
            score_text->initialize("Score : 0", sf::Vector2f(score_text_x_position, text_y_position), FontType::BUBBLE_BOBBLE, font_size, sf::Color::Black);
        }
// Update level number text based on current level
        void GameplayUIController::updateLevelNumberText()
        {
            LevelNumber level_number = ServiceLocator::getInstance()->getLevelService()->getCurrentLevel();
            sf::String level_number_value = std::to_string(1 + static_cast<int>(level_number));

            level_number_text->setText("Level : " + level_number_value);
            level_number_text->update();
        }
// Update score text based on current player score
        void GameplayUIController::updateScoreText()
        {
            int player_score = ServiceLocator::getInstance()->getPlayerService()->getPlayerScore();
            sf::String score_value = std::to_string(player_score);

            score_text->setText("Score : " + score_value);
            score_text->update();
        }
```



> **TODO: GameplayUIController**
> ✅ Using the above script update `initializeLevelNumberText()`, `initializeScoreText()`, `updateLevelNumberText()` & `updateScoreText()`



**Click here to see **`GameplayUIController.cpp````cpp
#include "UI/GameplayUI/GameplayUIController.h"
#include "Main/GameService.h"
#include "Graphics/GraphicService.h"
#include "Sound/SoundService.h"
#include "Event/EventService.h"
#include "Global/Config.h"
#include "Level/LevelModel.h"
#include "Player/PlayerService.h"

namespace UI
{
    namespace GameplayUI
    {
        using namespace Global;
        using namespace Event;
        using namespace Sound;
        using namespace Main;
        using namespace Graphics;
        using namespace Level;
        using namespace Player;
        using namespace UI::UIElement;

        GameplayUIController::GameplayUIController()
        {
            createTexts();
        }

        GameplayUIController::~GameplayUIController()
        {
            destroy();
        }

        void GameplayUIController::initialize()
        {
            initializeTexts();
        }

        void GameplayUIController::createTexts()
        {
            level_number_text = new TextView();
            score_text = new TextView();
            time_complexity_text = new TextView();
            operation_text = new TextView();
        }

        void GameplayUIController::initializeTexts()
        {
            initializeLevelNumberText();
            initializeScoreText();
        }

        void GameplayUIController::initializeLevelNumberText()
        {
            level_number_text->initialize("Level : 1", sf::Vector2f(level_number_text_x_position, text_y_position), FontType::BUBBLE_BOBBLE, font_size, sf::Color::Black);
        }

        void GameplayUIController::initializeScoreText()
        {
            score_text->initialize("Score : 0", sf::Vector2f(score_text_x_position, text_y_position), FontType::BUBBLE_BOBBLE, font_size, sf::Color::Black);
        }

        void GameplayUIController::updateLevelNumberText()
        {
            LevelNumber level_number = ServiceLocator::getInstance()->getLevelService()->getCurrentLevel();
            sf::String level_number_value = std::to_string(1 + static_cast<int>(level_number));

            level_number_text->setText("Level : " + level_number_value);
            level_number_text->update();
        }

        void GameplayUIController::updateScoreText()
        {
            int player_score = ServiceLocator::getInstance()->getPlayerService()->getPlayerScore();
            sf::String score_value = std::to_string(player_score);

            score_text->setText("Score : " + score_value);
            score_text->update();
        }

        void GameplayUIController::update()
        {
            updateLevelNumberText();
            updateScoreText();
        }

        void GameplayUIController::render()
        {
            level_number_text->render();
            score_text->render();
        }

        void GameplayUIController::show()
        {
            level_number_text->show();
            score_text->show();
        }

        void GameplayUIController::destroy()
        {
            delete (level_number_text);
            delete (score_text);
        }
    }
}
```





## making space for level and point text


---

Now that you've implemented the logic for the `TextView`, it's time to make space for these texts on the screen.



Currently, the **grid dimensions** are calculated as follows:

```cpp
//LevelView.h
static const int border_offset_left = 40;
static const int border_offset_top = 40;

//LevelView.cpp
void LevelView::calculateGridExtents() {
    sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

    grid_width = game_window->getSize().x - 2 * border_offset_left;
    grid_height = game_window->getSize().y - 2 * border_offset_top;
}
```

Because of these properties, the spaces outside borders looked like this:

![Image](/Full-Stack-Game-Development/images/94a0b23c719ab699.png)

***Current Screen***



To make space for the Level and Point display, you need to adjust the top border offset. 

This change will shift the top border down, creating the necessary space for the UI elements. 



Here’s the updated code:

```cpp
//LevelView.h
static const int border_offset_left = 40;
static const int border_offset_top = 100;  // Increased top offset
static const int border_offset_bottom = 40;

//LevelView.cpp
void LevelView::calculateGridExtents() {
    sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

    grid_width = game_window->getSize().x - 2 * border_offset_left;
    grid_height = game_window->getSize().y - border_offset_top - border_offset_bottom;  // Adjusted to new top and bottom offsets
}
```



> **TODO: LevelView**
> ✅ Update the border offsets in `LevelView.h` and `LevelView.cpp` as shown above.



**Run your code,** and you should see your screen with the level and score visible at the top. 



![Image](/Full-Stack-Game-Development/images/c9c96dab2a4efe81.png)



**Good job!**

You've now set up the UI to display the score and level, making your game more engaging and visually appealing. 



In the next section, you'll explore how to further enhance the gameplay experience by adding more features in the UI. 

**See you there!👋🏼**
