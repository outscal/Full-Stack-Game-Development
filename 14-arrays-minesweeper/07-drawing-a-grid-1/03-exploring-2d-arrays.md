In this lesson, let's see how you can a 2D array.

To understand the syntax and implementation of a 2D array, we will consider some real-time game dev. examples. 
For this, we are going slightly away from our actual project minesweeper.

But don’t worry, once we understand the syntax, we will come right back to it.



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/02_17_2024__11_53_10.png)

**2D ARRAY**

A 2D Array is an ***array of arrays***. 

Like a 1D array, a 2D array can also be created for different Data Types like int, char, float, etc.



**Note: **You can implement the code in this lesson while reading it, in our [**Compiler**](https://outscal.com/compiler/2D-Arrays)**.**
Refer to this [**content**](https://outscal.com/course/full-stack-game-development/text-based-adventure-game/getting-started-with-letho-using-c/using-outscals-compiler-content-3) if you're not familiar with outscal's compiler.



Remember this game?🤔

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/03_06_2025__06_30_18.png)

**TIC-TAC-TOE**



The entire *TIC-TAC-TOE* game can be created just using a 2D array!

Let's see how we can use a 2D array in *TIC-TAC-TOE*.



## Creating a 2D Array


---

First, let's see how you can create a Tic-Tac-Toe board

**Creating a 2D integer array:**

`**Syntax**`

```cpp
int number_of_rows = 3;
int number_of_columns = 3;
int ticTacToeBoard[number_of_rows][number_of_columns];
```



> **TODO: **[**Compiler**](https://outscal.com/compiler/2D-Arrays)
> **✅ **Create a `int ticTacToeBoard[number_of_rows][number_of_columns]`



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/03_06_2025__06_39_05.png)

**Declaring a 2D Array**



> **💡PRO TIP: **Declaring 2D arrays
> 2D arrays can be declared in multiple ways:
> 1. Using constants for size: `int arr[5][10];` where 5 and 10 are fixed sizes for rows and columns.
> 2. Using variables for size:
> 
> `int n = 3`
> `int m = 3`
> `int arr[n][m];`



You have successfully created a *tic-tac-toe *board using a 2D array! 💪🏼

In the next lesson, you learn how to initialize, access, and traverse the elements of a 2D array using the same tic-tac-toe example

**See you there! 👋🏼**
