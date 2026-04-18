In this lesson, you'll learn how to create, and render a cell.

Since the cell needs to be clickable (for revealing and flagging), it'll use a `Button` class.

So, let’s setup the Button class first!

You already know how to implement the rendering logic, so do this lesson as a speed run 🏃🏼‍➡️



## Creating Button Class


---



For now, the Button class will just be used to render a cell, you’ll create the clickable feature in ***Opening the Cells*** chapter.

Here’s the header file of the `Button` class that you need to create:



Create the `header` and `source` files for `Button` class in the following folder structure:

`header/UI/UIElements/Button/` 

`source/UI/UIElements/Button/`



`Button.h` file

> **Summary📃**
> For all the buttons, you need to add the following:

> 🔸Mouse Button Type enum to track the left or right click.

> 🔸Initialize and render functions for rendering the buttons.

> 🔸Constructor of the Button class.

> 🔸Texture and Sprite for a button.



`Button.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "../../header/Event/EventPollingManager.h"
#include "../../header/Sound/SoundManager.h"
#include <functional>

namespace UIElements {

    enum class MouseButtonType
    {
        LEFT_MOUSE_BUTTON,
        RIGHT_MOUSE_BUTTON
    };
    
    class Button {
    private:
        sf::Texture button_texture;
        sf::Sprite buttonSprite;

        void initialize(const std::string& texture_path, const sf::Vector2f& position, float width, float height);

    public:
        Button(const std::string& texture_path, const sf::Vector2f& position, float width, float height);

        void render(sf::RenderWindow& window) const;
    };
}
```





Reminder⏱️

In the `Button.cpp` file, don't forget to include the `Button.h` file and write the function definitions in the `UIElements` namespace.

`Button.cpp`

```cpp
#include "../../header/UI/UIElements/Button/Button.h"

namespace UIElements 
{
	//Function Definitions
}
```





Now that you have created the `Button.cpp` and `Button.h` files, let's implement the rendering logic:

You have previously implemented the rendering logic for the Board.

Buttons will also be rendered in the same way.

Refer to the rendering of the board and try to implement this on your own.

You can do it 😌



> **PROTIP💡**
> Implement the `Button.cpp` file function by function. One step at a time.** **



> **TODO: **
> **✅** In `header/UI/UIElements/Button/` implement the `Button.h` file. 
> ✅ In `source/UI/UIElements/Button/` implement the `Button.cpp` file.



Click here to see the solution.

> **Summary📃**
> Here's how a button is rendered:

> 🔸Call the `initialize()` method in the constructor of the `Button` class.

> 🔸Initialize the buttonSprite and texture variables in the `initialize()` method.

> 🔸In the `render()` method draw the `buttonSprite`.



`Button.cpp`

```cpp
#include "../../header/UI/UIElements/Button/Button.h"
#include <iostream>

namespace UIElements {

    Button::Button(const std::string& texturePath, const sf::Vector2f& position, float width, float height) {
        initialize(texturePath, position, width, height);
    }

    void Button::initialize(const std::string& texturePath, const sf::Vector2f& position, float width, float height) {
        if (!button_texture.loadFromFile(texturePath)) {
            std::cerr << "Failed to load button texture: " << texturePath << std::endl;
            return;
        }
        buttonSprite.setTexture(button_texture);
        buttonSprite.setPosition(position);
        buttonSprite.setScale(width / button_texture.getSize().x, height / button_texture.getSize().y);
    }

    void Button::render(sf::RenderWindow& window) const {
        window.draw(buttonSprite);
    }
}
```





Now that your button class is ready, it’s time to create the `Cell` class!



# Creating Cell


---



Here’s the `Cell` class that you need to create with all the functions and variables required for rendering a cell:



Create the `header` and `source` files for `Cell` class in the following folder structure:

`header/GameLoop/Gameplay/` 
`source/GameLoop/Gameplay/`



`Cell.h`

> **Summary📃**
> In the Cell.h class, you need to add the following to render a cell:

> 🔸Cell's Dimensions and Position

> 🔸Cell's Texture and an object of the Button class

> 🔸Helper Functions to Initialize the Variables

> 🔸Cell Constructor

> 🔸A Helper Function to Render the Cell



`Cell.h`

```cpp
#pragma once

#include <SFML/Graphics.hpp>
#include "../../header/UI/UIElements/Button/Button.h"
#include "../../header/Event/EventPollingManager.h"

using namespace UIElements;

namespace Gameplay
{
    
    class Cell
    {
    private:
        sf::Vector2i position;

        const int tile_size = 128;
        const int slice_count = 12;
        const std::string cell_texture_path = "assets/textures/cells.jpeg";
        
        Button* cell_button;

        void initialize(float width, float height, sf::Vector2i position);

    public:
        Cell(float width, float height, sf::Vector2i position);
        ~Cell() = default;

        void render(sf::RenderWindow& window);
    };
}

```







