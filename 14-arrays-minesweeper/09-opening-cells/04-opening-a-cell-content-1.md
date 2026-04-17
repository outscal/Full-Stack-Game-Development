In the previous lesson, we set up our callback system to detect when a player clicks on a cell.

But detecting clicks isn't enough - we need something to happen when those clicks are detected!

Now it's time for the exciting part - making those cells actually open when clicked!



But first, let's break down what happens when you click a cell in Minesweeper:

1. You click a cell
2. If it's not flagged or not already open, it reveals what's underneath



Updated header file. 

> **Summary📃**
> Here's what is added in the Cell class:

> 🔸`canOpenCell` function to check if a cell can open
> 🔸`open` function to open the cell



`Cell.h`

```cpp
//previous code
using namespace UIElements;

namespace Gameplay
{
    class Cell
    {
    //previous code
    public:

        bool canOpenCell() const;
        void open();
    };
}

```



> **Summary📃**
> Here's what is added in the Board class:
> 🔸`openCell` function to open the cell



`Board.h`

```cpp
//previous code

namespace Gameplay
{

    class Board
    {
    private:
 
        void openCell(sf::Vector2i cell_position);
        //previous code

    };
}
```





## Making Cells Openable


---

First, let's handle the left click in our Board class:



`Board.cpp`

```cpp
void Board::onCellButtonClicked(sf::Vector2i cell_position, MouseButtonType mouse_button_type) {
    if (mouse_button_type == MouseButtonType::LEFT_MOUSE_BUTTON) {
    		Sound::SoundManager::PlaySound(Sound::SoundType::BUTTON_CLICK); //play click sound
        openCell(cell_position); // Open the cell when left-clicked
    }
}
```



> **TODO**: 
> ✅ In the `Board.h` file add the `openCell` method. 
> ✅ Implement the `onCellButtonClicked` method to the `Board` class.



Now, let's see how to implement the `openCell` method.



## Opening the Cell


---

Now that we can check if a cell can be opened let's implement the opening logic:

`Board.cpp`

```cpp
void Board::openCell(sf::Vector2i cell_position) {
    cell[cell_position.x][cell_position.y]->open(); // Open it!
}
```

In the Cell class, set the state to `OPEN`:

`Cell.cpp`

```cpp
void Cell::open() {
    setCellState(CellState::OPEN); // Change state to OPEN
}
```



> **TODO**: 
> ✅ In the `Board.cpp` file implement the `openCell` method. 
> ✅ In the `Cell.cpp` file implement the `open` method. 
> ✅ Play the game and click on a cell



The cells can now open!

But wait! 🤔

We can't just open any cell.

What if it's already open? What if it's flagged? We need some rules!



## Cell Opening Rules


---

Let's add a method to check if a cell can be opened:

- A cell can be opened only when it is in a HIDDEN state:

`Cell.cpp`

```cpp
    bool Cell::canOpenCell() const { return current_cell_state == CellState::HIDDEN; }
```

Now, using these rules you can update the `openCell()` method of the `Board` class before opening a cell.

`Board.cpp`

```cpp
void Board::openCell(sf::Vector2i cell_position) {
    if (!cell[cell_position.x][cell_position.y]->canOpenCell()) {
        return; // Can't open this cell!
    }
	//previous code
}
```



> **TODO**: 
> ✅ Add the `canOpenCell` method to the `Board` class. 
> ✅ Implement the `openCell` method in the `Board` class. 
> ✅ Add the `open` method to the `Cell` class. 
> ✅ Play the game and open a cell



You have successfully added the logic to open a cell! 👏🏼

Now, similarly, you need to write the logic to flag a cell.

Let’s do that in the next lesson!
