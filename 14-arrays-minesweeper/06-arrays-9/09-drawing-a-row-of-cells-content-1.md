In this lesson, you'll render a row of cells using a 1D Array.



![ ](/Full-Stack-Game-Development/images/e085c71abad5545e.png)

**DRAWING A ROW**



Let's see how you can create an array in C++.



## **Creating an Array**


---

Now, you know data types can be of in-built data types like int, float, double, etc.

But did you know that you can create an array of custom data(Classes) types as well?!

But what is the custom data type for which you'll create an array?



Do we need an array of Boards?🤔

We need only one board, so No.



Do we need an array of Cells?🤔

We need to render one whole row of cells. 
We want to avoid creating multiple objects of Cells manually.

So, it makes sense to create an Array of Cells.



Instead of storing Cell objects directly in the array, we use an array of pointers to Cells (`Cell* cell[numberOfColumns]`).

Why do this?

Using pointers gives you more flexibility. 

Instead of allocating memory for each Cell object upfront, we only store the address (pointer) of the Cell. 
This lets us control when and how memory is allocated for each Cell object.

So, in your `Board` class, you’ll declare an array of pointers to Cells like this:

Update the `Cell* cell` variable to an array of cells with nine columns in `Board.h`:

`Board.h`

```cpp
#include <random>
#include "../../header/GameLoop/Gameplay/Cell.h"
#include "../../header/Event/EventPollingManager.h"

namespace Gameplay
{

    class Board
    {
			private:
					//previous code
					Cell* cell[numberOfColumns];
					//previous code
		}
}
```

Each element in the array will store a pointer to a Cell, and this will give you control over creating and managing the Cells later.



You have created an array of cells.

What do you think is the space complexity of the `cells[]` array? 🤔

The space complexity for the `**cell[]**` array is **O(n)**, where **n = 9**. 

Since complexity notation ignores constants, we still write it as O(n) rather than O(9).





In the previous lessons, you created a single cell.  

Now, you just need to initialize the cells array to create a whole row of cells.



![ ](/Full-Stack-Game-Development/images/e7ed6f1688e5ad40.png)





## Creating Cell Instances


---

You can use the for loop here as well, to access and initialize the `cells` array.

The size of the `cells` arrays is = `numberOfColumns` = **9, **
so you need to traverse the array till the 8th index, 
and create a new instance of the cell class for each index:

`Board.cpp`

```cpp
void Board::createBoard()
{
    float cell_width = getCellWidthInBoard();
    float cell_height = getCellHeightInBoard();
    
    //Create a cell for each array index
    for (int col = 0; col < numberOfColumns; ++col) {
    		cell[col] = new Cell(cell_width, cell_height, sf::Vector2i(col, 0));
    }
}
```

One whole row has 9 columns and the cells will render in the x-axis, hence `col` is passed in the x-axis.

Similarly, for rendering each cell, you need a for loop:

`Board.cpp`

```cpp
void Board::render(sf::RenderWindow& window)
{
		window.draw(boardSprite);
    //render array's elements one by one
    for (int col = 0; col < numberOfColumns; ++col) {
        cell[col]->render(window);
    }
}
```



Before implementing the **TODO **try solving this question:

What is the time complexity of creating and rendering cells? 🤔

Time complexities for creating and rendering the cells will be the same.

Why?

Well, because both creating and rendering cells require iterating over the array once, meaning each element is processed exactly once. 

Since the number of operations scales linearly with n, the time complexity for both operations is **O(n)**.





> **TODO: **
> `**Board.h**`** **
> **✅** Create an array of `Cell* cell[numberOfColumns]` 
> `**Board.cpp**`
> ✅ Update the `createBoard()` method. 
> ✅ Update the `render()` method.



Try playing the game!

What happened?🤔

Why is there still only one cell visible? 🤔 

Even though we created 9 cells, they are overlapping because we haven't properly positioned them in a row!

To position the cells properly, we need to calculate the positions of the cells.



## **Calculating Cell Position in an Array**


---



![ ](/Full-Stack-Game-Development/images/ad3bd30e7ac00a85.png)

**Position**

Let's assume that the width of a cell is ***'10'*** and the first cell is at '**(*****0,0)'***

Then, the cell's position at the 5th Index will be **(50, 0)**.

Because there are 5 cells with a width of 10 before it. 

**5(index)*10(width) = 50(new position in the x-axis)!**

We'll use this logic to calculate cell location based on its index.



The position of the cells is initialized in the `getCellScreenPosition` method of the Cell class, 
so you need to update the `Cell::getCellScreenPosition()` method to use the below calculation:

`**index(position in array) * width = new position on the x-axis!**`

Similarly for calculating the position on the y-axis, you need to multiply the height instead of the width:
`**index(position in array) * height= new position on the y-axis!**`



Now, how will the `getCellScreenPosition()` method access the height and width of the cell?🤔

Well, the `getCellScreenPosition` method is called in the `Cell::initiliaze` method, and we are already passing width and height as parameters in it.

So you can just pass the width and height as parameters in the `getCellScreenPosition` method.



> **TODO**: 
> ✅ In the `Cell.h` file update the signature of the `getCellScreenPostion()` method.
> 
> In `Cell::getCellScreenPosition()` method:
> **✅** In the `xScreenPosition`, add `position.x * width` 
> ✅ In the `yScreenPosition`, add `position.y * height`



Click here to see the code.

`Cell.h`

```cpp
//previous code
namespace Gameplay
{
    //previous code

    class Cell
    {
    private:
        //previous code
        sf::Vector2f getCellScreenPosition(float width, float height) const; //update the signature
        //previous code
    };
}

```



`Cell.cpp`

```cpp
sf::Vector2f Cell::getCellScreenPosition(float width, float height) const
{
    float xScreenPosition = cell_left_offset + position.x * width;
    float yScreenPosition = cell_top_offset + position.y * height;
    return sf::Vector2f(xScreenPosition, yScreenPosition);
}

```





This will make all your cells appear in a row!



![ ](/Full-Stack-Game-Development/images/e085c71abad5545e.png)

**ROW OF CELLS**



> 💡**PRO TIP: **
> **Try changing the value of the number of columns to something larger and see what happens**



**In the next chapter, you'll complete the Board by drawing more rows of cells!**

**See you there 👋**
