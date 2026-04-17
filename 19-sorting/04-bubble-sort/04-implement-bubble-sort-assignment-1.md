# **TASKS**


---



## Implement bubble sort


---



## [IN MainMenuUIController.cpp]

1. Uncomment the button bindings for Bubble Sort



## [IN StickCollectionController]

1. Create an empty private method `void processBubbleSort()` 
2. Uncomment the switch case for the `processBubbleSort` inside the `sortElements()` method



## [IN StickCollectionModel]

1. Add `enum class SortState` which consists:

> `SORTING`
>  `NOT_SORTING`





## [IN StickCollectionController]

1. Add a property `SortState sort_state` 
2. Set `sort_state = SortState::SORTING` in `sortElements()`
3. Set `sort_state = SortState::NOT_SORTING` in `initialize()`, `processSortThreadState()` & `reset()`.
4. Inside `processBubbleSort()`:
5. 1. Get an instance of `SoundService` to play `COMPARE_SFX` when comparing a pair of sticks.
  2. **Outer Loop**: Loop through the entire collection of sticks.
  3. Inside the outer loop, 
  4. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
    - Create a `bool` variable `swapped` to track if any swaps are made during a pass.
  5. **Inner Loop**: Loop through the sticks from the beginning to the last unsorted stick.
  6. - Break the inner loop if `sort_state` is `SortState::NOT_SORTING`.
    - Increment the counters for the number of array accesses and comparisons. Play `COMPARE_SFX`.
    - Set the colour of the two sticks being compared to `processing_element_color`.
    - Compare the data of the two sticks. If the previous stick's data is greater than the current stick's data, swap the two sticks using the `std::swap()` function. 
      Set `swapped` to `true` if a swap occurs.
    - Pause the execution for `current_operation_delay` using thread sleep.
    - Revert the colour of the two sticks back to the default `element_color`
    - Call `updateStickPosition()` method to update the positions of the sticks.
  7. Set the colour of the last sorted stick to `placement_position_element_color`
  8. If no swaps were made during a pass, the array is already sorted. Break out of the loop.



## DRAMATIC End EFFECT


---

## [IN StickCollectionModel]

1. Add a property `const long initial_color_delay = 40` 



## [IN StickCollectionController]

1. Add a property `int color_delay` 
2. Inititalize `color_delay` in `sortElements()` 
3. Set `color_delay=0` in `reset()`
4. Declare and Implement `setCompletedColor()` and Inside it:
5. 1. Iterate through the `sticks` collection and set each stick's colour to `element_color`. 
  2. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
  3. Get the `SoundService` instance from the `ServiceLocator`.
  4. Iterate through the `sticks` collection again, playing the sound of `COMPARE_SFX` and changing the colour of each stick to `placement_position_element_color`. Introduce a delay to visualize the colour change.
  5. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
  6. Play a final sound `SCREAM` , if `sort_state` is `SortState::SORTING`, to indicate completion.
6. Call `setCompletedColor()` at the end of `processBubbleSort()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Bubble-Sort**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Bubble-Sort**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
