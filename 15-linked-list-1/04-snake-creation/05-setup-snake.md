# **TASKS**


---



## Setting up Snake COntroller


---





## [IN Snake Controller]

1. Create `enum class SnakeState` in `SnakeController.h`
2. Create a empty method `void spawnSnake()` in `SnakeController` and call it from `spawnPlayer()` method in `PlayerService`
3. Create below properties in `SnakeController.h`
4. 1. `const int initial_snake_length = 10;`
  2. `SnakeState current_snake_state;`
5. Create the following empty methods:
6. 1. `void processPlayerInput()`
  2. `void processPlayerInput()`
  3. `void updateSnakeDirection()`
  4. `void moveSnake()` 
  5. `void processSnakeCollision()`
  6. `void handleRestart()`
  7. `void reset()`
  8. `void respawnSnake()`
7. Create a method `void setSnakeState(SnakeState state)` and inside it, set `current_snake_state = state`
8. Create a method `SnakeState getSnakeState()` and return `current_snake_state`
9. Call `processPlayerInput(), moveSnake(), processSnakeCollision()` when the `current_snake_state = ALIVE` and call `handleRestart()` when `current_snake_state = DEAD` in `update()`



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
