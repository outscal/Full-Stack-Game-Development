# **TASKS**


---



**TODO: To create and implement a Gameplay UI Controller to display the current score, current level, last operation performed & time complexity of the last operation on the play area. **



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_22_2024__06_47_02.gif)

**Top-Bar showing: Current*** ***Level, Point, Last Operation & Time Complexity**




1. Create `GameplayUIController` using `IUIController` interface in `Gameplay` file under `UI` file using nested namespaces



## **Updating SNAKECONTROLLER**


---

## [IN SNAKECONTROLLER]



1. Create enum classes for `TimeComplexity` and `LinkedListOperations`.
2. 1. TimeComplexity -> `{ NONE, ONE, N, }`
  2. LinkedListOperations -> `{ NONE, INSERT_AT_HEAD, INSERT_AT_TAIL, INSERT_AT_MID, REMOVE_AT_HEAD, REMOVE_AT_TAIL, REMOVE_AT_MID, DELETE_HALF_LIST, REVERSE_LIST }`
3. Add the following properties:

> `int player_score`
> `TimeComplexity time_complexity`
> `LinkedListOperations last_linked_list_operation`

1. Create the following getters: 

> `int getPlayerScore()`
> `TimeComplexity getTimeComplexity()`
> `LinkedListOperations getLastOperation()`

1. Inside `processFoodCollision()` , add `player_score++` whenever there is a successful collision i.e. inside `if` condition
2. Inside `reset()` method, set `player_score = 0`
3. Set the `**time_complexity**` and `**last_linked_list_operation**` in the switch case inside `OnFoodCollected()` based on the operation.



## **Updating PlayerService**


---

## [IN **PlayerService**]

1. Create the following getters that will call the getters of SnakeController:

> `int getPlayerScore()`
> `TimeComplexity getTimeComplexity()`
> `LinkedListOperations getLastOperation()`



## **Updating **LevelView


---

## [IN LevelView]

1. Add the following properties:

> `static const int border_offset_left = 40;`
> `static const int border_offset_top = 100; `
> `static const int border_offset_bottom = 40;`

1. Update the `grid_height` calculation in `calculateGridExtents()` method, 

`grid_height = game_window->getSize().y - border_offset_top - border_offset_bottom`



## **Gameplay UI Controller for Level number**


---

## [IN **GameplayUIController**]



1. Override methods from `IUIController` interface
2. Add the following properties:

> `const float font_size = 60.f;`
> `const float text_y_position = 7.f;`
> `const float level_number_text_x_position = 65.f;`
> `UI::UIElement::TextView* level_number_text;`

1. Create the following methods:

> `void createTexts();`
> `void initializeTexts();`
> `void initializeLevelNumberText();`
> `void updateLevelNumberText();`

1. Inside the constructor, call `createTexts()`
2. Inside destructor, call `destroy()`
3. Inside `createTexts()`, create`TextView` for `level_number_text`
4. Inside `initialize()`, call `initializeTexts()`
5. Inside `initializeTexts()`, call `initializeLevelNumberText()`
6. Inside `update()`, call `updateLevelNumberText()`
7. Inside `show()`, call `level_number_text->show()`
8. Inside `render()`, call `level_number_text->render()`
9. Don't forget to delete `level_number_text`
10. Implement `initializeLevelNumberText()` and inside it, initialize the `level_number_text` for level number display
11. Implement `updateLevelNumberText()` and inside it, fetch and store the level number and convert it into string , then set the `level_number_text` and then update `level_number_text`.



## **Gameplay UI Controller for player score**


---

## [IN **GameplayUIController**]



1. Add the following properties:

> `const float score_text_x_position = 800.f;`
> `UI::UIElement::TextView* score_text;`

1.  Create the following methods:

> `void initializeScoreText();`
> `void updateScoreText();`

1. Similar to `level_number_text`, implement the same logic.
2. Implement `updateScoreText()` and inside it, fetch and store the player score and convert it into string, then set the `score_text` and then update `score_text`.



## **Gameplay UI Controller for LAST OPERATION**


---

## [IN **GameplayUIController**]



1. Add the following properties:

> `const float operations_font_size = 36.f;`
> `const float operations_text_x_position = 1330.f;`
> `const float operations_text_y_position = 10.f;`
> `UI::UIElement::TextView* operation_text;`

1.  Create the following methods:

> `void initializeOperationText();`
> `void updateOperationText();`

1. Similar to `level_number_text`, implement the same logic.
2. Implement the logic for `updateOperationText()`and inside it, use a switch case that will work based on the operation it gets. And then set and update the `TextView` of `operation_text`.



## **Gameplay UI Controller for TIME COMPLEXITY**


---

## [IN **GameplayUIController**]



1. Add the following properties:

> `const float time_complexity_text_x_position = 1330.f;`
> `const float time_complexity_text_y_position = 45.f;`
> `UI::UIElement::TextView* time_complexity_text;`

1.  Create the following methods:

> `void initializeTimeComplexityText();`
> `void updateTimeComplexityText();`

1. Similar to `level_number_text`, implement the same logic.
2. Implement the logic for `updateOperationText()`and inside it, use a switch case that will work based on the time complexity it gets. And then set and update the `TextView` of `time_complexity_text`.




# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Linked-List-Operations**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Linked-List-Operations**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
