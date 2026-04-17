# **TASKS**


---



**TODO: Create a Level Selection Screen. Add 3 buttons: one for Level One, one for Level Two, and one for the menu. Display this screen when the player clicks the Play button in the menu.**


![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_03_2024__10_19_23.png)

***Level Selection UI***



## Creating LEVEL SELECTION UI


---

## [IN MAIN MENU UI CONTROLLER]

1. Update `playButtonCallback()` :
2. 1. Set `GameState` to `LEVEL_SELECTION`



## [IN LEVEL SELECTION UI CONTROLLER]

1. Create the `LevelSelectionUIController` inheriting `IUIController` interface
2. Create the nested `namespace LevelSelection`
3. Implement lifecycle methods
4. Declare and create `ImageView` for `background_image`
5. Declare and create `ButtonView` for `level_one_button`, `level_two_button` & `menu_button`
6. Set the offset for the button and background image according to the above screen. (You can take reference from `MainMenuUIController` for offset)
7. Initialize background image.
8. Create and implement `calculateLeftOffsetForButton()` method.
9. Initialize buttons by using `calculateLeftOffsetForButton()` method.
10. Set sprites for the buttons. You can find the texture in `Config`.
11. Create `singleLinkedListButtonCallback`, `doubleLinkedListButtonCallback` & `menuButtonCallback` 
12. Implement logic for `registerButtonCallback()` 
13. Implement logic for all callback buttons and set the `GameState` to `GAMEPLAY` and call `createLevel()` passing the player input of selected level.
14. Take reference from `MainMenuUIController`.



## [IN UISERVICE]

1. Add a reference of `LevelSelectionUIController* level_selection_ui_controller`
2. Add the `namespace LevelSelection`
3. Implement the logic for `level_selection_ui_controller` similar to other controllers.



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Level**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Level**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
