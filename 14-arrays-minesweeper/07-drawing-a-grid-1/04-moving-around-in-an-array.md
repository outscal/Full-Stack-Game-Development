In this lesson, you'll learn the initialization, access, and traversal of elements in 2D Arrays!



**Note: **You can implement the code in this lesson while reading it in our [**Compiler**](https://outscal.com/compiler/2D-Arrays).
Refer to this [**content**](https://outscal.com/course/full-stack-game-development/text-based-adventure-game/getting-started-with-letho-using-c/using-outscals-compiler-content-3) if you're not familiar with outscal's compiler.



Let's start with initializing the tic-tac-toe board with empty values!



## Initializing Elements in a 2D Array


---



A 2D array can be initialized in 2 ways, either at the time of declaration like:

```cpp
//Assume -1 = empty space
int ticTacToeBoard[number_of_rows][number_of_columns] = {
    {-1, -1, -1},
    {-1, -1, -1},
    {-1, -1, -1}
};
```

This is how the ticTacToeBoard array looks:

```cpp
-1 -1 -1
-1 -1 -1
-1 -1 -1
```

In this board, -1 represents an empty cell, 1 represents player X, and 0 represents player O.

Now that the 2D array is initialized, how do you access each element of the array? 🤔



## ACCESSING an Element in a 2D Array


---



Let's say you want to check whether a cell in **row 2, column 3** is occupied.

You would write the following code:

`int move = ticTacToeBoard[1][2];`

**Notice**: 1 is subtracted from both indices because, in arrays, indices begin from '0'.



Now that you know how to access the elements in a 2D array, let's understand another way of initializing an array. This is done by traversing each element of the array using a for loop.



Like in a **1D array** you use a for-loop:

```cpp
int oneDArray[5] = {1, 2, 3, 4, 5};

    // Traversing a 1D array
    for(int i = 0; i < 5; ++i) {
        cout << "Element at index " << i << ": " << oneDArray[i] << endl;
    }
```

**TRAVERSING 1D ARRAY**



click here to see the Output![undefined](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/02_10_2024__13_26_30.png)





Similarly, we use ***"nested-loop"*** to traverse a 2D array



> 📖🎮**Game Dev Dictionary**
> ***nested-loop:*** *"*Nested loops are loops within loops; they let you step through elements in a grid, handling each row and then each column. More nested levels mean more detail, but also more complexity and longer run times.*" *



## Traversing A 2D Array


---




<iframe src="https://www.loom.com/embed/47b111ade78945caba57a5b940d569b9" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





```cpp
    // Traversing a 2D array
    for(int i = 0; i < number_of_rows; ++i) {
        for(int j = 0; j < number_of_columns; ++j) {
            cout << "Element at [" << i << "][" << j << "]: " << ticTacToeBoard[i][j] << endl;
        }
    }
```

**TRAVERSING 2D ARRAY**



> **TODO: **[**Compiler**](https://outscal.com/compiler/2D-Arrays)
> **✅ **Initialize the `ticTacToeBoard` array using a for loop.
> ✅ Print all the elements of the `ticTacToeBoard` array using a for loop.



You now know how to create, initialize, and traverse a 2D array.

But do you how is memory allocated to a 2D array?🤔



## **Memory Allocation of a 2D Array**


---

Internally `ticTacToeBoard` stores the address of the first element of the array. 
It stores the **base address**.



Address for any element is calculated using this formula:

> address = **base_address** + (row_index * number_of_columns * size_of_element) + (column_index * size_of_element)



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/03_12_2025__11_01_24.png)



Since memory is stored **row-wise (row-major order)** in C++, the formula ensures that elements in the same row are stored next to each other.

For example if you want to access the 8th element, then this is how its address is calculated:

```text
address = base_address + (row_index * number_of_columns * size_of_element) + (column_index * size_of_element)
address = 1000 + (2 * 3 * 4) + (1 * 4)
address = 1028
```



👆🏼Click here for a fun TODO:

```cpp
#include <iostream>

int main() {
  int ticTacToeBoard[3][3];
  std::cout << "arr: "<<ticTacToeBoard <<"\n";
  std::cout << "arr: "<<&ticTacToeBoard[0][0]<<"\n";
  std::cout << "arr: "<<&ticTacToeBoard[0][1]<<"\n";
  std::cout << "arr: "<<&ticTacToeBoard[0][2]<<"\n";
  std::cout << "arr: "<<&ticTacToeBoard[1][0]<<"\n";
}
```



> **TODO:**
> ✅Run the above program in a compiler and notice the values printed



Each value is the address of the element and notice that each address is 4 bytes (size of int)







You know now about 2D arrays in detail!

And you have also created your own 2D array 💪🏼

Now, let's understand some operations on 2D arrays.



## Making a Move in Tic-Tac-Toe (Insertion)


---

What is making a move? 🤔

Well, making a move is placing a value (X or O) at a specific position on the board that is currently empty.

So, if a `ticTacToeBoard` has all empty spaces (represented by -1) and player X wants to place their mark at the center, we need to set the value at row 1, column 1 to 1 which is used for X.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/03_19_2025__08_01_32.png)



Now you know what making a move means. But, how to actually make a move on the board?🤔 Making a move requires checking if the position is empty and then placing the symbol:

```cpp
int row = 1;
int col = 1;
int playerSymbol = 1; // 1 for X, 0 for O

// Check if position is valid and empty
if(row >= 0 && row < number_of_rows && col >= 0 && col < number_of_columns) {
    if(ticTacToeBoard[row][col] == -1) {
        // Make the move
        ticTacToeBoard[row][col] = playerSymbol;
        cout << "Move successful!" << endl;
    } 
    else 
    {
        cout << "Position already taken! Try again." << endl;
    }
} 
else 
{
    cout << "Invalid position! Row and column must be between 0 and 2." << endl;
}
```



**What is the time complexity of making a move in the ticTacToeBoard array? 🤔**

Making a move involves checking if the position is valid and empty, then setting a value at that position. 

All of these operations are direct memory accesses that take constant time. 

**Time complexity is O(1),** as it doesn't depend on the board size.





## Resetting the Board (Deleting Elements)


---



What is resetting the board? 🤔

Well, resetting the board is just updating every position on the board to its default value, which in this case is `-1` to indicate that no moves have been made.

So, if a `ticTacToeBoard` has various player marks from a previous game, we need to set all elements to `-1` to prepare for a new game.

Now you know what resetting the board means. But how do we actually reset the board?🤔 Resetting can be done using loops:

```cpp
// Reset the tic-tac-toe board to -1
for(int i = 0; i < number_of_rows; i++) {
    for(int j = 0; j < number_of_columns; j++) {
        ticTacToeBoard[i][j] = -1; // Set each position to -1
    }
}
```

#### **How does it work?**

1. We use **nested loops** to go through each row and column.
2. Every position in `ticTacToeBoard[i][j]` is set to `-1`.
3. After execution, the board is completely reset to its initial state.



**What is the time complexity of deleting all elements in the ticTacToeBoard array? 🤔**

Resetting the board involves iterating over all positions and setting each to `-1`.

Each position must be modified individually, so the time taken depends on the total number of rows and columns.

Time complexity is **O(n²)**, as `number_of_rows = number_of_columns` .



Deleting all the elements is equivalent to traversing each element and marking it as -1 hence it will have **O(n²)** but if you need to delete a single element and you know the location of it then what will be the Time Complexity? 

It will be **O(1)**





Finally, searching in 2D arrays.



## Checking for a Win (Searching)


---

What is Searching for an Empty Space? 🤔

In a game like Tic-Tac-Toe, searching for an empty space is essential to determine where a move can be placed. 

An empty space is represented by `-1` on the board.

Let's consider the case of searching for the **first available empty space**:

- If a `ticTacToeBoard` has an empty slot at `[0][2]`, `[1][1]`, or `[2][0]`, the algorithm should detect the first available position and return it.
- This helps the game logic decide where a player or AI can make their next move.

Now you know what searching for an empty space means. But how do we actually find an empty space on the board? 🤔 

Searching can be done using loops.

```cpp
		bool emptySpaceFound = false; // Assume no empty space initially
    int emptyRow = -1, emptyCol = -1; // Store empty space coordinates

    // Searching for an empty space (-1) on the board
    for (int i = 0; i < number_of_rows; i++) {
        for (int j = 0; j < number_of_cols; j++) {
            if (ticTacToeBoard[i][j] == -1) {
                emptySpaceFound = true;
                emptyRow = i;
                emptyCol = j;
                break; // Stop search once an empty space is found
            }
        }
        if (emptySpaceFound) 
        		break;
    }

    // Print result
    if (emptySpaceFound) {
        cout << "Empty space found at row " << emptyRow << ", column " << emptyCol << "!" << endl;
    } 
    else {
        cout << "No empty spaces left on the board!" << endl;
    }

    return 0;
}

```



**What is the time complexity of searching for an empty space in the ticTacToeBoard array? 🤔**

For a Tic-Tac-Toe board, finding an empty space requires scanning each position until an empty one (`-1`) is found.

- In this example, we loop through the board until an empty space is located.
- A full search of an **n × n** board may require checking all `n²` positions in the worst case, giving a **time complexity of O(n²)**.





You have learned 2D arrays in detail! 💪🏼

In the next lesson, you'll implement 2D Arrays to complete the grid in our game.

See you there 👋🏼
