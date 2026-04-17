# **TASKS**


---



## Storing Previous Direction


---

## [IN **BodyPart**]



1. Create `Direction previous_direction` in `BodyPart.h` 
2. Create a getter function: `Direction getPreviousDirection()` 
3. Inside `setDirection()`, before updating `direction`, store the `direction` in `previous_direction` 





## REVERSE A LINKED LIST


---

## [IN SINGLELINKEDLIST]



1. Create `Direction SingleLinkedList::getReverseDirection(Direction reference_direction),` and inside it, return the opposite direction of `reference_direction` 
2. Create and implement `void SingleLinkedList::reverseNodeDirections()`, inside it, traverse through all `Node`s and for each `BodyPart`, take its `previous_direction`, reverse it using `getReverseDirection()` and set it as the new direction
3. Inside `reverse()`,  call `reverseNodeDirections()` and return `head_node->body_part.getDirection()` 



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Linked-List-Operations**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Linked-List-Operations**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
