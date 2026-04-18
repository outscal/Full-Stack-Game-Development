Right now you have a perfectly placed cell with perfect texture. All you need to do is, create many more cells and the game is good to play.

But how many cells can you place? What will be the grid size?

9x9? 20x20? 32x32?

But, currently, we have just hardcoded a value, which makes the board static(only suitable for a 9x9 board).

In this lesson, you'll calculate the size of the cell dynamically for different grid sizes.



# Calculating Cell Size


---



How can you calculate the size of the cell dynamically?🤔

So the size of a cell can be calculated based on the number of cells there are going to be.

Here is an example of different sizes of cells being drawn for different numbers of rows and columns:



![ ](//outscal.github.io/Full-Stack-Game-Development/images/9d2dea5c80323a6b.png)

**Multiple Grid Sizes**



**To calculate the size of a cell:**

Size calculation will be done in `Board` class

*Width of 1 cell = Width of board/number of columns*

*Height of 1 cell = Height of board/number of rows*



**Factors that affect Cell Size:**

1. Board Width and Height
2. Number of rows and columns

You have the board's width and height in `Board.h`: `boardWidth`, `boardHeight`

But, you need to declare the number of rows and columns in the `Board.h` file:



`Board.h`

```cpp
private:
// Board Constants
static const int numberOfRows = 9;
static const int numberOfColumns = 9;

```



Now, you can simply divide these values by the number of rows or columns you need on the board.

But!

Before starting to calculate, we have to subtract *"*`*horizontalCellPadding*`*"* and *"*`*verticalCellPadding*`*"* from the board size.



**What is** `horizontalCellPadding`**and** `verticalCellPadding`**?**

- This is the extra space (marked in *red*) on the board as shown below:



![ ](//outscal.github.io/Full-Stack-Game-Development/images/df3f325575ac74e5.png)

**Highlighted Extra Space**



After subtracting this extra area, we'll get the playable area's width and height.

Here are the offsets for extra width and height,
declare them in `Board.h` file:

`Board.h`

```cpp
private:
const float horizontalCellPadding = 115.f;
const float verticalCellPadding = 329.f;
```



Now, you'll need helper functions to calculate both the width and height of the cell.



`Board.h`

> **Summary📃**
> Here's what has been added to the Board class:

> 🔸Helper functions for calculating the cell's width and height



```cpp
private:
//previous code

float getCellWidthInBoard() const;
float getCellHeightInBoard() const;

```





Here's how you can calculate the height and width of the cell:

`Board.cpp`

```cpp
float Board::getCellWidthInBoard() const
{
    return (boardWidth - horizontalCellPadding) / numberOfColumns;
}

float Board::getCellHeightInBoard() const
{
    return (boardHeight - verticalCellPadding) / numberOfRows;
}

```



> **TODO: **
> In `**Board.cpp**` 
> ✅Implement `float getCellWidthInBoard()` and `float getCellHeightInBoard()`



You have successfully written the logic to calculate the cell size dynamically!💪🏼

Now, you just need to call the helper functions to set the cell size, instead of hardcoding the value!



# Setting Cell Size


---



Where did you set the size of the cell?🤔

In the `Cell`'s constructor!

And it’s getting called in the `Board::createBoard()` function!

So, you just need to pass the dynamic cell size instead of hardcoding 83.



> **PROTIP💡** 
> Don’t pass the function calls directly as the parameters. Create local variables in the `createBoard()` function and then pass the cell size. It’s a good practice!



> **TODO:** 
> In `Board::createBoard()` function: 
> ✅Create `float cell_width` and `float cell_height` 
> ✅Use the `getCellWidthInBoard()` and `getCellHeightInBoard()` functions to the values of `float cell_width` and `float cell_height` 
> ✅Pass `cell_width` and `cell_height` as the parameters of the `Cell`’s constructor.
> ✅Change the `numberOfRows` and `numberOfColumns` to test dynamic size changing.



Click here to see the solution.

`Board.cpp`

```cpp
 void Board::createBoard()
    {
        float cell_width = getCellWidthInBoard();
        float cell_height = getCellHeightInBoard();
        cell = new Cell(cell_width, cell_height, sf::Vector2i(0, 0));
    }
```





There's one last thing to address.'

The `position` variable of the `Cell` class is not being used currently. 

But keep it as it is, because it'll be used in future content.

`Cell.cpp`

```cpp
void Cell::initialize(float width, float height, sf::Vector2i position)
{
    this->position = position; // will be used in the future content
    sf::Vector2f cellScreenPosition = getCellScreenPosition(width, height);
    cell_button = new Button(cell_texture_path, cellScreenPosition, width * slice_count, height);
}
```



In the next lesson, we'll discuss an approach to creating the rest of the cells.

**See you in the next lesson👋**
