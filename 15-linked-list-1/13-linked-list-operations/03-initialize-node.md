# **TASKS**


---



## Initialize node


---



## [IN SingleLinkedList]

1. Create an `enum class Operation` and fill it with `{HEAD,MID,TAIL}`
2. Create `sf::Vector2i SingleLinkedList::getNewNodePosition(Node* reference_node, Operation operation)` such that it returns Node's next position when Operation is at `HEAD` and returns Node's previous position when Operation is at `TAIL`. Ignore `MID` and return `default_position` as default
3. Replace all uses of the old `**getNewNodePosition()**` with this new function and delete the old function



## [IN SingleLinkedList]

1. Create and implement `void SingleLinkedList::initializeNode(Node* new_node, Node* reference_node, Operation operation)` & inside it:
2. 1. Call `getNewNodePosition(reference_node, operation) `to fetch and store new node position.
  2. Initialize new node `body_part`.



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Linked-List-Operations**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Linked-List-Operations**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
