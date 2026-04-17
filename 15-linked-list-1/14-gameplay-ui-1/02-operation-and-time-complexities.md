**Let's Add More To Gameplay UI!!**

In this section, you'll add more features to your game by displaying operations and time complexities. 

This feature will not only be an interesting addition for players but will also showcase your **technical skills. 😎**



**Why display operations and time complexities? 🤔**

Imagine you're playing your snake game, and you can see in real-time what operations are being performed and their time complexities. 

Sounds cool, right? 😮



You know the effects of each food type on the snake, but your Gamedev friend doesn’t. 

Your Gamedev friend isn't familiar with these effects yet. They don't know which food does what.

Now, imagine you have 100 Gamedev friends who are all curious about these details. 

Instead of explaining it to everyone, wouldn't it be better to display these operations and their complexities in the game? 🤩



> 🧠 **Fun Fact:** Time complexity is a crucial concept that describes the efficiency of an algorithm. By displaying time complexity and operations in your game, you’re giving tech enthusiasts and potential recruiters a peek into your technical skills. It’s like adding a signature of your coding expertise right into the gameplay. Plus, it’s a unique feature that sets your game apart from others.



To accurately manage and display these values, you need properties to track which **operations** are performed and their **time complexity**. 

For that, create enums for `TimeComplexity` and `LinkedListOperations`. They will help to represent the time complexity and linked list operations in the form of enums.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_04_2024__13_43_23.png)

***Operation to Time Table***



## **Creating enums in SnakeController**

```cpp
//SnakeController.h
enum class TimeComplexity
{
	NONE,
	ONE,
	N,
};

enum class LinkedListOperations
{
	NONE,
	INSERT_AT_HEAD,
	INSERT_AT_TAIL,
	INSERT_AT_MID,
	REMOVE_AT_HEAD,
	REMOVE_AT_TAIL,
	REMOVE_AT_MID,
	DELETE_HALF_LIST,
	REVERSE_LIST,
};
```



> **TODO: SnakeController.h**
> ✅ Create enum classes for `TimeComplexity` and `LinkedListOperations`.





## starting off with Time Complexity** AND **Linked List Operations display in gameplay UI


---

Current operations and its time complexity can only be tracked from `**SnakeController**` because `**SnakeController**` is the brain that controls the snake's operation according to the food. 

So, it is required to add the properties for the current operation and its time complexity in the `SnakeController`.





> **TODO: **`**SnakeController**`
> ✅ Add the following properties:
> `TimeComplexity time_complexity`
> `LinkedListOperations last_linked_list_operation`

> 

> **TODO: **`**SnakeController**`** & **`**PlayerService**`
> ✅ Create the following getters for these properties in `SnakeController` and `PlayerService`: 
> `TimeComplexity getTimeComplexity()`
> `LinkedListOperations getLastOperation()`



Now that you've created enums, it's time to set the properties using them. 



How can you set your properties? 🤔

You already have done something similar earlier.



Click here to check the answer.

You already have a **switch case **to handle operations based on `food_type`. 

Each food type corresponds to a specific operation in your game.

Using this **switch case** can help you to track and update these properties.



> **TODO: SnakeController**
> ✅ Set the `**time_complexity**` and `**last_linked_list_operation**` based on operation.



Naah! Naah! I am not gonna help, as you already know the time complexities of these operations. I know you can do it. 💪

The getter functions for these properties will help the `GameplayUIController` to stay in sync with the operations.



## Updating gameplay UI Controller to display operations and time


---

To display these new texts, update the `GameplayUIController` to show the current operation and its time complexity on the screen.



> **TODO: GameplayUIController**
> ✅ Add the following properties:

> `const float operations_font_size = 36.f;`
> `const float operations_text_x_position = 1330.f;`
> `const float operations_text_y_position = 10.f;`
> `const float time_complexity_text_x_position = 1330.f;`
> `const float time_complexity_text_y_position = 45.f;`
> `UI::UIElement::TextView* time_complexity_text;`
> `UI::UIElement::TextView* operation_text;`

> ✅ Create the following methods:

> `void initializeTimeComplexityText();`
> `void initializeOperationText();`
> `void updateTimeComplexityText();`
> `void updateOperationText();`



The logic for the operations and time text view will be similar to the one you made for the level and point text view.



