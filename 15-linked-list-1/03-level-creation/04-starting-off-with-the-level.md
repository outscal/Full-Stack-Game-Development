# **TASKS**


---



## Level creation


---

1. Create Empty `LevelModel`, `LevelView`, `LevelController` and `LevelService` classes with empty lifecycle methods and follow `namespace Level` 



## [IN LevelNumber]

1. Create an enum class `LevelNumber` follow  `namespace Level` 
2. Add enums `ONE` & `TWO`



## [IN LevelService]

1. Create a reference of `LevelController` and call its lifecycle methods.
2. Create a property  `LevelNumber current_level`
3. Create `void createLevel(LevelNumber level_to_load)` to set `current_level`



## [IN LevelData]

1. Create a struct `LevelData` inside `Level` to represent data for a specific level.
2. Include the `LevelService` and follow `namespace Level` 





## create level border and background


---

## [IN LevelView]

1. Create the following properties:
2. 1. `const sf::Color background_color = sf::Color(180, 200, 160)`
  2. `RectangleShapeView* background_rectangle`
  3. `RectangleShapeView* border_rectangle` 
3. Create `createViews()` method and inside it create `RectangleShapeView` for `background_rectangle` & `border_rectangle` 
4. Call `createViews()` inside `constructor`
5. Create `initializeButtonImage()`  & inside it:
6. 1. Calculate background size w.r.t. game window from `GraphicService` 
  2. Make necessary calls like `initialize()` & `show()`  for `background_rectangle`
7. Create offsets and thickness properties for border
8. Create properties for `grid_width` & `grid_height` and also make getter functions for them
9. Create `calculateGridExtents()` to calculate `grid_width` and `grid_height`
10. Create `initializeBorder()` & inside it:
11. 1. Create a `Vector2f` of size by using `grid_width` and `grid_height`
  2. Make necessary calls like `initialize()` & `show()`  for `border_rectangle`
12. Call `initializeButtonImage()` , `calculateGridExtents()` & `initializeBorder()` inside `initialize()`
13. Implement the remaining lifecycle methods.





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Level**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Level**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
