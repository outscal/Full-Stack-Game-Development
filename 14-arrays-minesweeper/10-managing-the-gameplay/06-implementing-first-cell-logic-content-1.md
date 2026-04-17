In Minesweeper, there's a crucial rule: the first click should never be a mine!

In this lesson, you're going to implement this logic💪🏼



Think about it - it wouldn't be fair to lose on your very first move, would it? 

To make this work, we need to be clever.

Instead of placing mines when creating the board, 
we'll wait until after the first click. 

This way, we can ensure that the first click is always safe!

You need to track the Board's State to do this.

What are board states?🤔

Well, there are 3 board states:

- First Cell State
- - When the player opens the first cell
- Playing
- - When the first cell is opened.
- Completed
- - When the player has won or lost the game



Update `Board.h` file

> **Summary📃**
> Here's what is added in the Board class:
> 🔸Enum for tracking Board State
> 🔸Variable for `BoardState` enum
> 🔸Helper function to skip the first cell
> 🔸Getters and Setters for `board_state` variable.



`Board.h`

```cpp
namespace Gameplay
{
		enum class BoardState
		{
		    FIRST_CELL,
		    PLAYING,
		    COMPLETED,
		};
		
		class Board{
		private:
					BoardState boardState;
					//previous code
					bool isInvalidMinePosition(sf::Vector2i first_cell_position, int x, int y);
					
		public:
					//previous code
					BoardState getBoardState() const;
					void setBoardState(BoardState state);

		}
}
```





Now, 

Let's implement this step by step:

First, you need to initialize the board’s state to the First cell:



`Board.cpp`

```cpp
void Board::initializeVariables(GameplayManager* gameplay_manager) {
        this->gameplay_manager = gameplay_manager;
        randomEngine.seed(randomDevice());
    		boardState = BoardState::FIRST_CELL;  // Start with first cell state
}
```



Then, while opening a cell, 
if the board state is `FIRST_CELL`, 
then, while populating the board, you can skip the first cell’s position so that mine doesn’t get plotted on that cell.

After populating the board, change the board’s state to playing.



Now, let's modify our `openCell` method to handle the first click specifically:

**Note: **

1. You need to update the signature `populateBoard()` add the `sf::Vector2i cell_position` as a parameter.
2. Remove the function call of `populateBoard()` from `initialize()` and add it in `openCell()`

`Board.cpp`

```cpp
void Board::openCell(sf::Vector2i cell_position) {
    if (!cell[cell_position.x][cell_position.y]->canOpenCell())
        return;

    if (boardState == BoardState::FIRST_CELL) {
        populateBoard(cell_position);    // Place mines after first click
        boardState = BoardState::PLAYING; // Now we can play normally
    }
		
		processCellType(cell_position);
}
```



> **TODO**: 
> ✅ Update the `Board.h` file.
> ✅ Update the `initializeVariables` method in the `Board` class. 
> ✅ Update the `openCell` method in the `Board` class.
> ✅ Run the code to make sure there no errors



When placing mines, we need to make sure we don't put them on the first clicked cell:

**Note: **You need to update the signature `populateMines()` add the `sf::Vector2i first_cell_position` as a parameter.

Move the Mine check also to `isInvalidMinePosition` method:

`Board.cpp`

```cpp
void Board::populateMines(sf::Vector2i first_cell_position) {
    //previous code
    int mines_placed = 0;
    while (mines_placed < minesCount) {
        int x = x_dist(randomEngine);
        int y = y_dist(randomEngine);

        if (isInvalidMinePosition(first_cell_position, x, y))
            continue;  // Skip first cell's position before placing a mine

        cell[x][y]->setCellType(CellType::MINE);
        ++mines_placed;
    }
}
```

**Note**: You can remove the previous mine check as it is handled in the `isInvalidMinePosition` function.

And here's how we check if a position is valid for a mine:

- If the clicked is the first cell
  OR
- If the cell already has a mine

`Board.cpp`

```cpp
bool Board::isInvalidMinePosition(sf::Vector2i first_cell_position, int x, int y) {
    return (x == first_cell_position.x && y == first_cell_position.y) ||
           cell[x][y]->getCellType() == CellType::MINE;
}
```



Lastly, you also need to implement the getter and setter functions for the `boardState` variable.



> **TODO**: 
> ✅ Implement the `populateMines` and `isInvalidMinePosition` methods in the `Board` class.
> ✅ Implement the `getBoardState` and `setBoardState` functions in the `Board` class
> ✅ Play the game.



Click here to see the solution.

`Board.cpp`

```cpp
    BoardState Board::getBoardState() const 
    { 
    		return boardState; 
    }

    void Board::setBoardState(BoardState state) 
    { 
    		boardState = state; 
    }
```





Now your first click will always be safe, making the game much more enjoyable to play!

But, the player can easily win the game because the players can play the game forever!

There’s no time limit.

In the next lesson, you’ll add a timer ⏱️ to make your game even more challenging!💪🏼