> **TODO: GameplayUIController**
> ✅ Inside `createTexts()`, initialize `TextView()` for `time_complexity_text` & `operation_text`
> ✅ Inside `initializeTexts()`, call `initializeTimeComplexityText()` & `initializeOperationText()`
> ✅ Inside `update()`, call `updateTimeComplexityText()` & `updateOperationText()`
> ✅ Inside `show()`, call `time_complexity_text->show()` & `operation_text->show()`
> ✅ Inside `render()`, call `time_complexity_text->render()` & `operation_text->render()`
> ✅ Don't forget to delete `time_complexity_text` & `operation_text` inside `destroy()`





Here's the implementation to Initialize the `initializeTimeComplexityText()` & `initializeOperationText()`:

```cpp
// Initialize text for time complexity display 
void GameplayUIController::initializeTimeComplexityText()
        {
            time_complexity_text->initialize("Time Complexity : O(1)", sf::Vector2f(time_complexity_text_x_position, time_complexity_text_y_position), FontType::BUBBLE_BOBBLE, operations_font_size, sf::Color::Black);
        }

// Initialize text for operation display
        void GameplayUIController::initializeOperationText()
        {
            operation_text->initialize("Last Operation : Insert at Middle", sf::Vector2f(operations_text_x_position, operations_text_y_position), FontType::BUBBLE_BOBBLE, operations_font_size, sf::Color::Black);
        }
```



> **TODO: GameplayUIController**
> ✅ Implement the `initializeTimeComplexityText()`, `initializeOperationText()`



But hold on, this isn't over yet! 



Now, it's time to implement the logic behind `updateTimeComplexityText()` and `updateOperationText()`:

- In `updateTimeComplexityText()`, you're fetching the current time complexity from `PlayerService` and assigning a string representation to display. 

  For this, you can use a switch case that will work based on the time complexity it gets. And then set and update the `TextView` of
  time complexity text.



> **TODO: GameplayUIController**
> ✅ Implement the logic for `updateTimeComplexityText()`



- Similarly, in `updateOperationText()`, you're determining the last operation performed, so fetch it from `PlayerService` and set its string representation accordingly.

  For this, you can use a switch case that will work based on the operation it gets. And then set and update the `TextView` of
  operation text.



> **TODO: GameplayUIController**
> ✅ Implement the logic for `updateOperationText()`



