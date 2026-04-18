Your board is ready!

In this lesson, you'll make the cells clickable. 🖱️

This lesson is going to be lengthy! So make sure you do it with proper focus.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/1e51c6b084f82418.png)





How do you know when a player has clicked on a cell?🤔

Well, there’s a simple way to detect this,

If the player’s mouse is on the cell’s sprite and has pressed the left mouse button, you can say that the player has clicked on a cell!

You already have a function to detect left and right click in the `EventPollingManager` (Outscal team has already coded `EventPollingManager` for you).

You just need a new function to check if the player’s mouse is on the cell.



> **TODO**: `Button.h`
> ✅ Add  a `private` `bool isMouseOnSprite(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` method.



## Detecting a Mouse Click


---



Okay, now how do you compare the mouse position with the sprite’s position?🤔

1. Get the position of the mouse using the  `getMousePosition()` function of the `EventPollingManager` class.
2. Check if the mouse’s position is present in the bounds of `buttonSprite`

That’s it!

It’s that simple 😌



`Button.cpp`

```cpp
bool Button::isMouseOnSprite(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)
{
		//Get the position of the mouse
    sf::Vector2i mouse_position = event_manager.getMousePosition();
    
    //Check if the mouse’s position is present in the bounds of buttonSprite.
    return buttonSprite.getGlobalBounds().contains(static_cast<float>(mouse_position.x), static_cast<float>(mouse_position.y));
}
```



> **TODO**: `Button.cpp`
> ✅ Implement the `bool isMouseOnSprite(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` method.
> ✅ Run the code to make sure there are no errors



You have implemented the function to check if the mouse is on the button.

Now, you just need to detect the mouse click.



## Detecting Mouse Clicks


---

To detect a mouse click, you need to use the `EventPollingManager`’s `pressedLeftMouseButton()` and `pressedRightMouseButton()` functions.

Let's do this using a new method to handle the logic that is implemented after detecting a click.



> **TODO**: 
> In the `Button.h` file 
> ✅ Add a `public:` `void handleButtonInteractions(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` function.



Now, how to implement this method?🤔

For now, you can just add a print statement for left click and right click.

This is straightforward, try implementing this on your own:

- Check if the mouse is on the `buttonSprite` and if the player has pressed the left mouse button.

If both the conditions are true then print Left Click Detected

-  Else check if the mouse is on the `buttonSprite` and if the player has pressed the right mouse button.

If both the conditions are true then print Right Click Detected


> **TODO**: 
> In the `Button.cpp` file 
> ✅Implement the `void handleButtonInteractions(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` function.
> ✅Run the code to make sure there are no errors.



Click here to see the solution.

`Button.cpp`

```cpp
void Button::handleButtonInteractions(Event::EventPollingManager& event_manager, const sf::RenderWindow& window) {

    if (event_manager.pressedLeftMouseButton() && isMouseOnSprite(event_manager, window))
        //handle logic
        std::cout << "Left Click Detected" << std::endl;
    
    else if (event_manager.pressedRightMouseButton() && isMouseOnSprite(event_manager, window))
     		//handle logic
        std::cout << "Right Click Detected" << std::endl;
}
```





Now, to detect the mouse clicks, 
you need to call the `handleButtonInteraction()` method in the `update` function of the `Cell` class to detect button interactions at every frame:



> **Note: **
> 1. You need to declare a
> `public:`
> `void update(Event::EventPollingManager& eventManager, sf::RenderWindow& window)` method in the `Cell.h`, `Board.h` , and `GameplayManager.h` files.
> 2. Don't forget to use the `Event` namespace in the  `Cell.h`, `Board.h` , and `GameplayManager.h` files



Here's how the update method of the cell class will be called:

