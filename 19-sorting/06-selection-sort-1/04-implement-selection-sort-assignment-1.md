# **TASKS**


---



## IMPLEMENT Selection SORT


---



## [IN MAINMENUUICONTROLLER.CPP]

1. Uncomment the button bindings for Selection Sort



## [IN STICKCOLLECTIONCONTROLLER]

1. Create an empty private method `void processSelectionSort()` 
2. Create a case for `SELECTION_SORT` and call the `processSelectionSort` inside the `sortElements()` method



## [IN STICKCOLLECTIONCONTROLLER]

1. Inside `processInsertionSort()`:
2. 1. Get an instance of `SoundService` to play `COMPARE_SFX` when comparing a pair of sticks.
  2. **Outer Loop**: Loop through the sticks starting from the first element to the second last element.
  3. Inside the outer loop, 
  4. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
    - Set `min_index` to `i`.
    - Set the colour of the current element (`sticks[i]`) to `selected_element_color`.
  5. **Inner Loop**: Loop through the sticks from `i+1` to the last element.
  6. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
    - Increment the counters for the number of array accesses and comparisons. 
    - Play the comparison sound effect and set the colour of the current element (`sticks[j]`) to `processing_element_color`.
    - Pause execution for `current_operation_delay`.
    - If `sticks[j]` data is less than `sticks[min_index]` data:
    - - Reset the colour of the `min_index` element to `element_color`.
      - Update `min_index` to `j`.
      - Set the colour of new `min_index` element to `temporary_processing_color`.
    - Else: Reset the colour of the current element to `element_color`.
  7. After the inner loop, swap the `min_index` element with the current element (`sticks[i]`).
  8. Increment the array access counter for the swap.
  9. Set the colour of the sorted element (`sticks[i]`) to `placement_position_element_color`.
  10. Update stick positions to visualize the current state.
  11. After the outer loop, ensure the last element is marked as sorted by setting its colour to `placement_position_element_color`.



## DRAMATIC END EFFECT


---

## [IN STICKCOLLECTIONCONTROLLER]

1. Call `setCompletedColor()` at the end of `processSelectionSort()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-3-Selection-Sort**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-3-Selection-Sort**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
