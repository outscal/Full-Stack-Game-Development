# **TASKS**


---



## Resetting the snake


---



## [IN **Snake Controller**]

1. Create 		`const float restart_duration = 2.f` 
2. Create and implement `void SnakeController::reset()` 
  Inside it, reset the following properties:

> `current_snake_state`
> `current_snake_direction`
> `elapsed_duration`
> `restart_counter`





## RESPAWNING THE SNAKE


---



## [IN **Snake Controller**]

1. Create and implement `void SnakeController::respawn()` 





## HANDLING RESTART TIMER


---



## [IN **Snake Controller**]

1. Create and implement `void SnakeController::handleRestart()` 
2. Call it inside `update()` when Snake is `DEAD`



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
