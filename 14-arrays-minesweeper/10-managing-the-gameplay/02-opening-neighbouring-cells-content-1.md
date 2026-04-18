Until now, the cells are openable.

However, all types of cells simply open, and there are no consequences for a particular type of cell.

In this chapter, you'll implement the consequence of opening different types of cells!

Starting with the **empty cells** in this lesson!



Click here to see the goal of this lesson.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/ad639e4b7b81c9cb.gif)



See how the adjacent cells opened when an empty cell was opened?

That is your goal in this lesson.





First, let's understand what happens when an empty cell is opened:


<iframe src="https://www.loom.com/embed/87a77eda921f449db489fb6c75ad89d8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





Now, let's implement the logic explained in the video.

Functions you need to add in `Board.h` to open the neighboring cells.

> **Summary📃**
> Here's what is added in the Board class:

> 🔸`processCellType` function to handle different cell types
> 🔸`processEmptyCell` function to handle Empty Cells



```cpp
//previous code
namespace Gameplay
{
    class Board
    {
    private:
				//previous code
        // Private helper methods
        void processCellType(sf::Vector2i cell_position);
        //Empty Cells
        void processEmptyCell(sf::Vector2i cell_position);
    };
}
```





# Processing Cell Type


---



Now, when we open a cell, instead of opening it directly, we'll implement a logic based on its type and then open the clicked cell:

For Example: If the cell is empty, then we'll first open the neighboring cells and then the empty cell.

`Board.cpp`

```cpp
void Board::openCell(sf::Vector2i cell_position) {
    if (!cell[cell_position.x][cell_position.y]->canOpenCell())
        return;
        
    //replace open() method
    processCellType(cell_position);
}

```

First, let's create a method that handles different cell types.

You can use switch-case for different cell types: `EMPTY`, `MINE`, and other cells(Number cells)

If the cell is an `EMPTY` cell, then implement the logic for opening neighboring cells.

If the cell is a `MINE` cell, then implement the logic for opening a mine cell(in the next lesson)

And, if it is a numbered cell, then simply open the cell.

`Board.cpp`

```cpp
void Board::processCellType(sf::Vector2i cell_position) {
    switch (cell[cell_position.x][cell_position.y]->getCellType()) {
    case CellType::EMPTY:
        processEmptyCell(cell_position);
        break;
    case CellType::MINE:
		    //Handling Mine cell in next lesson
        break;
    default:
        cell[cell_position.x][cell_position.y]->open();
        break;
    }
}
```



> **TODO**: 
> ✅ Update the `openCell` method in the `Board` class. 
> ✅ Add the `processCellType` method in the `Board` class.
> ✅ Run the code to make sure there are no errors.



Now, let's focus on empty cells.



## Handling Empty Cell


---



When an empty cell is clicked:

1. Check the state of the cell
2. if it is already OPEN, then return from the function
3. Otherwise, open the cell.



`Board.cpp`

```cpp
void Board::processEmptyCell(sf::Vector2i cell_position) {
    CellState cell_state = cell[cell_position.x][cell_position.y]->getCellState();

    // Handle the clicked cell
    switch (cell_state) {
    case::Gameplay::CellState::OPEN:
        return;  // Already open, stop here
    default:
        cell[cell_position.x][cell_position.y]->open();
    }
}
```



Now, the clicked cell is empty, which means that the 8 adjacent cells around the empty cell are non-mine cells and are safe to open.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/ee31702373301e56.png)



But, what if there's an empty cell around the clicked cell?🤔

![ ](//outscal.github.io/Full-Stack-Game-Development/images/a46527cfad7e7ca6.png)



Then we can again open the 8 adjacent cells around the empty cell.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/64b7c3befe74b4bd.png)



This process of opening adjacent cells keeps on repeating until a numbered cell is opened. Because a numbered cell indicates that there's a mine around that cell.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/4019ed54e069886b.png)