![ ](//outscal.github.io/Full-Stack-Game-Development/images/8b211d8484e2ec02.png)



Let's start with the cell class:

1. If the `cell_button` is not null, then call the `handleButtonInteractions` method: 

`CelWe l.cpp`

```cpp
void Cell::update(Event::EventPollingManager& eventManager, sf::RenderWindow& window)
{
    if (cell_button)
        cell_button->handleButtonInteractions(eventManager, window);
}
```





1. Then, update every cell on the board:

`Board.cpp`

```cpp
void Board::update(Event::EventPollingManager& eventManager, sf::RenderWindow& window)
{
    for (int row = 0; row < numberOfRows; ++row)
        for (int col = 0; col < numberOfColumns; ++col)
            cell[row][col]->update(eventManager, window);
}
```





1. Update the board in the gameplay manager:

`GameplayManager.cpp`

```cpp
void GameplayManager::update(EventPollingManager& eventManager, sf::RenderWindow& window)
{
		board->update(eventManager, window);
}
```





1. Update the gameplay manager in the GameLoop class:

`GameLoop.cpp`

```cpp
void GameLoop::update()
{
    Time::TimeManager::update();
    event_manager->update();
    window_manager->update();

    switch (current_state)
    {
    case GameState::SPLASH_SCREEN:
        splash_screen_manager->update();
        break;
    case GameState::MAIN_MENU:
        break;
    case GameState::GAMEPLAY:
        gameplay_manager->update(*event_manager, *game_window); //update gameplay_manager
        break;
    case GameState::EXIT:
        game_window->close();
        break;
    }
}
```





1. The main function handles the overall flow, hence it calls the update method of the `GameLoop` class.



> **TODO**: 
> In the `Cell.cpp`, `Board.cpp`, `GameplayManager.cpp`, and `GameLoop.cpp` files 
> ✅ Implement the `update()` methods for respective classes. 
> ✅ Play the game and test left and right click by clicking on the cells.



Example Expected Output.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/661949bec75ef0d2.png)





You can now successfully detect mouse clicks!

Now, you need to change the state of the cells to open or flag.

You can do it directly by accessing and changing the `**CellState**`.

But we’ll not do that here!

Why?🤔

Well, it’s a good practice to have detection and logic for opening a cell separately.

It adds flexibility to the game!

But how do you separate the detection and logic of opening a cell?🤔

That’s where the concept of `**Callback**` functions come in!



## What is a Callback Function?


---



**Example**: Imagine you're ordering food at a restaurant. 🍔

Instead of waiting for food at the counter, you get a buzzer that will notify you when the food is ready.

Here's how the callback is used in this case:

Food is ready is an `**Event**`

You get a buzzer, which acts as a `**Callback**`.

The buzzer will notify you when your food is ready: **Event Occurs**

You go to the counter to get the food. This is the `**Logic**`** when an event occurs**.



That's exactly how a callback function works in programming!

Let's understand it with an example:

`**Event**`**:** A Cell was clicked.

When the cell is clicked **(Event Occurs)** -> callback function is called**(**`**Callback**`** notifies)** -> `**Logic**`**(function)**



Now, how to implement this in our code?🤔



# Implementing Callback Function


---

In code, the callback function points to another function.

So you need to register a method to the callback function. Register here means that the callback function will point to another function.

Now, when an event occurs(cell was clicked) the registered method let's say `onCellButtonClicked` will get called.

The `onCellButtonClicked` method will have the logic of what happens when a cell is clicked.

This was just a surface-level explanation, you'll understand it in more detail while implementing the callback functionality.



## Setting up the Callback function


---

Let's implement this step by step:

Update `Button.h`

> **Summary📃**
> For all the buttons, you need to add the following:

> 🔸Add a callback function.
> 🔸Initialize the callback function to nullptr
> 🔸`registerCallbackFunction` to register a callback function



`Button.h`

```cpp
//include the functional library
#include <functional>
//previous header files

namespace UIElements {

//previous code

class Button {
private:
	//callback function with a parameter of MouseButtonType
	using CallbackFunction = std::function<void(MouseButtonType)>;
	CallbackFunction callback_function = nullptr;
	//previous code
	
public:
		//previous code
		void registerCallbackFunction(CallbackFunction button_callback);
}
}
```





`Button.h`

```cpp
using CallbackFunction = std::function<void(MouseButtonType)>;
CallbackFunction callback_function = nullptr;
```

What do these lines mean? 🤔

The **first line** defines a function type (`CallbackFunction`) that takes a `MouseButtonType` and returns `void`, 
allowing us to point to any function with this signature:

```cpp
void functionName(MouseButtonType mouse_button)
```

The second line initializes the `callback_function` to a `nullptr`, meaning no function is assigned yet, but we can later set it to dynamically handle mouse button events!



Now, you are ready to implement callback functions 💪🏼

First, we need to **register a callback function** by assigning it to the `callback_function` variable.
This simply means that `callback_function` will **now point to another function**.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/aa6e21cdfeb0992c.png)



`Button.cpp`

```cpp
void Button::registerCallbackFunction(CallbackFunction button_callback) {
    callback_function = button_callback;
}
```

Then, you need to call the `callback_function` when a mouse click is detected:

Update the `handleButtonInteractions` method:

