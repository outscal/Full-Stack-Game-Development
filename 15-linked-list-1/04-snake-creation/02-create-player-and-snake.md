# **TASKS**


---



## Create Player Service


---

1. Create files for `SnakeController` and `PlayerService` classes inside `Player` folder and use `namespace Player` 
2. Create empty lifecycle methods inside `SnakeController` and `PlayerService`



## [IN **PlayerService**]

1. Create a property `SnakeController* snake_controller` 
2. Create a `private` method `void createController()`and initialize `snake_controller` inside it
3. Call all lifecycle methods of `snake_controller`
4. Create `private void destroy()`, delete `snake_controller` inside it, and call this function inside the destructor
5. Create a `public` empty method `void spawnPlayer()`



## [IN **LevelService**]

1. Create an empty `private` method `void spawnPlayer()` and call it from `createLevel()`
2. Call `PlayerService`'s `spawnPlayer()` from `LevelService`'s `spawnPlayer()`



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
