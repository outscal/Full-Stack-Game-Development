# **TASKS**


---

## Rendering A COLLECTION OF STICKS


---



## [in stickcollectioncontroller.h]



1. Declare the method `void initializeSticksArray()` 



## [IN STICKCOLLECTIONCONTROLLER.CPP]

1.  Implement these methods:- 

- - `initializeSticks()`
  - `calculateStickWidth()`
  - `calculateStickHeight()`
  - `updateSticksPosition()`



1. Implement the `void initializeSticksArray()` method to initialize sticks based on the number of elements in the collection model as :

-> Iterate through `collection_model->number_of_elements`.

-> Create a new `Stick` object for each iteration.

-> Add each `Stick` object to the `sticks` vector.

1. Call  `initializeSticksArray()` within the constructor of `StickCollectionContoller`





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Linear-Search**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Linear-Search**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
