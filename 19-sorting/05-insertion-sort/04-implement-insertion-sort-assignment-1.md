# **TASKS**


---



## IMPLEMENT Insertion SORT


---



## [IN MAINMENUUICONTROLLER.CPP]

1. Uncomment the button bindings for Insertion Sort



## [IN STICKCOLLECTIONCONTROLLER]

1. Create an empty private method `void processInsertionSort()` 
2. Create a case for `INSERTION_SORT` and call the `processInsertionSort` inside the `sortElements()` method



## [IN STICKCOLLECTIONCONTROLLER]

1. Inside `processInsertionSort()`:
2. 1. Get an instance of `SoundService` to play `COMPARE_SFX` when comparing a pair of sticks.
  2. **Outer Loop**: Loop through the sticks starting from the second element (`i = 1`).
  3. Inside the outer loop, 
  4. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
    - Set `j` to `i - 1` and assign the current stick (`sticks[i]`) to `key`.
    - Increment the array access counter for accessing the `key` stick.
    - Set the colour of the `key` stick to `processing_element_color`.
    - Pause execution for `current_operation_delay`.
  5. **Inner Loop**: While `j` is non-negative and the data of `sticks[j]` is greater than the `key`'s data:
  6. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
    - Increment the counters for the number of array accesses and comparisons. 
    - Move `sticks[j]` to `sticks[j + 1]`.
    - Set the colour of `sticks[j + 1]` to `processing_element_color` to mark it as being compared.
    - Play the comparison sound effect and update stick positions to visualize the current state.
    - Pause the execution for `current_operation_delay` using thread sleep.
    - Set the colour of `sticks[j + 1]` to `selected_element_color` to indicate it has been compared.
    - Decrement `j`.
  7. Insert the `key` stick in its correct position (`sticks[j + 1]`) and increment the array access.
  8. Set the colour of the stick to `temporary_processing_color` indicating it's sorted and plays a sound.
  9. Update the stick positions and pause for visuals.



## DRAMATIC END EFFECT


---

## [IN STICKCOLLECTIONCONTROLLER]

1. Call `setCompletedColor()` at the end of `processInsertionSort()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Insertion-Sort**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Insertion-Sort**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