Here's how we implement this chain reaction:



**Note: **The adjacent cells are traversed in the same way as explained in the [***Calculating Cell Value***](https://outscal.com/course/arrays/arrays-minesweeper/populating-the-board/calculating-cell-value-content-1) content.

`Board.cpp`

```cpp
void Board::processEmptyCell(sf::Vector2i cell_position) {
     CellState cell_state = cell[cell_position.x][cell_position.y]->getCellState();
			
		switch (cell_state) {
    case::Gameplay::CellState::OPEN:
        return;  // Already open, stop here
    default:
        cell[cell_position.x][cell_position.y]->open();
        
        
    // Check all 8 neighbors
    for (int a = -1; a <= 1; ++a) {
        for (int b = -1; b <= 1; ++b) {
        	//Store neighbor cells position
            sf::Vector2i next_cell_position = sf::Vector2i(a + cell_position.x, b + cell_position.y);
            
             //Open neighbor cell
            openCell(next_cell_position);  // Open neighbor
        }
    }
}
```



Notice how `openCell` keeps on calling `processCellType` function and then the `processEmptyCell` function is called again for the empty cell and `open()` function for the numbered cell:



![ ](//outscal.github.io/Full-Stack-Game-Development/images/a9c2ac6edee5f663.png)



`processEmptyCell` is called until all the empty cells around an empty cell are opened.

This process is called **Recursion: **When a function directly or indirectly calls itself until a terminating condition is true.** **

For the non-empty cells, the current cell is opened only once.

So, the numbered cells are the terminating condition here.

You'll learn Recursion in detail in the upcoming modules.



Don't forget to handle the edge cases:

1. If the adjacent cell is not in the bounds of the Array.
  OR
2. If the for loop is on the current cell while traversing the neighbors.

`Board.cpp`

```cpp
void Board::processEmptyCell(sf::Vector2i cell_position) {
    //Handle the current cell
    //previous code

    // Check all 8 neighbors
    for (int a = -1; a <= 1; ++a) {
        for (int b = -1; b <= 1; ++b) {
        	//Store neighbor cells position
            sf::Vector2i next_cell_position = sf::Vector2i(a + cell_position.x, b + cell_position.y);
						
						 // Skip current cell and invalid positions
            if ((a == 0 && b == 0) || !isValidCellPosition(next_cell_position)) {
                continue; 
            }

             //Open neighbor cell
            openCell(next_cell_position);  // Open neighbor
        }
    }
}
```



1. If a wrong cell is flagged and an empty cell around that cell is opened, then remove the flag and open the cell.

`Board.cpp`

```cpp
void Board::processEmptyCell(sf::Vector2i cell_position) {
    //Handle the current cell
    //previous code

    // Check all 8 neighbors
    for (int a = -1; a <= 1; ++a) {
        for (int b = -1; b <= 1; ++b) {
        	//Store neighbor cells position
            sf::Vector2i next_cell_position = sf::Vector2i(a + cell_position.x, b + cell_position.y);

            if ((a == 0 && b == 0) || !isValidCellPosition(next_cell_position)) {
                continue;  // Skip current cell and invalid positions
            }
            
            //Flagged Cell Case
            CellState next_cell_state = cell[next_cell_position.x][next_cell_position.y]->getCellState();

             if (next_cell_state == CellState::FLAGGED)
             {
                  toggleFlag(next_cell_position);
             }   
             
             //Open neighbor cell
            openCell(next_cell_position);  // Open neighbor
        }
    }
}
```



> **TODO**: 
> ✅ Implement the `processEmptyCell` method in the `Board` class. 
> ✅ Play the game.



You have successfully implemented the logic for empty cells!

Expected Output

![ ](//outscal.github.io/Full-Stack-Game-Development/images/ad639e4b7b81c9cb.gif)





In the next lesson, you'll implement the most dangerous cell type - mines! 💣
