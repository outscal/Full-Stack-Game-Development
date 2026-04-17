# **Tasks**


---



## updating **SnakeController**


---

## [IN **SnakeController**]



1. Create a new property `LinkedList* linked_list` and delete the old `single_linked_list` 
2. Modify the `createLinkedList()` function and create a switch case, which will create a Linked List according to user input.
3. Remove `createLinkedList()` call from the constructor
4. Replace all instances of using `single_linked_list`  with `linked_list` 
5. Create `void SnakeController::initializeLinkedList()` and move all the functionality of initializing the Linked List from `initialize()` to `initializeLinkedList()` 
6. Call `initializeLinkedList()` at the end of `createLinkedList()`



## updating PLAYER SERVICE


---

## [IN PLAYERSERVICE]



1. Update `spawnPlayer()` & inside it:
2. 1. Call `SnakeController`'s `createLinkedList(level_type)`
  2. Then, call `SnakeController`'s `spawnSnake()`



## updating LEVEL SERVICE


---

## [IN LEVELSERVICE]



1. Create a property: `LinkedListType current_linked_list_type` 
2. Create `void LevelService::setCurrentLevelNumber(LevelNumber level_to_load)` and inside it, set `current_level = level_to_load`.
3. Modify `createLevel()` to take `LinkedListTypelinked_list_type` and inside it, set `current_linked_list_type = linked_list_type` and call the rest of the functions required for the game.



## updating LEVEL SELECTION UI CONTROLLER


---

## [IN LevelSelectionUIController]



1. Update the level button callback functions for both Level 1 and 2 to change the `GameState` to  `LINKED_LIST_SELECTION` and instead of calling `LevelService::createLevel()`call `LevelService::setCurrentLevelNumber()` 



## updating LINKED LIST SELECTION UI CONTROLLER


---

## [IN LinkedListSelectionUIController]



1. Create and implement `singleLinkedListButtonCallback()` and `doubleLinkedListButtonCallback()`
2. Implement logic for all callback buttons and set the `GameState` to `GAMEPLAY` and call `createLevel()` passing the player input for the Linked List Type.





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-5-Doubly-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-5-Doubly-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
