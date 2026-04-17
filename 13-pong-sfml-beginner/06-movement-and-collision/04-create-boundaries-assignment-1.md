# Initial Instructions


---

- Make sure you are in the `Feature-6_Movement-And-Collision`  branch in your git repo.
- Make changes for this assignment (Add new commits) on this branch.
- Create a `Pull Request`, from this feature branch `Feature-6_Movement-And-Collision` to the previous branch `main` if not already created.
- If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.
- Since, this is a guided assignment, code reviews will not happen, instead the solution code is present in the content.
- But, before checking the solution code, try your best to solve it independently.



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



## Create Boundaries


---

## [TASKS]

1. In `Source/Gameplay/Boundary/Boundary.cpp` implement the following methods:
  `createLeftBoundary()` , `createTopBoundary()`, `createBottomBoundary()`, and `createRightBoundary()`. 
2. Implement `createCenterLine()` for that classic Pong look.
3. In `Boundary()` constructor call the following methods:
  `createLeftBoundary()` , `createTopBoundary()`, `createBottomBoundary()`, and `createRightBoundary()`. 
4. In the `Boundary::render()` draw all the boundaries and the center line.



## Render BOundaries


---

## [Tasks]

1. In `GameplayManager.h` create pointer object of the `Boundary` class. 
2. In `GameplayManager.cpp` initialize the `boundary` object. 
3. In the `GameplayManager::render(RenderWindow* game_window)` call `boundary→render(game_window)`.



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
