# **Tasks**


---



## CREATING shift Nodes After Removal


---

## [in SingleLinkedList]



**TODO: Implement a method to handle shifting the linked list towards the front after a node is removed. **



1. Create a method `void shiftNodesAfterRemoval(Node* cur_node)` 
2. Fetch and copy `cur_node`'s position and direction.
3. Then shift the `cur_node` to its next node.
4. Then traverse from `cur_node` till the end to update the positions of the nodes to their previous node's position and direction.



## CREATING remove node at INDEX


---

## [in SingleLinkedList]



**TODO: Implement a method to remove a node at a given index in the linked list and update (shift) the list structure accordingly.**



1. Create a method `void removeNodeAtIndex(int index)` 
2. Traverse the list until reaching the node at the specified index.
3. Handle removing the specified node from the list and update the list structure.
4. Then delete the specified node.



## CREATING remove Node At


---

## [in SingleLinkedList]



1. Create a method `void removeNodeAt(int index)` 
2. Check if the index is valid or not
3. Make the call to remove according to the index. (You can refer to `insertNodeAt()`)



## CREATING remove Node At middle


---

## [in SingleLinkedList]



1. Create a method `void removeNodeAtMiddle()` 
2. Check if the list is empty or not.
3. Fetch and copy the middle index. Then call `removeNodeAt()`. (You can refer to `insertNodeAtMiddle()`)





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Linked-List-Operations**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Linked-List-Operations**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
