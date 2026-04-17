# **TASKS**


---



## IMPLEMENT PROCESS QUICK SORT


---



## [IN MAINMENUUICONTROLLER.CPP]

1. Uncomment the button bindings for Radix Sort



## [IN STICKCOLLECTIONCONTROLLER]

1. Create an empty private method `void processRadixSort()` 
2. Create a case for `RADIX_SORT` and call the `processRadixSort` inside the `sortElements()` method





## IMPLEMENT count sort


---

**TODO: **Implement the `countSort()` function to sort elements based on their digits at a specified exponent position.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare and implement a private method `void updateStickPosition(int i)` that updates only the `stick[i]` position.
2. Declare a private method `void countSort(int exponent)`.
3. Inside `countSort()`:
4. - Get an instance of `SoundService` to play `COMPARE_SFX` when comparing a pair of sticks.
  - Create `output` vector to store sorted sticks.
  - Create `count` vector initialized to zeros for counting digit occurrences.
  - Counting Digits:
  - - Iterate through each stick in the `sticks` array.
    - Calculate the digit position using `(sticks[i]->data / exponent) % 10`.
    - Increment the count of the corresponding digit in the `count` array.
    - Play a comparison sound effect, update array access count, and visualize processing color for the current stick.
  - Accumulate Counts:
  - - Adjust the `count` array so that each element at index `i` contains the cumulative count of digits less than or equal to `i`.
  - Sorting Based on Digit:
  - - Iterate backwards through the `sticks` array (from end to start).
    - Calculate the `digit` position using `(sticks[i]->data / exponent) % 10`.
    - Place the stick into the `output` array based on its digit position adjusted by `count`.
    - Set the colour of the stick to `temporary_processing_color` and decrement the count of the corresponding `digit`.
    - Increment counters for array accesses.
  - Place Sorted Elements:
  - - Copy elements from `output` back to `sticks` to finalize the sorting order.
    - Set the colour of the stick to `placement_position_element_color` 
    - Update the position of each stick using `updateStickPosition(i)` and introduce a delay for observation.





## IMPLEMENT Radix SORT


---

**TODO: **Implement the `radixSort()` function, which iteratively sorts an array using `countSort()`.



## [IN STICKCOLLECTIONCONTROLLER]

1. Declare a private method `void radixSort()` 
2. Inside `radixSort()`:
3. - Initialize `maxElement` to the minimum possible integer value (`INT_MIN`)
  - Iterate through the `sticks` array to find the maximum value (`maxElement`) among all stick data.
  - Perform Radix Sort Iteratively:
  - - Initialize `exponent` to `1` and continue sorting by increasing digit places (`exponent` represents powers of `10`) until all digits of `maxElement` are processed.
    - - `exponent = 1; maxElement / exponent > 0; exponent *= 10`
    - Call `countSort(exponent)` for each `exponent`.



## [IN STICKCOLLECTIONCONTROLLER]

1. Inside `processRadixSort()` make a call to `radixSort()`.



## DRAMATIC END EFFECT


---

## [IN STICKCOLLECTIONCONTROLLER]

1. Call `setCompletedColor()` at the end of `processRadixSort()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-6-Radix-Sort**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-6-Radix-Sort**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
