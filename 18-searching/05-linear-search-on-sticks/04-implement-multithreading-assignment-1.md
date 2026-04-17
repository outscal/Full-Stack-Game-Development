# **TASKS**


---

## DELAY ADDITION


---



## [IN STICKCOLLECTIONCONTROLLER.H]

1.  Declare a variable for `current_operation_delay`
2. Also declare the corresponding getter `getDelayMilliseconds()` method for it.
3. Set `current_operation_delay = 0` in `reset()`



## [IN STICKCOLLECTIONCONTROLLER.CPP]

1. Set `current_operation_delay` as `linear_search_delay` in `LINEAR_SEARCH` case in `searchElement()`



## THREAD IMPLEMENTATION


---

## [IN STICKCOLLECTIONCONTEOLLER.H]

1. Add the <thread> include.
2. Declare `search_thread` as `private` std::thread in class `StickCollectionController`
3. Declare `joinThreads()` as private void in class `StickCollectionController`



## [IN STICKCOLLECTIONCONTROLLER.CPP]

1. Implement the `search thread `which is mainly to initiate the search operation.
2. Implement the `join thread`.
3. Implement the `processLinearSearch()` for the search operation.





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Linear-Search**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Linear-Search**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
