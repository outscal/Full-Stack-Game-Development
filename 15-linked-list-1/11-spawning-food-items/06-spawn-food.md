# **TASKS**


---



## SPAWN BURGER


---

1. Create empty `FoodService` classes with empty lifecycle methods and follow `namespace Food` 



## [IN **FoodService**]

1. Create the following properties:

> `FoodItem* current_food_item `
> `float cell_width `
> `float cell_height `

1. Initialize `current_food_item` with `nullptr` in `constructor` 
2. Create `void startFoodSpawning()` and inside it set `cell_width` & `cell_height`
3. Create `FoodItem* createFood(sf::Vector2i position, FoodType type)` and inside it:
4. 1. Create a new object of `FoodItem`
  2. Initialize that object passing necessary parameters.
5. Create `void spawnFood()` and inside it:
6. 1. Call `current_food_item = createFood(sf::Vector2i(4, 6), FoodType::BURGER)`
7. Call `spawnFood()` from `startFoodSpawning()`
8. Call lifecycle methods of `current_food_item` from `FoodService`'s lifecycle methods, but mak sure `current_food_item` is not null.
9. Don't forget to delete `current_food_item`.



## [IN **SERVICELOCATOR**]

1. Create a reference of `FoodService` as `food_service` and set it `nullptr` in `constructor`.
2. Create a `getFoodService()` getter function that returns the reference of `food_service`.
3. Create an object of `FoodService` in `createServices()`
4. Call lifecycle functions of `food_service` just take care that `update()` & `render()` should only be called if the `GameState` is `GAMEPLAY`.
5. Don't forget to delete the object of `FoodService`.



## [IN **LevelService**]

1. Create `void spawnFood()` and inside it call `startFoodSpawning()`.
2. Call `spawnFood()` inside `createLevel()`

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-3-Food-Spawning**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-3-Food-Spawning**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