You can click here to check the implementation to update the text views (I won't tell anyone🤫)```cpp
void GameplayUIController::updateTimeComplexityText()   // Update time complexity text based on current player performance
{
// Get time complexity from player service
    TimeComplexity time_complexity = ServiceLocator::getInstance()->getPlayerService()->getTimeComplexity();
    sf::String time_complexity_value;

// Convert complexity to string based on enum value
    switch (time_complexity)
    {
    case TimeComplexity::NONE:
        time_complexity_value = "";
    case TimeComplexity::ONE:
        time_complexity_value = "1";
        break;
    case TimeComplexity::N:
        time_complexity_value = "N";
        break;
    }
    
    // Update text with formatted time complexity
    time_complexity_text->setText("Time Complexity : (" + time_complexity_value + ")");
    time_complexity_text->update();
}

// Update operation text based on last linked list operation
void GameplayUIController::updateOperationText()
{
// Get last operation type from player service
    LinkedListOperations operation = ServiceLocator::getInstance()->getPlayerService()->getLastOperation();
    sf::String operation_value;

	// Convert operation type to string based on enum value
    switch (operation)
    {
    case LinkedListOperations::NONE:
        operation_value = "";
    case LinkedListOperations::INSERT_AT_HEAD:
        operation_value = "Insert at Head";
        break;
    case LinkedListOperations::INSERT_AT_TAIL:
        operation_value = "Insert at Tail";
        break;
    case LinkedListOperations::INSERT_AT_MID:
        operation_value = "Insert at Mid";
        break;
    case LinkedListOperations::REMOVE_AT_HEAD:
        operation_value = "Remove at Head";
        break;
    case LinkedListOperations::REMOVE_AT_TAIL:
        operation_value = "Remove at Tail";
        break;
    case LinkedListOperations::REMOVE_AT_MID:
        operation_value = "Remove at Mid";
        break;
    case LinkedListOperations::DELETE_HALF_LIST:
        operation_value = "Delete Half List";
        break;
    case LinkedListOperations::REVERSE_LIST:
        operation_value = "Reverse List";
        break;

    }

// Update text with formatted operation information
    operation_text->setText("Last Operation : " + operation_value);
    operation_text->update();
}
```





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

			// Constants: Operations and Time Complexities
			const float operations_font_size = 36.f;
			const float operations_text_x_position = 1330.f;
			const float operations_text_y_position = 10.f;
			const float time_complexity_text_x_position = 1330.f;
			const float time_complexity_text_y_position = 45.f;

			UI::UIElement::TextView* level_number_text;
			UI::UIElement::TextView* score_text;
			UI::UIElement::TextView* time_complexity_text;
			UI::UIElement::TextView* operation_text;

			void createTexts();
			void initializeTexts();
			void initializeLevelNumberText();
			void initializeScoreText();
			void initializeTimeComplexityText();
			void initializeOperationText();

			void updateLevelNumberText();
			void updateScoreText();
			void updateTimeComplexityText();
			void updateOperationText();

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
            initializeTimeComplexityText();
            initializeOperationText();
        }

        void GameplayUIController::initializeLevelNumberText()
        {
            level_number_text->initialize("Level : 1", sf::Vector2f(level_number_text_x_position, text_y_position), FontType::BUBBLE_BOBBLE, font_size, sf::Color::Black);
        }

        void GameplayUIController::initializeScoreText()
        {
            score_text->initialize("Score : 0", sf::Vector2f(score_text_x_position, text_y_position), FontType::BUBBLE_BOBBLE, font_size, sf::Color::Black);
        }

        void GameplayUIController::initializeTimeComplexityText()
        {
            time_complexity_text->initialize("Time Complexity : O(1)", sf::Vector2f(time_complexity_text_x_position, time_complexity_text_y_position), FontType::BUBBLE_BOBBLE, operations_font_size, sf::Color::Black);
        }

        void GameplayUIController::initializeOperationText()
        {
            operation_text->initialize("Last Operation : Insert at Middle", sf::Vector2f(operations_text_x_position, operations_text_y_position), FontType::BUBBLE_BOBBLE, operations_font_size, sf::Color::Black);
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

        void GameplayUIController::updateTimeComplexityText()
        {
            TimeComplexity time_complexity = ServiceLocator::getInstance()->getPlayerService()->getTimeComplexity();
            sf::String time_complexity_value;

            switch (time_complexity)
            {
            case TimeComplexity::NONE:
                time_complexity_value = "";
            case TimeComplexity::ONE:
                time_complexity_value = "1";
                break;
            case TimeComplexity::N:
                time_complexity_value = "N";
                break;
            }
            time_complexity_text->setText("Time Complexity : (" + time_complexity_value + ")");
            time_complexity_text->update();
        }

        void GameplayUIController::updateOperationText()
        {
            LinkedListOperations operation = ServiceLocator::getInstance()->getPlayerService()->getLastOperation();
            sf::String operation_value;

            switch (operation)
            {
            case LinkedListOperations::NONE:
                operation_value = "";
            case LinkedListOperations::INSERT_AT_HEAD:
                operation_value = "Insert at Head";
                break;
            case LinkedListOperations::INSERT_AT_TAIL:
                operation_value = "Insert at Tail";
                break;
            case LinkedListOperations::INSERT_AT_MID:
                operation_value = "Insert at Mid";
                break;
            case LinkedListOperations::REMOVE_AT_HEAD:
                operation_value = "Remove at Head";
                break;
            case LinkedListOperations::REMOVE_AT_TAIL:
                operation_value = "Remove at Tail";
                break;
            case LinkedListOperations::REMOVE_AT_MID:
                operation_value = "Remove at Mid";
                break;
            case LinkedListOperations::DELETE_HALF_LIST:
                operation_value = "Delete Half List";
                break;
            case LinkedListOperations::REVERSE_LIST:
                operation_value = "Reverse List";
                break;

            }

            operation_text->setText("Last Operation : " + operation_value);
            operation_text->update();
        }

        void GameplayUIController::update()
        {
            updateLevelNumberText();
            updateScoreText();
            updateTimeComplexityText();
            updateOperationText();
        }

        void GameplayUIController::render()
        {
            level_number_text->render();
            score_text->render();
            time_complexity_text->render();
            operation_text->render();
        }

        void GameplayUIController::show()
        {
            level_number_text->show();
            score_text->show();
            time_complexity_text->show();
            operation_text->show();
        }

        void GameplayUIController::destroy()
        {
            delete (level_number_text);
            delete (score_text);
            delete (time_complexity_text);
            delete (operation_text);
        }
    }
}
```



Now, you are able to see everything on the screen: score, current level, time complexity of operations, and last operation performed. 

Your screen should look like this:

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_22_2024__06_47_02.gif)



**Great job! You can flex this on LinkedIn or show it off to your friends. **

Your game has become more fun to play and is also a great portfolio piece highlighting your coding skills.** **Keep up the fantastic work!✨



**See you in the next chapter 👋**
