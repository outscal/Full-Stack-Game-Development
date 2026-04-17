# **TASKS**


---



## IMPLEMENT process Merge SORT


---



## [IN STICKCOLLECTIONCONTROLLER]

1. Create an empty private method `void processMergeSort()` 
2. Update the case for `MERGE_SORT`, change the name from `processInPlaceMergeSort` to `processMergeSort` inside the `sortElements()` method





## implement merge


---

**TODO: **Implement the `merge()` function that merges two sorted halves of an array back into a single sorted array.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare a private method `void merge(int left, int mid, int right)`
2. Inside `merge()`:
3. - Get an instance of `SoundService` to play `COMPARE_SFX` when comparing a pair of sticks.
  - Create a `temp` array to store elements from the left to the right indices, the size of the vector = `right - left + 1`.
  - Initialize variables: `i` for the first half, `j` for the second half, and `k` for the merged array.
    `i = 0; // Start of the first half in temp`
    `j = mid - left + 1; // Start of the second half in temp`
    `k = left; // Start position in the original array to merge back`
  - Copy elements from the `sticks` array to the `temp` array.
  - Set the colour of elements to `temporary_processing_color`.
  - Merging Elements Back:
  - - In the while loop, compare elements from the two halves of the `temp` array.
    - If `temp[i]` is smaller or equal to `temp[j]`, place `temp[i]` in `sticks` array and increment `i` and `k`.
    - Otherwise, place `temp[j]` in `sticks` array and increment `j` and `k`.
    - During merging, play a sound and set the colour of the stick being processed to `processing_element_color`.
    - After each comparison and assignment, update stick positions and wait for `current_operation_delay`.
  - Handling Remaining Elements:
  - - After one of the halves is exhausted, copy the remaining elements from the other half.
    - Visual and audio updates will remain the same.



## implement merge sort


---

**TODO: **Implement the `mergeSort()` function, which recursively sorts an array using `merge()`.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare a private method `void mergeSort(int left, int right)` 
2. Inside `mergeSort()`:
3. - Check for base case:
  - - If the `left` index is greater than or equal to the `right` index, `return`. This means the array is already sorted or has only one element.
  - Calculate the midpoint of the array to split it into two halves.
  - - `mid = left + (right - left) / 2`
  - Recursively call `mergeSort` on the left half of the array.
  - Recursively call `mergeSort` on the right half of the array.
  - After both halves are sorted, merge them back together using the `merge` function.



## [IN STICKCOLLECTIONCONTROLLER]

1. Inside `processMergeSort()` make an initial call where `left` is `0` and `right` is `size - 1` to `mergeSort()`.



## DRAMATIC END EFFECT


---

## [IN STICKCOLLECTIONCONTROLLER]

1. Call `setCompletedColor()` at the end of `processMergeSort()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Merge-Sort**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Merge-Sort**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
