![ ](//outscal.github.io/Full-Stack-Game-Development/images/e5ccad594a07aac0.png)

**ELONGATED CELL**



Okay, so we increased the button's width and this happened. 

But at a time you only need a specific piece of this long image, not the entire thing.

**How to solve this?**

The height of the texture is 128 Pixels, therefore, the width of a single cell will be 128 Pixels.

You can use this information to slice the specific area of the texture you want.

To identify what part of the texture you want, you need to understand the cell's behavior.

In this lesson, you'll understand the cell's behavior.



## **CELL BEHAVIOUR**


---


<iframe src="https://www.loom.com/embed/2aecb425b32f4664af06f03075be64d4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



Depending on the number of mines around a cell, it can either be a mine, empty, or numbered. Let's call this **CellType**



![ ](//outscal.github.io/Full-Stack-Game-Development/images/b9ae323737cdab71.png)

**Different Cell Types**



A cell can also be flagged or unflagged(Hidden). The default state of a cell is Hidden.  Let's call this **CellState**



![ ](//outscal.github.io/Full-Stack-Game-Development/images/9d889a8af971598a.png)

**Different Cell State**



Cell State and Cell Type define a cell's appearance and also its behaviour.

You can use `enums` for Cell State and Cell Type!



Cell.h

> **Summary📃**

> Here's what is updated in the `Cell.h` file:

> 🔸Added two enums to maintain `CellState` and `CellType` as follows:



`Cell.h`

```cpp
namespace Gameplay
{
    enum class CellState
    {
        HIDDEN,
        OPEN,
        FLAGGED,
    };

    enum class CellType
    {
        EMPTY,
        ONE,
        TWO,
        THREE,
        FOUR,
        FIVE,
        SIX,
        SEVEN,
        EIGHT,
        MINE,
    };

    //Cell Class
}

```





Now, you need to create variables for these enums.



> **TODO: **
> **✅** In Cell class create `CellState current_cell_state` variable. 
> ✅ In Cell class create `CellType cell_type` variable. 
> ✅ Create Getters and Setters for these variables.
> ✅ Define Getters and Setters in `Cell.cpp` file.
> ✅ Run the code to make sure that there are no errors



Click here to see the solution.

> **Summary📃**

> Here's what is updated in the `Cell` class:

> 🔸Added two objects of `CellState` and `CellType` enums.
> 🔸Created getters and setters for `current_cell_state` and `cell_type`.



`Cell.h`

```cpp
class Cell
{
private:
    // Cell data members
    CellState current_cell_state;
		CellType cell_type;

    //previous code

public:
    //previous code

    //Getters, Setters
		CellState getCellState() const;
		void setCellState(CellState state);
		CellType getCellType() const;
		void setCellType(CellType type);
};

```



`Cell.cpp`

```cpp
CellState Cell::getCellState() const { return current_cell_state; }

void Cell::setCellState(CellState state) { current_cell_state = state; }

CellType Cell::getCellType() const { return cell_type; }

void Cell::setCellType(CellType type) { cell_type = type; }

```





You have successfully set up the `CellState` and `CellType` enums.

In the next lesson, you’ll *slice* cell texture to render the relevant cell with the help of `CellState` and `CellType` enums.
