# **TASKS**


---



## IMPLEMENT PROCESS QUICK SORT


---



## [IN MAINMENUUICONTROLLER.CPP]

1. Uncomment the button bindings for Quick Sort



## [IN STICKCOLLECTIONCONTROLLER]

1. Create an empty private method `void processQuickSort()` 
2. Create a case for `QUICK_SORT` and call the `processQuickSort` inside the `sortElements()` method





## IMPLEMENT PARTITIOn


---

**TODO: **Implement the `partition()` function to rearrange the array with elements less than the pivot on the left and greater on the right.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare a private method `int partition(int left, int right)`
2. Inside `partition()`:
3. - Get an instance of `SoundService` to play `COMPARE_SFX` when comparing a pair of sticks.
  - Set the pivot element (`sticks[right]`) colour to `selected_element_color`
  - Initialize the `i` index to `left - 1`
  - Loop through the `sticks` array from `left` to `right - 1`.
  - Set the colour of current element to `processing_element_color`.
  - Increment counters for array accesses and comparisons.
  - Swap Elements if Needed:
  - - If the current element is less than the pivot, increment `i` and swap the elements at `i` and `j` using the `std::swap()` function.
    - Update the stick positions, play a sound effect, and introduce a delay for visualization.
    - Increment counters for array accesses.
    - Else: Reset the colour of the current element to `element_color`.
  - Place Pivot in Correct Position:
  - - Swap the pivot element with the element at `i + 1` using the `std::swap()` function.
    - Update the stick positions and increment the array access counter.
    - Return the index `i + 1`, which is the final position of the pivot.





## IMPLEMENT Quick SORT


---

**TODO: **Implement the `quickSort()` function, which recursively sorts an array using `partition()`.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare a private method `void quickSort(int left, int right)` 
2. Inside `quickSort()`:
3. - Check for base case:
  - - If the `left` index is greater than or equal to the `right` index, `return`. This means the array is already sorted or has only one element.
  - Use the `partition` function to determine the pivot index.
  - - `pivot_index = partition(left, right)`
  - Recursively call `quickSort` on the left partition.
  - Recursively call `quickSort` on the right partition.
  - After sorting each segment, set the elements' colour to `placement_position_element_color`.



## [IN STICKCOLLECTIONCONTROLLER]

1. Inside `processQuickSort()` make an initial call where `left` is `0` and `right` is `size - 1` to `quickSort()`.



## DRAMATIC END EFFECT


---

## [IN STICKCOLLECTIONCONTROLLER]

1. Call `setCompletedColor()` at the end of `processQuickSort()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-5-Quick-Sort**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-5-Quick-Sort**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
