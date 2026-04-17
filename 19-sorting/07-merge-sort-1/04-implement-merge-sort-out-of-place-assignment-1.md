# **TASKS**


---



## IMPLEMENT PROCESS MERGE SORT


---



## [IN MAINMENUUICONTROLLER.CPP]

1. Uncomment the button bindings for Merge Sort



## [IN STICKCOLLECTIONCONTROLLER]

1. Create an empty private method `void processInPlaceMergeSort()` 
2. Create a case for `MERGE_SORT` and call the `processInPlaceMergeSort` inside the `sortElements()` method





## IMPLEMENT MERGE


---

**TODO: **Implement the `inPlaceMerge()` function that merges two sorted halves of an array back into a single sorted array.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare a private method `void inPlaceMerge(int left, int mid, int right)`
2. Inside `inPlaceMerge()`:
3. - Get an instance of `SoundService` to play `COMPARE_SFX` when comparing a pair of sticks.
  - Set `start2` to `mid + 1`.
  - Compare the data at `mid` and `start2`. If the direct merge is already sorted (i.e., `sticks[mid]->data <= sticks[start2]->data`).
  - - Increment comparison and array access counters.
    - Return immediately.
  - Merge Process with Two Pointers:
  - - Use two pointers (`left` and `start2`) to maintain the start of both arrays to merge.
    - Continue merging while `left` is less than or equal to `mid` and `start2` is less than or equal to `right`.
    - Increment comparison and array access counters.
    - Compare and Shift Elements:
    - - If `sticks[left]->data` is less than or equal to `sticks[start2]->data`, increment `left`.
      - Else:
      - - Store `sticks[start2]` in a temporary variable `value`.
        - Shift all elements between `left` and `start2` to the right by one position.
        - Place `value` at `left`.
        - Increment array access counters.
        - Increment `left`, `mid`, and `start2` to update their positions after insertion.
      - Call `updateStickPosition()` to update the visual positions of the sticks.
  - Play the comparison sound effect and set the colour of the current element (`sticks[left - 1]`) to `processing_element_color`.
  - Pause execution for `current_operation_delay`.
  - Reset the colour of the current element to `element_color`.



## IMPLEMENT MERGE SORT


---

**TODO: **Implement the `inPlaceMergeSort()` function, which recursively sorts an array using `merge()`.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare a private method `void inPlaceMergeSort(int left, int right)` 
2. Inside `inPlaceMergeSort()`:
3. - Check for base case:
  - - If the `left` index is greater than or equal to the `right` index, `return`. This means the array is already sorted or has only one element.
  - Calculate the midpoint of the array to split it into two halves.
  - - `mid = left + (right - left) / 2`
  - Recursively call `mergeSort` on the left half of the array.
  - Recursively call `mergeSort` on the right half of the array.
  - After both halves are sorted, merge them back together using the `inPlaceMerge` function.



## [IN STICKCOLLECTIONCONTROLLER]

1. Inside `processInPlaceMergeSort()` make an initial call where `left` is `0` and `right` is `size - 1` to `inPlaceMergeSort()`.



## DRAMATIC END EFFECT


---

## [IN STICKCOLLECTIONCONTROLLER]

1. Call `setCompletedColor()` at the end of `processInPlaceMergeSort()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Merge-Sort**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Merge-Sort**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
