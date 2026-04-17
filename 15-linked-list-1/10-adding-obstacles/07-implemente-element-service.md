# **TASKS**


---



## CREATE OBSTACLES


---

1. Create `ElementService` class with empty lifecycle methods and follow `namespace Element`



## [IN ElementService]

1. Add the following properties:

> `std::vector<Obstacle*> obstacle_list;`

1. Create and implement `spawnObstacle(sf::Vector2i position, float cell_width, float cell_height)`
2. Create and implement `const void spawnElements(std::vector<ElementData>& element_data_list, float cell_width, float cell_height)`
3. Call `obstacle_list` in a loop in `update()` and `render()`



## [IN **ServiceLocator**]

1. Create a reference of `ElementService` as `element_service` and set it `nullptr` in `constructor`.
2. Create a `getElementService()` getter function that returns the reference of `element_service`.
3. Create an object of `ElementService` in `createServices()` 
4. Call lifecycle functions of `element_service` just take care that `update()` & `render()` should only be called if the `GameState` is `GAMEPLAY`.
5. Don't forget to delete the object of `ElementService`.



## [IN **LevelData**]

1. Add `std::vector<Element::ElementData>element_data_list`
2. Pass the `std::vector<Element::ElementData>* data_list` in `constructor` and set the `element_data_list`



## [IN **LevelModel**]

1. Add the following properties:

> `std::vector<Element::ElementData> level_one_element_list;`

> `std::vector<Element::ElementData> level_two_element_list;`

> `std::vector<LevelData> level_configurations;`

1. Create and implement a `private` method `void initializeLevelData()`
2. Create a getter `const std::vector<Element::ElementData>& getElementDataList(int level_to_load)` 



## [IN **LevelController**]

1. Create a getter `const std::vector<Element::ElementData>& getElementDataList(int level_to_load)` 



## [IN **LevelService**]

1. Create `spawnLevelElements(LevelNumber level_to_load)` and call it from `createLevel()`
2. Call `spawnElements(element_data_list, cell_width, cell_height)` from `spawnLevelElements()`

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