`Button.cpp`

```cpp
void Button::handleButtonInteractions(Event::EventPollingManager& event_manager, const sf::RenderWindow& window) {
    if (event_manager.pressedLeftMouseButton() && isMouseOnSprite(event_manager, window)) {
        callback_function(MouseButtonType::LEFT_MOUSE_BUTTON);
    } 
    else if (event_manager.pressedRightMouseButton() && isMouseOnSprite(event_manager, window)) {
        callback_function(MouseButtonType::RIGHT_MOUSE_BUTTON);
    }
}
```



> **TODO**: 
> ✅ Add the `registerCallbackFunction` method in the `Button` class. 
> ✅ Update the `handleButtonInteractions` implementation in the `Button` class.
> ✅ Run the code to make sure there are no errors



Now, at every frame, Button Clicks(Left/Right) are checked using the `handleButtonInteractions` method.

Whenever the click condition is true, the `callback_function` gets called.

`callback_function` will call the registered method and the logic to open the cell will be implemented.

Now this system can be used for any button that you'll add in the game.



## Implementing Callback for Cells


---

Let's connect our cells to this system.

Where should we implement the logic of opening a cell?🤔 

Let's understand this by looking at the below diagram:



![ ](//outscal.github.io/Full-Stack-Game-Development/images/bea8e4bbbad52be7.png)



Here's how this works:

1. The `handleButtonInteractions` method will check for mouse clicks at every frame.
2. The cell gets clicked.
3. The `callback_function` in the `Button` class gets triggered**.**
4. The cell class will have a method: `cellButtonCallback`, which will be registered to the `callback_function`. 
  Hence `cellButtonCallback` gets called as soon as the `callback_function` is triggered.
5. The `cellButtonCallback` method will call the `onCellButtonClicked` method of the `Board` class.
  The `onCellButtonClicked` method will have the logic of opening a cell.



Let's implement this system 💪🏼

Our `Button` class is already set up.

Now, you just need to update the `Board` and `Cell` classes to complete the `callback` functionality.



Update `Cell.h` and `Board.h` File.

> **Summary📃**
> Here's what is added in the `Cell` class:
> 🔸A method to register a callback function: `registerCellButtonCallback()`
> 🔸And a callback function: `cellButtonCallback()`
> 🔸Forward declared the Board class and created its object.
> 🔸Updated the `Cell` constructor to initialize the board variable.
> 🔸Updated the signature of the `initialize` method
> 🔸Getter function for the cell's postion.



`Cell.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>
#include "../../header/UI/UIElements/Button/Buttons.h"
#include "../../header/Event/EventPollingManager.h"

using namespace UIElements;

namespace Gameplay
{
		class Board;
    class Cell
    {
    private:
				//previous code
				Board* board;
				
        void initialize(float width, float height, sf::Vector2i position, Board* board);
        void registerCellButtonCallback();
        void cellButtonCallback(MouseButtonType button_type);
        
     		//previous code
     		public:
    		Cell(float width, float height, sf::Vector2i position, Board* board);
    		 sf::Vector2i getCellPosition();
    };
}
```



> **Summary📃**
> Here's what is added in the `Board` class:
> 🔸`onCellButtonClicked()` method that gets called when the callback function gets called.



`Board.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>
#include <random>
#include "../../header/GameLoop/Gameplay/Cell.h"
#include "../../header/Event/EventPollingManager.h"
#include "../../header/Sound/SoundManager.h"

namespace Gameplay
{
		
    class Board
    {
    //previous code
    public:
        void onCellButtonClicked(sf::Vector2i cell_position, MouseButtonType mouse_button_type);
    };
}
```





Here are the three must-do things after updating the `Cell.h` and `Board.h` files

1. After updating the header files, you'll need to update the call of the `Cell` constructor as well in the `Board` class.

`Board.cpp`

```cpp
    void Board::createBoard()
    {
        float cell_width = getCellWidthInBoard();
        float cell_height = getCellHeightInBoard();

        for (int row = 0; row < numberOfRows; ++row)
            for (int col = 0; col < numberOfColumns; ++col)
                cell[row][col] = new Cell(cell_width, cell_height, sf::Vector2i(row, col), this); //pass the board as a parameter
    }
```



1. Include the `Board.h` file in the `Cell.cpp` file to avoid the errors:

`Cell.cpp`

```cpp
#include "../../header/GameLoop/Gameplay/Cell.h"
//include board.h file
#include "../../header/GameLoop/Gameplay/Board.h"
#include <iostream>

namespace Gameplay
{
		//previous code
}
```



1. Initialize the board variable in the Cell class:

`Cell.cpp`

```cpp
    Cell::Cell(float width, float height, sf::Vector2i position, Board* board)
    {
        initialize(width, height, position, board);
    }

    void Cell::initialize(float width, float height, sf::Vector2i position, Board* board)
    {
        this->position = position;
        this->board = board; //initialize the board variable
        sf::Vector2f cellScreenPosition = getCellScreenPosition(width, height);
        cell_button = new Button(cell_texture_path, cellScreenPosition, width * slice_count, height);
    }
```





Let's start by calling the `registerCellButtonCallback` function in the initialize function.

And then register the `cellButtonCallback` function:

`Cell.cpp`

```cpp
void Cell::initialize(float width, float height, sf::Vector2i position, Board* board)
{
		this->position = position;
		this->board = board;
		sf::Vector2f cellScreenPosition = getCellScreenPosition(width, height);
		cell_button = new Button(cell_texture_path, cellScreenPosition, width * slice_count, height);
		cuurent_cell_state = CellState::HIDDEN;
		
    registerCellButtonCallback(); //register a method
}

void Cell::registerCellButtonCallback() {
    cell_button->registerCallbackFunction([this](MouseButtonType button_type) {
        cellButtonCallback(button_type);  // Call Cell's own callback logic
    });
}
```



Click here if you didn't understand the `registerCellButtonCallback` method.

This is just the syntax for calling the callback function, if you don’t understand it, don’t worry too much about it. This is not the core focus of this module.



The `Button::registerCallbackFunction` method took a `CallbackFunction` as a parameter.

But here we have passed `this` which is a Cell instance.

Doesn't make sense?!🤨

```cpp
cell_button->registerCallbackFunction([this](MouseButtonType button_type) {
        cellButtonCallback(button_type);  // Call Cell's own callback logic
    });
```

Let me explain:

Method Definition (Expecting a Callback Function)

`Button.cpp`

```cpp
void Button::registerCallbackFunction(CallbackFunction button_callback) {
    callback_function = button_callback;
}
```

- `registerCallbackFunction` method takes a function with a signature:`<void(MouseButtonType)>` as a parameter
- The function which is passed a parameter is stored in the `callback_function`, allowing it to be called later.

Now, nn the `Cell` class, we pass `cellButtonCallback` as the function to be stored inside `registerCallbackFunction`:

```cpp
cell_button->registerCallbackFunction([this](MouseButtonType button_type) {
    cellButtonCallback(button_type);
});
```

- `**[this]**` → Captures the current `Cell` instance so `cellButtonCallback` runs inside it.
- **Lambda function** → Matches the expected function signature (`void(MouseButtonType)`).
- **Stored & Called Later** → `registerCallbackFunction` stores the `cellButtonCallback` function and execute it when needed.





Now, the `cellButtonCallback` method will call the `onCellButtonClicked` method:

`Cell.cpp`

```cpp
void Cell::cellButtonCallback(MouseButtonType button_type) {
    board->onCellButtonClicked(getCellPosition(), button_type);
}
```



Finally, don't forget to implement the getter function: `getCellPosition()`

`Cell.cpp`

```cpp
    sf::Vector2i Cell::getCellPosition() { return position; }    
```



> **TODO**: 
> ✅ Call `registerCellButtonCallback()` in `Cell::intialize()`
> ✅ In `Cell.cpp` implement `registerCellButtonCallback` and `cellButtonCallback` methods.
> ✅Run the code to make sure there are no errors



Finally, let's prepare the Board to handle these events:



`Board.cpp`

```cpp
void Board::onCellButtonClicked(sf::Vector2i cell_position, MouseButtonType mouse_button_type) {
    if (mouse_button_type == MouseButtonType::LEFT_MOUSE_BUTTON) {
        // Left-click logic will be added in the next lesson
    } else if (mouse_button_type == MouseButtonType::RIGHT_MOUSE_BUTTON) {
        // Right-click logic will be added in the next lesson
    }
}
```



> **TODO**: 
> ✅ Add the `onCellButtonClicked` method in the `Board` class.
> ✅Run the code to make sure there are no errors



Now you've successfully:

1. Detected mouse clicks on cells
2. Set up a callback system to handle those clicks
3. Connected everything from Button to Cell to Board



In the next lesson, we'll implement what happens when you actually click a cell!

Get ready to open some cells! 🎮
