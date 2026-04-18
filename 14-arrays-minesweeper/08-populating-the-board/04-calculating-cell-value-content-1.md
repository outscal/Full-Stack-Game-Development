You've placed mine randomly on our board.

But what about the non-mine cells? 🤔 

Every non-mine cell needs a value. 

This value will be either **empty** (when there are no adjacent mines) 
or 
a **number** (indicating how many mines are in the surrounding cells).



In this lesson, you'll implement the logic to calculate the values of the empty cells.



# How to Calculate Cell Values?


---

For each non-mine cell, we need to:

1. Check all eight surrounding cells
2. Count how many of these cells contain mines
3. Assign this count as the cell's value

How To Calculate Cell Values?🤔

1. First, identify if the current cell contains a mine. 
  If it does, skip to the next cell.
2. If it's not a mine, examine the eight adjacent cells:
3. - Top-left, top, top-right
  - Left, right
  - Bottom-left, bottom, bottom-right

The number of mines found in these adjacent cells becomes the value of the current cell.

One important consideration when implementing this algorithm is handling cells at the grid's edges. 

We must validate each adjacent cell position to ensure it exists within our board's boundaries.



Add these methods in `Board.h` to implement the above algorithm.

> **Summary📃**
> Here is list of thing that you need to add:
> 🔸Helper functions to:

> 🔹Count the mines around
> 🔹Populate cells with values
> 🔹Validate cell's postion



`Board.h`

```cpp
//previous code

namespace Gameplay
{
    class Board
    {
    private:
        //previous code
        int countMinesAround(sf::Vector2i cell_position);
        void populateCells();
        bool isValidCellPosition(sf::Vector2i cell_position);

        //previous code
        
    };
}
```





Now that you have added the functions, let's start with the implementation of the algorithm.



# Counting Mines Around


---

Let's implement the cell value calculation step by step:

First, you need a local variable to keep track of the mines around a cell :

`Board.cpp`

```cpp
int Board::countMinesAround(sf::Vector2i cell_position) {
		// local variable to keep track of cell value
    int mines_around = 0;
    
    // We'll add the counting logic here
}
```



Now, to implement the algorithm, you need to traverse the `cell` array. And for each non-mine cell, you also need to traverse its adjacent cells.

How do you traverse the adjacent cells? 🤔



## Iterating Adjacent Cells


---

Let's say we're checking the cell at position `**[3,4]**`.

To check its adjacent cells, we need to calculate their positions:



