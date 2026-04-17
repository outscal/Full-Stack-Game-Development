You understand what are 2D Arrays and how to create, access, and traverse a 2D Array.

That is all you need to draw a grid!

In this lesson, you will replace your 1D array with a 2D array.



## **Creating a 2D Array for Board**


---



It's time to replace the boring 1D Array of cells with an awesome 2D array for the board!

Update the `cell[]` 1D Array to a `cell[][]` 2D Array:

`Board.h`

```cpp
private:
Cell* cell[numberOfRows][numberOfColumns];
```



What is the space complexity of the `cell[][]` array? 🤔

For a 2D Array, the space complexity is the total number of elements.

Since `numberOfRows = numberOfColumns = n`, the correct space complexity is **O(n²)**.

If rows(n) are not equal to the number of columns(m), then space complexity will be **O(n*m)**



## **Initializing a 2D Array for Board**


---

Now, you need to initialize the `cell` array.

We already have for loop in place, you just need to add another for loop to complete the initialization.

Update the 1D array code:

`Board.cpp`

```cpp
void Board::createBoard()
{
    float cell_width = getCellWidthInBoard();
    float cell_height = getCellHeightInBoard();
    
    //create cells for the cell[][] array
    for (int row = 0; row < numberOfRows; ++row)
    {
        for (int col = 0; col < numberOfColumns; ++col)
        {
            cell[row][col] = new Cell(cell_width, cell_height, sf::Vector2i(row, col));
        }
    }
}

```



What is the time complexity of initializing the `cell[][]` array? 🤔

For a 2D Array, the space complexity is the total number of elements.

The initialization loops over `numberOfRows × numberOfColumns`, meaning each cell is initialized once.

**Time complexity is O(n²),** as the nested loops iterate `n²` times (`numberOfRows * numberOfColumns`).





Currently, we are only rendering one row on the screen. 

Apply your learnings of the 2D array and make the changes in the render function to render a grid of cells on the screen.



> **TODO**: 
> In `Board.h` 
> ✅ Change the `Cell* cell[numberOfColumns]` to `Cell* cell[numberOfRows][numberOfColumns]` 
> In `Board.cpp` 
> ✅ Update the `createBoard()` method. 
> ✅ Update the `render()` method.



Click here to see the solution.

`Board.cpp`

```cpp
void Board::render(sf::RenderWindow& window)
{
    window.draw(boardSprite);
    
    for (int row = 0; row < numberOfRows; ++row)
        for (int col = 0; col < numberOfColumns; ++col)
            cell[row][col]->render(window);
}
```





Final Output.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_13_2025__13_08_56.png)





You have come a long way! 

And now you'll move on to creating interesting gameplay logic that makes the game super fun!

**See you in the next chapter👋**
