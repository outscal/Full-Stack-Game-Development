Now that we can open cells with a left click, let's implement the right-click functionality - flagging cells! 🚩

In Minesweeper, players use flags to mark cells they think contain mines.

This helps them keep track of potential mine locations without accidentally opening them.



Update header files.

> **Summary📃**
> Here's what is added in the `Board` class:

> 🔸`flaggedCell` variable to keep track of the number of flagged cells
> 🔸`toggleFlag` function to flag the cell



`Board.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>
#include <random>
#include "../../header/GameLoop/Gameplay/Cell.h"
#include "../../header/Event/EventPollingManager.h"

namespace Gameplay
{
    class Board
    {
    private:
        //previous code
        int flaggedCells;

        //previous code
        void toggleFlag(sf::Vector2i cell_position);

      //previous code
      }
}
```



> **Summary📃**
> Here's what is added in the `Cell` class:
> 🔸`toggleFlag` function to flag the cell



`Cell.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>
#include "../../header/UI/UIElements/Button/Button.h"
#include "../../header/Event/EventPollingManager.h"

using namespace UIElements;

namespace Gameplay
{
   //previous code

    class Cell
    {
    	//previous code
    	public:
        void toggleFlag();
    };
}


```





## Flagging a Cell


---



Let's add this feature to our game:

First, we need to modify the `onCellButtonClicked` to handle the right clicks:

`Board.cpp`

```cpp
void Board::onCellButtonClicked(sf::Vector2i cell_position, MouseButtonType mouse_button_type)
{
    if (mouse_button_type == MouseButtonType::LEFT_MOUSE_BUTTON)
    {
    		Sound::SoundManager::PlaySound(Sound::SoundType::BUTTON_CLICK);
        openCell(cell_position);
    }
    //Right Click
    else if (mouse_button_type == MouseButtonType::RIGHT_MOUSE_BUTTON)
    {
    		Sound::SoundManager::PlaySound(Sound::SoundType::FLAG);//play flag sound
        toggleFlag(cell_position);
    }
}
```



> **TODO**: 
> ✅ Update the `onCellButtonClicked` method in the `Board` class.



Now, let's implement the `toggleFlag` method in the Board class:

- Toggle the flag
- If the current cell is FLAGGED then increase the `flaggedCells` by 1 and decrease by 1 otherwise.

`Board.cpp`

```cpp
void Board::toggleFlag(sf::Vector2i cell_position) {
    cell[cell_position.x][cell_position.y]->toggleFlag();
    flaggedCells += (cell[cell_position.x][cell_position.y]->getCellState() == CellState::FLAGGED) ? 1 : -1;
}
```



Next, we need a way to toggle flags in the cell class.

When you right-click a cell:

- If it's hidden, it should become flagged
- If it's already flagged, it should become hidden again

Here's how we implement this toggle behavior:

`Cell.cpp`

```cpp
void Cell::toggleFlag() {
    if (current_cell_state == CellState::HIDDEN) {
        setCellState(CellState::FLAGGED);
    } else if (current_cell_state == CellState::FLAGGED) {
        setCellState(CellState::HIDDEN);
    }
}
```



> **TODO**: 
> ✅ Implement the `toggleFlag` method in the `Board` class. 
> ✅ Implement the `toggleFlag` method to the `Cell` class. 
> ✅ Right-click on cells to test the flagging mechanism.



You can now flag a cell!

But, currently, there are no consequences for opening a particular cell type.

You’ll fix this in the next chapter!

See you there 👋🏼
