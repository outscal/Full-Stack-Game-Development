**Gameplay UI Controller **is responsible for managing and displaying the user interface (UI) elements specific to the gameplay screen in a game.



It performs the following roles:-

- **Manages Game Info Displays:** Controls UI elements showing player stats, game mechanics.
- **Creates UI Elements:** Text views, buttons, etc.
- **Updates UI with Game Data:** Fetches information from the game like scores and displays it on UI elements.
- **Renders UI:** If not using a UI framework, it might draw UI elements on the screen.
- **Handles User Input:** Processes button presses or interactions with UI elements.



Let's proceed with creating `GameplayUIController` for this project.



## Creating Gameplay UI COntroller


---

1. Create a subfolder named `GameplayUI` inside the `UI` folder.
2. Create `GameplayUIController.h` and `GameplayUIController.cpp`
3. Connect `gameplay_ui_controller` to `UIService`.





## [in GameplayUIController.h]

1. Add `#pragma once` to prevent multiple inclusions.
2. Include these necessary header files:

- - `IUIController.h` for the UI interface.
  - `TextView.h`, `ButtonView.h`, and `ImageView.h` for UI elements.
  - `GameplayService.h` for interacting with gameplay logic.

1. Declare namespaces, namely `UI` and `GameplayUI`
2. Declare the `GameplayUIController` class inheriting from `IUIController`.
3. Define private member variables for `TextView` and `ButtonView` 
4. - TextView:
  - -  search type
    - number of comparisons
    - number of array access
    - num sticks
    - delay
    - time complexity.
  - ButtonView: 
  - - menu button.
5. Define private constants for position and size.
6. Declare private methods for creating, initializing, updating, and destroying UI elements.
7. Declare public methods for initializing, updating, rendering, and showing the UI.





## [in gameplayuicontroller.cpp]

1. Include the header file `GameplayUIController.h` to access class declarations and definitions.
2. Include other header files needed for implementation like `Config`, `ServiceLocator`.
3. Use the suitable namespaces to access class members.
4. Define the constructor to initialize UI elements:
5. - createButton()
  - createTexts()
6. Implement the corresponding destructor.
7. Implement the `initialize()` method to set up UI elements.
8. Within this method, call:-
9. - initializeButton();
  - initializeTexts();
  - updateSearchTypeText();
10. Implement all the methods mentioned above.
11. Implement the `update()` method to update UI elements based on the current game state.
12. Within this method, call:-
13. -  updateSearchTypeText();
  -  updateComparisonsText();
  -  updateArrayAccessText();
  -  updateNumberOfSticksText();
  -  updateDelayText();
  -  updateTimeComplexityText();
14. Implement the methods mentioned above.
15. Implement the `render()` method to render UI elements onto the screen.
16. Implement the `show()` method to show UI elements based on the current gameplay state.
17. Implement the `menuButtonCallback()` method to handle button clicks.
18. Implement the `registerButtonCallback()` method to register the button callback function.
19. - Within this method, use `menu_button` to register the callback function defined in `menuButtonCallback()`.
20. Implement the `destroy()` method to deallocate dynamically allocated resources. Delete the memory allocated for:-
21. 1.  menu_button
  2.  search_type_text
  3.  number_of_comparisons_text
  4.  number_of_array_access_text





All the codes are given in the solution branch. You can double-check them in case you missed anything.



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Linear-Search**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Linear-Search**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
