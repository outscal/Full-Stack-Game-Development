# Initial Instructions


---

- Make sure you are in the  `Feature-2_Cell`  branch in your git repo.
- Make changes mentioned in the assignment (Add new commits) on this branch.
- Create a `Pull Request`, from this feature branch `Feature-2_Cell` to the previous branch `main` if not already created.
- If you had created a PR previously, no need to create again, simply commit your changes, and that PR will be updated.
- Since this is a guided assignment, code reviews will not happen, instead, the solution code is present at the end of the chapter.
- But, before checking the solution code, try your best to solve it independently.



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution[ ](https://github.com/outscal/Arrays/tree/Feature-2_Cell/Array-Minesweeper)before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!
> Cross-check your code with the content.
> If you're still blocked then:

> Clear your doubts [**here**](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



## Create Button Class


---

## [tasks]

1. In `header/UI/UIElements/Button/` implement the `Button.h` file. 
2. In `source/UI/UIElements/Button/` implement the `Button.cpp` file.



## Create Cell


---

## [tasks]

1.  In `header/GameLoop/Gameplay/` create and implement the `Cell.h` file. 
2. In `source/GameLoop/Gameplay/` create the `Cell.cpp` file.
3. In `Cell.cpp` file:
4. 1. Implement the `initialize` and `render` methods. 
5. In `Board.h` 
6. 1. Create a pointer object(`cell`) of the `Cell` class
  2. Declare a `createBoard` function.
7. In `Board.cpp`
8. 1. Call the `createBoard` function in the `initialize` function.
  2. Initialize the cell object in the `createBoard` function.
  3. In the `render` function call the `render` function of the `Cell` class.

# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
