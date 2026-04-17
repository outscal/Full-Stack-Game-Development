# **TASKS**


---



## IMPLEMENTING BODY COLLISION


---



## [IN **Single Linked List**]

1. Create `bool SingleLinkedList::processNodeCollision()`  
2. Inside it, compare each node's next position with the head's next position; if they are the same, return true. Else, return false.
  Remember: There is no need to do anything if `head_node` is `nullptr` 



## [IN **Snake Controller**]

1. Inside `processSnakeCollision()`, check for collision using `single_linked_list->processNodeCollision()`  and if true, set the `current_snake_state` to `DEAD` 
2. Inside `delayedUpdate()`, after calling `processSnakeCollision()` check if the Snake is `ALIVE` and then only call `moveSnake()` 



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