Reminder⏱️

In the `Cell.cpp` file, don't forget to include the `Cell.h` file and write the function definitions in the `Gameplay` namespace.

`Cell.cpp`

```cpp
#include "../../header/GameLoop/Gameplay/Cell.h"

namespace Gameplay
{
	//Function Definitions
}
```





Now that we have our `Cell` class defined, let's implement its core functions.



## Implementing Cell Functions


---



Starting with the constructor, the constructor will initialize the cell at a width, height, and position. 

`Cell.cpp`

```cpp
Cell::Cell(float width, float height, sf::Vector2i position)
{
    initialize(width, height, position);
}
```

Then, the `initialize()` function will create an object of the button class and store the cell's position.



**Note: **The constructor of the** **`Button` class needs the float position, hence you need to typecast the position from int to float.

Now as the cell should be clickable, you need to create an object of the button class which will give us the functionality to click our cell in the *Opening Cells* chapter.

`Cell.cpp`

```cpp
void Cell::initialize(float width, float height, sf::Vector2i position)
    {
        this->position = position;
        sf::Vector2f float_position(static_cast<float>(position.x), static_cast<float>(position.y));  //Convert int to float
        cell_button = new Button(cell_texture_path, float_position, width, height);
    }
```

Now, you just need to call the `render` function of the `Button` class in the `render` function of the `Cell` class:

`Cell.cpp`

```cpp
void Cell::render(sf::RenderWindow& window) {
    if (cell_button) cell_button ->render(window);
}
```

Finally, the Board class will create and render a cell.



## Rendering Cells


---



The `Board` class will manage all our cells. Here's how it works:

- For now, let’s create a single-cell (`Cell* cell`) object, later you render all the cells
- Then, initialize the cell object in a new `createBoard` function.
- Lastly, render the object that you have created(`cell->render()`)



Updated `Board.h` file.

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
        Cell* cell;

				//previous code

        void createBoard();

    public:
				//previous code

    };
}

```





Now, to render the cell, you need to:

1. Call the `createBoard()` in `initialize()` function.
2. Allocate a new `Cell` object with specific dimensions and position in the `createBoard()` function.
3. Call the render function of the Cell class in the render function of the Board class.



`Board.cpp`

```cpp
void Board::initialize() {
    initializeBoardImage();
    createBoard(); //Call Create Board method:
}

void Board::createBoard() {
    cell = new Cell(83, 83, sf::Vector2i(0, 0));
}

void Board::render(sf::RenderWindow& window)
{
		window.draw(boardSprite);
    cell->render(window);   //Render the cell     
}

```

**Note:** Don’t worry about the hardcoded cell size value. In the *Setting Cell Size* lesson, you’ll use a dynamic method to set it.



> **TODO**: 
> ✅ In `header/GameLoop/Gameplay/` create and implement the `Cell.h` file. 
> ✅ In `source/GameLoop/Gameplay/` create and implement the `Cell.cpp` file.
> 
> In `Board.h` 
> ✅Create a pointer object(`cell`) of the `Cell` class
> ✅Declare a `createBoard` function.
> In `Board.cpp`
> ✅Call the `createBoard` function in the `initialize` function.
> ✅Initialize the cell object in the `createBoard` function.
> ✅In the `render` function call the `render` function of the `Cell` class.



**Was the output something like this?**



![ ](//outscal.github.io/Full-Stack-Game-Development/images/e88b4131f5c37c65.png)



**What just happened?**

**Why does this cell texture look weird?**



## **Understanding Cell Texture**


---

![ ](//outscal.github.io/Full-Stack-Game-Development/images/d87a712125da19ee.png)

**CELL TEXTURE**

This is the cell texture. The cell is a square in shape. But this texture is definitely not square. This texture contains **12 different values of cells**.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/b9ae323737cdab71.png)

**LABELLED**



All types of cell images are included in a single texture.

The number of cells in the texture are 12, so you need to multiply the width of the texture by 12(`slice_count`) to render the entire texture.

Update the initialization of the `cell_button`:

`Cell.cpp`

```cpp
void Cell::initialize(float width, float height, sf::Vector2i position)
{
    this->position = position;
    sf::Vector2f float_position(static_cast<float>(position.x), static_cast<float>(position.y));     
    cell_button = new Button(cell_texture_path, float_position, width * slice_count, height); // multiply width by slice count
}
```



> **TODO**: `Cell.cpp` 
> ✅In `initialize()` method, update the initialization of `cell_button` by multiplying width with slice count.



**Try playing the game!**

**You will again see something interesting, we'll discuss it in the next lesson 👋**
