# **TASKS**


---



## food spawning in intervals


---



## [IN FoodService]

1. Create `enum FoodSpawningStatus` 
  `{ACTIVE, IN_ACTIVE}`
2. Create the following properties:
3. 1. `const float spawn_duration = 4.f;`
  2. `float elapsed_duration;`
  3. `FoodSpawningStatus current_spawning_status`
4. Inside `initialize()` method set `elapsed_duration` = `spawn_duration`
5.  Inside `reset()` method set `elapsed_duration = 0.f`
6. Create and implement a method `updateElapsedDuration()`.



## HANDLING FOOD SPAWNING


---



1. Create a method `handleFoodSpawning()` and inside it, when `elapsed_duration>= spawn_duration`:
2. 1. Call `destroyFood()` 
  2. Call `reset()`
  3. Call `spawnFood()`
3. Update `startFoodSpawning()` to set `current_spawning_status` to `ACTIVE` and not call `spawnFood()`
4. Create `stopFoodSpawning()` and inside it:
5. 1. Set `current_spawning_status` to `INACTIVE` 
  2. Call `destroyFood()`
  3. Call `reset()`
6. Update `update()`to call `updaeElapsedDuration()` & `handleFoodSpawning()` when `FoodSpawningStatus` is `ACTIVE`

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-3-Food-Spawning**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-3-Food-Spawning**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
