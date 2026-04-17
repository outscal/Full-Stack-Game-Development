# **TASKS**


---



## Process Player input


---



## [IN Snake Controller]

1. Inside `processPlayerInput()`, use `EventService` to check for Key Presses and update the `current_snake_direction`
2. Call it inside `update()` before calling `moveSnake()` 



## UPDATING EACH BODY PART


---



## [IN **Single LinkedList**]

1. Create `void SingleLinkedList::updateNodeDirection(Direction direction_to_set)`: Inside it, write the logic such that the HEAD node updates with the direction of input, i.e. `direction_to_set` and the rest nodes are updated with the direction of the node ahead of them 
2. Create `void SingleLinkedList::updateNodePosition()`: Inside it, write the logic to traverse through all nodes and call `updatePosition()` of each `BodyPart` 



## **MOVING IN SNAKE CONTROLLER**


---



## [IN Snake Controller]

1. Call `SingleLinkedList`'s `updateNodeDirection()` inside `SnakeController::updateSnakeDirection()` and pass `current_node_direction`  as an argument
2. Call `SingleLinkedList`'s `updateNodePosition()` inside `SnakeController::moveSnake()`  



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
