# Initial Instructions


---

- Make sure you are in the  `Feature-2_Cell`  branch in your git repo.
- Make changes mentioned in the assignment (Add new commits) on this branch.
- Create a `Pull Request`, from this feature branch `Feature-2_Cell` to the previous branch `main` if not already created.
- If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.
- Since this is a guided assignment, code reviews will not happen, instead, the solution code is present in the assignment.
  [**Click Here To See The Solution Code**](https://github.com/outscal/Arrays/tree/Feature-2_Cell/Array-Minesweeper)
- But, before checking the solution code, try your best to solve it independently.



> 💡**PROTIP:**
> You can spoil yourself by looking at the [**solution** ](https://github.com/outscal/Arrays/tree/Feature-2_Cell/Array-Minesweeper)before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [**here**](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



## Calculate Cell Size


---

## [tasks]

1. In** **`**Board.h**`** **
  Create the offsets in the header file: `horizontalCellPadding`, `verticalCellPadding` 
2. In `**Board.cpp**` 
  Implement `float GetCellWidthInBoard()` and `float GetCellHeightInBoard()`, both will be `Private`



## Set Cell Size


---

## [tasks]

1. In `Board::createBoard()` function: 
2. Create `float cell_width` and `float cell_height` 
3. Use the `getCellWidthInBoard()` and `getCellHeightInBoard()` functions to the values of `float cell_width` and `float cell_height` 
4. Pass `cell_width` and `cell_height` as the parameters of the `Cell`’s constructor.
5. Change the `numberOfRows` and `numberOfColumns` to test dynamic size changing.

# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
