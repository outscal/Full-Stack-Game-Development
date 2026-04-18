In this lesson, let's see how you can a 2D array.

To understand the syntax and implementation of a 2D array, we will consider some real-time game dev. examples. 
For this, we are going slightly away from our actual project minesweeper.

But don’t worry, once we understand the syntax, we will come right back to it.



![](//outscal.github.io/Full-Stack-Game-Development/images/e172a9120d7eb158.png)

**2D ARRAY**

A 2D Array is an ***array of arrays***. 

Like a 1D array, a 2D array can also be created for different Data Types like int, char, float, etc.



**Note: **You can implement the code in this lesson while reading it, in our [**Compiler**](https://outscal.com/compiler/2D-Arrays)**.**
Refer to this [**content**](https://outscal.com/course/full-stack-game-development/text-based-adventure-game/getting-started-with-letho-using-c/using-outscals-compiler-content-3) if you're not familiar with outscal's compiler.



Remember this game?🤔

![ ](//outscal.github.io/Full-Stack-Game-Development/images/97b86df6b7f22ba4.png)

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



![ ](//outscal.github.io/Full-Stack-Game-Development/images/b01e1021896909b3.png)

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
