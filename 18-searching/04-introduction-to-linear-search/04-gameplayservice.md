# **TASKS**


---

1. Create `GameplayView`, `GameplayController` and `GameplayService` classes with empty lifecycle methods and follow `namespace Gameplay` 



## Creating Gameplay Service


---



## [IN GAMESERVICE.H]

1. Update the `GameState enum class` to include a new member called `GAMEPLAY`.



## [IN SERVICELOCATOR.CPP]

1. Update and render `GameplayService` only when **GameState** is set to **GAMEPLAY.**



## [IN MAINMENUUICONTROLLER.CPP]

1. Inside `linearSearchButtonCallback()`, change the game state to GAMEPLAY using `**GameService**`.

## [IN GAMEPLAYVIEW.H]

1. Create `ImageView* background_image` and `ImageView* background_image = 55.f` 
2. Use these properties to draw the background image in `GameplayView.h` and `GameplayView.cpp` 
3. Initialize, update, render the background image and don't forget to delete it.





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Linear-Search**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Linear-Search**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