![ ](//outscal.github.io/Full-Stack-Game-Development/images/18aa0f06e2a9a573.png)





But how did we calculate these positions?🤔

You can calculate the position of the adjacent cells by adding 0,1 or -1 to the x and y coordinates of the current cell's position.

For example, assume the current cell's position as **[3,4]**:

Let's say **"a" **is the value added to the **x-coordinate** 
and **"b"** is the value added to the **y-coordinate**.

Then, this is how you can calculate the position of the Top row:

1. When **a = -1, b = -1**: `[3 + (-1), 4 + (-1)] = [2,3]` → **Top-left cell**
2. When **a = -1, b = 0**: `[3 + (-1), 4 + 0] = [2,4]` → **Top cell**
3. When **a = -1, b = 1**: `[3 + (-1), 4 + 1] = [2,5]` → **Top-right cell** and so on for all eight surrounding positions.

Here's how we can implement this using nested for loops:

- Traverse the 8 adjacent cells to the current cell.

`Board.cpp`

```cpp
int Board::countMinesAround(sf::Vector2i cell_position)
{
    int mines_around = 0;
		
		for (int a = -1; a <= 1; ++a) {
		    for (int b = -1; b <= 1; ++b) {
		        // Setting Cell Value
		    }
		}
}
```

**Note: **The two for loops will go from -1 to +1 for both ‘a’ and ‘b'



These loops will check all eight positions in this pattern:

**[C] = [0, 0]**

```txt
[-1,-1] [-1,0] [-1,1]
[0,-1]   [C]   [0,1]
[1,-1]  [1,0]  [1,1]
```

Now, you must validate that every adjacent cell exists in the `cell[][]` array.



## Validating Positions


---

Before checking each position, we need to:

1. Skip the current cell (when a=0 and b=0) as we need to count mines around the current cell.
2. Ensure the position is within the board's boundaries

`Board.cpp`

```cpp
int Board::countMinesAround(sf::Vector2i cell_position)
{
    int mines_around = 0;

		for (int a = -1; a <= 1; ++a) {
		    for (int b = -1; b <= 1; ++b) {
		        // Validate cell's postion and check current cell
		        if ((a == 0 && b == 0) || 
						!isValidCellPosition(sf::Vector2i(cell_position.x + a, cell_position.y + b)))
					    continue;
		    }
		}
}
```

**Note:** You’ll implement `isValidCellPosition()` after `countMinesAround()` function.

Now, if the conditions are not met, it means that the for loop is on an adjacent cell and it exists in the board.

We now just need to know if it is a Mine or not.

 

## Counting Mines


---

Finally, we check if the valid adjacent cell contains a mine:

- If it is a mine, increase `mines_around` by 1
- And return the mines_around.

`Board.cpp`

```cpp
int Board::countMinesAround(sf::Vector2i cell_position)
{
    int mines_around = 0;

		for (int a = -1; a <= 1; ++a) {
		    for (int b = -1; b <= 1; ++b) {
		        // Validate cell's postion and check current cell
		        if ((a == 0 && b == 0) || 
						!isValidCellPosition(sf::Vector2i(cell_position.x + a, cell_position.y + b)))
					    continue;
					    
	        //Check Mines
	        if (cell[cell_position.x + a][cell_position.y + b]->getCellType() == 
	        CellType::MINE)
					    mines_around++;
    			}
		}
		return mines_around;
}
```

Lastly, you need to implement the `isValidCellPosition` function as well:

This is quite straightforward, you just need to check if the cell is within the `cell` array's boundaries.

`Board.cpp`

```cpp
bool Board::isValidCellPosition(sf::Vector2i cell_position)
{
    return (cell_position.x >= 0 && cell_position.y >= 0 && 
        cell_position.x < numberOfColumns && cell_position.y < numberOfRows);
}
```



> **TODO:** 
> In `Board.cpp` 
> ✅ Implement the `countMinesAround(sf::Vector2i cell_position)` function. 
> ✅ Implement the `isValidCellPosition(sf::Vector2i cell_position)` function.
> ✅ Run the code to make sure there are no errors.



Now, you have the value for cells!

But, you still need to populate the cells with these values.



# Populating Cells with Values


---

Now that we can count mines around each cell, let's populate our board with the correct values! 🎯

How Does Cell Population Work?🤔

When populating cells, we need to:

1. Visit every cell on the board.
2. For a non-mine cell, count the mines around it.
3. Change the type of the cell according to the number of mines around it.

Use the `countMinesAround()` function for populating the cells.

It is quite easy, you can do it on your own 💪🏼



> **TODO:** 
> In `Board.cpp` 
> ✅ Implement `populateCells()` function. 
> ✅ In `populateBoard()` call `populateCells()` 
> ✅ Play the game.
> ✅ Set the cell’s state to `HIDDEN` in `Cell::initialize()`



> **PROTIP💡**
> Before setting the state to cell's state to HIDDEN, play the game to see the completely populated board!



Click here to see the solution.

`Board.cpp`

```cpp
void Board::populateBoard()
{
    populateMines();
    populateCells();
}

void Board::populateCells()
{
    for (int row = 0; row < numberOfRows; ++row)
        for (int col = 0; col < numberOfColumns; ++col)
            if (cell[row][col]->getCellType() != CellType::MINE)
            {
                int mines_around = countMinesAround(sf::Vector2i(row, col));
                cell[row][col]->setCellType(static_cast<CellType>(mines_around));
            }
}
```





Expected Output before hiding the Cells.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/106be5d989971dec.png)







Expected Output after hiding the Cells.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/1e236b3637c70b22.png)







Now, your Minesweeper board is fully initialized with both mines and numbered cells! 🎮

Every time you run the game, mines are placed in different cells, and the complete board changes!

Now, you need to make the cells clickable so that the players can open them.

You’ll do this in the next chapter!

**See you there!** 👋🏼
