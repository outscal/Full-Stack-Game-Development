In this lesson, you'll write the implementation to place a fixed number of mines **randomly** on the board.

Why Do We Need Random Mines? 🤔

Think about it - if mines were in the same cell every time, Minesweeper would be like watching a movie you've already seen. 

You know all the surprises!



> 📖 🎮 **GAME DEV DICTIONARY **
> ***Random Placement***: "A technique where game elements are positioned randomly to create unique gameplay experiences each time."



Let's start by updating the `Board.h` file.



## Setting Up the Board


---



Update Board class 

> **Summary📃**
> Here is list of thing that you need to add:
> 🔸`**std::default_random_engine randomEngine;**`: A pseudo-random number generator that produces numbers based on a seed.
> 🔸`**std::random_device randomDevice;**`**: **Generates a truly random number, often used to create a seed for more predictable random generators.
> 🔸`minesCount`: A variable to keep track of number of mines
> 🔸`populateBoard()`, `populateMines()`: Functions to populate the board



`Board.h`

```cpp
#include <SFML/Graphics.hpp>
#include <random>
#include "../../header/GameLoop/Gameplay/Cell.h"
#include "../../header/Event/EventPollingManager.h"

namespace Gameplay
{
    class Board
		private:
    //Randomization
    std::default_random_engine randomEngine;
    std::random_device randomDevice;

    //Number of Mines
    static const int minesCount = 9;

    //Populating the Board
    void populateBoard();
		void populateMines();
		
		void initializeVariables();
		
		//previous code
		}
}
```







Now, you need to seed an initial value for the random engine:

`Board.cpp`

```cpp
void Board::initialize()
{
    initializeBoardImage();
    initializeVariables(); //initialize random engine
    createBoard();
}

void Board::initializeVariables()
{
    randomEngine.seed(randomDevice()); //Function to initialize random engine
}
```

You have already learned [Randomization](https://outscal.com/course/full-stack-game-development/c-intermediate-pokemon/wild-pokemons/pseudo-random-numbers-content-1) in C++ intermediate module.

- `randomDevice()` generates a random number.
- `seed()` initializes `randomEngine` with this value, ensuring a different random sequence every run.



We are now ready to place the mines on the board 💪🏼

Let's see how you can place the mines.



## Placing the Mines!


---



The process of placing mines is straightforward,

Here's the algorithm for placing mines:

1. Generate random `x` and `y` coordinates within the grid dimensions using `std::uniform_int_distribution`.
2. Check if the randomly selected cell already contains a mine.
3. If not, place a mine in the cell by setting its type to `CellType::MINE`.
4. Repeat until the total number of mines (`minesCount`) is placed.



Let’s implement this algorithm step by step:

1. Generate random `x` and `y` coordinates within the grid dimensions using `std::uniform_int_distribution` and initialize `mines_placed` to 0.

`Board.cpp`

```cpp
void Board::populateMines() {
		//Step 1
    std::uniform_int_distribution<int> x_dist(0, numberOfColumns - 1);
    std::uniform_int_distribution<int> y_dist(0, numberOfRows - 1);
    int mines_placed = 0;
}
```



> **💡PROTIP:** 
> `std::uniform_int_distribution` ensures each grid coordinate has an equal chance of being selected.



1. Store the randomly generated coordinates in local variables:

`Board.cpp`

```cpp
void Board::populateMines() 
{
		//Step 1
    std::uniform_int_distribution<int> x_dist(0, numberOfColumns - 1);
    std::uniform_int_distribution<int> y_dist(0, numberOfRows - 1); 		
		int mines_placed = 0;
		
		//Step 2
    int x = x_dist(randomEngine);
    int y = y_dist(randomEngine);
}
```



1. Now, check if the randomly selected cell already contains a mine. 
2. If not, place a mine in the cell by setting its type to `CellType::MINE` and increase the `mines_placed`.



`Board.cpp`

```cpp
 	 void Board::populateMines() 
	{
		//Step 1
    std::uniform_int_distribution<int> x_dist(0, numberOfColumns - 1);
    std::uniform_int_distribution<int> y_dist(0, numberOfRows - 1); 		
		int mines_placed = 0;
		
		//Step 2
    int x = x_dist(randomEngine);
    int y = y_dist(randomEngine);
    
 	 //Step 3
   if (cell[x][y]->getCellType() != CellType::MINE) {
   		//Step 4
       cell[x][y]->setCellType(CellType::MINE);
       ++mines_placed;
    }
}
```



1. Repeat the process from Step 2 until the total number of mines (`minesCount`) are placed.



`Board.cpp`

```cpp
 	 void Board::populateMines() 
	{
		//Step 1
    std::uniform_int_distribution<int> x_dist(0, numberOfColumns - 1);
    std::uniform_int_distribution<int> y_dist(0, numberOfRows - 1); 		
		int mines_placed = 0;
		
		//Step 5
		while (mines_placed < minesCount) {
				//Step 2
		    int x = x_dist(randomEngine);
		    int y = y_dist(randomEngine);
		    
		 	 //Step 3
		   if (cell[x][y]->getCellType() != CellType::MINE) {
		   		//Step 4
		       cell[x][y]->setCellType(CellType::MINE);
		       ++mines_placed;
		    }
		}
}
```



That’s it!

Lastly, you just need to call the `populateMines()` in the `populateBoard()` method.

And `populateBoard()` in the `Board::initialize` method.



> **TODO: **
> **✅** Update the `Board.h` file. 
> ✅ Implement `populateMines()` function. 
> ✅ In `populateBoard()` function call the `populateMines()` function. 
> ✅ In `Board::initialize()` call the `populateBoard()` function. 
> ✅ Play the game.



Click here to see the solution.

`Board.cpp`

```cpp
void Board::initialize()
{
    initializeBoardImage();
    initializeVariables();
    createBoard();
    //populate the board
    populateBoard();
}


void Board::populateBoard()
{
    populateMines();
}

void Board::populateMines()
{
    std::uniform_int_distribution<int> x_dist(0, numberOfColumns - 1);
    std::uniform_int_distribution<int> y_dist(0, numberOfRows - 1);

    int mines_placed = 0;
    while (mines_placed < minesCount)
    {
        int x = x_dist(randomEngine);
        int y = y_dist(randomEngine);

         if (cell[x][y]->getCellType() != CellType::MINE) {
		   		//Step 4
		       cell[x][y]->setCellType(CellType::MINE);
		       ++mines_placed;
		    }
    }
}
```




Did you see any mines?🤔

I don’t think so.

To visually see the mines, you can set the cell’s state to OPEN!



## Making Mines Visible


---



To make the mines visible, you need to update the `initialize` method of the `Cell` class.

We'll make our mines visible by changing the state of the cell to `OPEN`:

`Cell.cpp`

```cpp
void Cell::initialize(float width, float height, sf::Vector2i position) {
    this->position = position;
    sf::Vector2f cellScreenPosition = getCellScreenPosition(width, height);
    cell_button = new Button(cell_texture_path, cellScreenPosition, width * slice_count, height);
    current_cell_state = CellState::OPEN; // Temporarily set to OPEN for visualization
    }
```

This helps us see if our mines are placed correctly!



> **TODO**: 
> ✅ Modify `Cell::initialize` to show mines 
> ✅ Play the game



Now, you should be able to see the mines!

![ ](/Full-Stack-Game-Development/images/5745ec906a33d47c.png)







Now that your mines are placed, you need to calculate the values of the empty cells!

How to do that?🤔

You’ll know it in the next lesson!

See you there 👋🏼
