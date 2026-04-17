# Initial Instructions


---

- Make sure you are in the `Feature-8_Score-System` branch in your git repo.
- Make changes for this assignment (Add new commits) on this branch.
- Create a `Pull Request`, from this feature branch `Feature-8_Score-System` to the previous branch `main` if not already created.
- If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.
- Since, this is a guided assignment, code reviews will not happen, instead the solution code is present in the content.
- But, before checking the solution code, try your best to solve it independently.



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



## Set Up Scoreboard


---

## [TASKS]

1. In `Header/UI` create the `UIService.h` file. 
2. In `Source/UI` create the `UIService.cpp` file. 
3. Setup the properties for `left_score` and `right_score`.



## Creating Scoreboard


---

`UIService.cpp`

## [Tasks]

1. Implement `loadFontTexture()` 
2. Implement `void createLeftScoreText()` and `void createRightScoreText()` functions 
3. Call these functions in the `UIService()` constructor.



## Show the Score


---

## [tasks]

1. In `UIService.cpp` implement the functions to render the score. 
2. Call `ui_service->render(game_window);` in `GameplayManager::render()`



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
