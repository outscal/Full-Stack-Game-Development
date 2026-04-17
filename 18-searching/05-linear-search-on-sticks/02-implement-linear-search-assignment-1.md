# **TASKS**


---

## IMPLEMENTING LINEAR SEARCH


---



## [IN GAMEPLAYSERVICE.CPP]

1. Implement `initializeRandomSeed()` to set the random seed using `std::srand(std::time(nullptr))`.
2. Call `initializeRandomSeed()` in `void GameplayService::initialize()` to ensure consistent random number generation.



## [IN SOUNDSERVICE.H]

1.  Define a sound type for comparison as `COMPARE_SFX` in `enum class SoundType` 
2.  Make sure you create a buffer for the new sound.



## [IN SOUNDSERVICE.CPP]

1. Include** **`Config.h`.
2. Load the comparison sound effect upon initialization.
3. Play the sound based on `SoundType` 



## [IN STICKCOLLECTIONCONTROLLER.CPP]

1. Add following properties:
           `int number_of_comparisons`
           `int number_of_array_access`
2. Create and Implement `getNumberOfComparisons()` & `getNumberOfArrayAccess()` methods.
3. Declare and Implement the following methods:
4. 1. `void shuffleSticks()`
  2. `void resetSearchStick()`
  3. `void resetVariables()`
5. Call all these functions within the `reset` function.
6. Implement `processLinearSearch()` function as well.
7. Call the `playSound()` function to play the comparison sound within the `processLinearSearch` loop.





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Linear-Search**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Linear-Search**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
