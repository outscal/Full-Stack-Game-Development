# **TASKS**


---



## Random food spawning


---



## [IN SingleLinkedList]

1. Create `getNodesPositionList()` and return the list of positions of all body parts of the snake. 



## [IN **SnakeController**]

1. Create `getCurrentSnakePositionList()` and call `SingleLinkedList`'s `getNodesPositionList()` and then return a vector list.



## [IN **PlayerService**]

1. Create `getCurrentSnakePositionList()` and call the `SnakeController`'s helper function `getCurrentSnakePositionList()` and then return a vector list.



## [IN Obstacle]

1. Create `getObstaclePosition()` and return the position of obstacle. 



## [IN **ElementService**]

1. Create `getElementsPositionList()` and return the list of positions of all elements (obstacles). Use helper function `getObstaclePosition()`.



## [IN **FoodService**]

1. Create the following properties:

> `std::default_random_engine random_engine;`
> `std::random_device random_device;`

1. Initialize `random_engine` with `random_device()` in the initializer list.
2. Create `isValidPosition(std::vector<sf::Vector2i> position_data, sf::Vector2i food_position)` to return a boolean.
3. Create `getRandomPosition()` that returns the random position inside the screen.
4. Create `getValidSpawnPosition()` & inside it:
5. 1. Call `getCurrentSnakePositionList()` to fetch and store the `player_position_data`
  2. Call `getElementsPositionList()` to fetch and store the `elements_position_data`
  3. Call `getRandomPosition()` to fetch and store the `spawn_position` of food.
  4. Call the `isValidPosition()` to check if the `spawn_position` is valid or not.
  5. Return valid `spawn_position`.
6. Create and implement `getRandomFoodType()` and return random food types.
7. Update `spawnFood()` method and call `createFood()` passing valid spawn position and random food type.

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-3-Food-Spawning**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-3-Food-Spawning**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
