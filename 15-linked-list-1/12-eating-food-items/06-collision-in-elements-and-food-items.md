# **TASKS**


---



## IMPLEMENTING COLLISION DETECTION WITH ELEMENTS


---



## [IN **Element Service**]

1. Create `bool ElementService::processElementsCollision(LinkedList::Node* head_node)` 
2. Inside it, check for collision of each obstacle with Snake's head. Return `true` when collided else, return `false` 





## USING ELEMENT COLLISION TO DETECT DEATH


---



## [IN **Snake Controller**]

1. Use `ElementService::processElementsCollision()` inside `SnakeController::processElementsCollision()` to detect collision. If a collision happens, change the state to `DEAD` and play the death sound



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Linked-List-Operations**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Linked-List-Operations**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
