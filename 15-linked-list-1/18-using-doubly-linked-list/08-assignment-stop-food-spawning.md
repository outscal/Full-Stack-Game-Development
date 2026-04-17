# **Tasks**


---



## IMPLEMENTING FOOD SPAWN STOP


---

## [IN **SnakeController, **PlayerService** & **FoodService]



1. In `SnakeController`: Create `bool SnakeController::isSnakeDead()` and inside it returns true if the snake is dead.
2. In `PlayerService`: Create `bool PlayerService::isPlayerDead()` and inside it return if the player is dead using `SnakeController::isSnakeDead()`.
3. In `FoodService`: inside `handleFoodSpawning()` exit the function if the player is dead. Check this using `PlayerService`'s `isPlayerDead()`.





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-5-Doubly-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-5-Doubly-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
