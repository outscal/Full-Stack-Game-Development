**You have the cell's data, it's time to use it to slice the texture!**

In this lesson, you'll slice the whole texture to render a single cell on the game window.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_13_2025__12_28_30.png)

**Cell State** and **Cell Value**



Before slicing the cells you need to understand how the texture depends on Cell State and Value/Type.

**Let's understand this with some examples:**

- When will texture show *'6'*? Cell State = OPEN & Cell Value = SIX
- When will texture show *'Mine'*? Cell State = OPEN & Cell Value = MINE
- When will the texture show the Flag? Cell State = FLAGGED & Cell Value = any
- When will texture show Hidden? Cell State = HIDDEN & Cell Value = any
- When will the texture show Empty? Cell State = OPEN & Cell Value = EMPTY

These examples show that the **Cell State gets the priority in deciding the texture** because it decides whether to Open a cell or not.

This hierarchy is explained in the diagram:



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_13_2025__12_28_56.png)

**Cell STATE-VALUE Map**



*Doesn't this diagram resemble a *`*switch-case*`* statement?*

Before implementing, you need to figure out how to slice a specific portion from the long texture.

Here's a detailed explanation:




<iframe src="https://www.loom.com/embed/8ecdf138d05c4fcabfa317205a4781bb" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



You'll use the `setTextureRect` function to crop a specific portion of the texture:

`setTextureRect` is an SFML method to set a rectangle on a texture as shown in the video. 

Only the part in that rectangle you set using the `setTextureRect` method will be rendered on the game window.



Now, how to implement the `setTextureRect` method?🤔

Well, for that you need to set a rectangle on the `buttonSprite` in the `Button` class.



Update `Button.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "../../header/Event/EventPollingManager.h"
#include "../../header/Sound/SoundManager.h"

namespace UIElements {

    //previous code

    class Button {
    //previous code

    public:
       //previous code

        void setTextureRect(const sf::IntRect& rect);
        //previous code
    };
}



```





`Button.cpp`

```cpp
void Button::setTextureRect(const sf::IntRect& rect) {
		//Set a rectangle on the texture
    buttonSprite.setTextureRect(rect);
}
```



> **PROTIP**💡 
> `void sf::Sprite::setTextureRect(const IntRect& rectangle)`: 
> Sets the sub-rectangle of the texture that the sprite will display.
> The texture rect is useful when you don't want to display the whole texture, 
> but rather a part of it. By default, the texture rect covers the entire texture.



Notice that `rect` object in the parameter of the `setTextureRect` method?🤔

You might think that,

How are the dimensions of the rectangle decided?

Well, to define the dimensions of the rectangle, you need to understand the constructor of the `IntRect` class.



## **Understanding **`**IntRect::Rect()**`** **


---

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_13_2025__12_30_02.png)



To define the dimensions of a rectangle, we need the **Top-Left coordinates** + **Width **and **Height**.



**CALCULATING Width and Height**

The width and height is as straightforward as it sounds.

It is the width and height of the rectangle.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/03_01_2025__12_56_30.png)

**Cells Texture's Properties**



For the `cell_texture`, you know that the height of a cell is `128` pixels, and since the cell is a square, the width of a single cell will also be 128 Pixels.

**Note: **`1536` is the width of the whole `cells` texture(`128 * 12`)



Now, how to calculate the Top-Left coordinates?🤔



**CALCULATING COORDINATES**



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/02_19_2025__06_42_21.png)

**Dimension of an Empty Cell**



For the first image, which is of an `EMPTY` cell, the coordinates will be `(0,0)`

And, the width and height of the texture are `128` Pixels.

Now, for the rest of the cells, you just need to change the position of the rectangle on the x-axis(Left coordinate).

The rest of the dimensions, Top coordinate, width, and height remain the same.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/02_19_2025__06_44_46.png)

**Dimensions of the '*****4*****' Cell**



For Example, the cell indicating the number ***'4'*** ⇒ **Top = 0** and **Left = 4 * **`**tile_size**`

Because the tile indicating ***"4"*** has 4 tiles before it with each tile's width being `tile_size`.



Now that you have understood slicing, let's implement it in the `Cell` class.

You need a new helper function: `setCellTexture` in the `Cell` class for slicing the cell texture.



> **TODO**
> ✅In `Cell.h` add a `public`  `void setCellTexture()` method.



Now, let's implement the `setCellTexture()` method of the Cell class.



# Implementing Texture Slicing


---



Now, to implement slicing we need to set a rectangle on the `cell_button`.

Before setting the rectangle, let's list down the dimensions that are common for all the cells:

1. **Top coordinate: 0**
2. **Width: 128 Pixels**
3. **Height: 128 Pixels**

The **left coordinate** is the only value that we need to change.

Now, you have 12 cells, will you use a switch case for all 12 cells?

or is there a smarter approach ?🤔

There is a smarter approach.



## Handling OPEN cells


---

Let's start with the Cells in `OPEN` state:



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/02_15_2025__14_14_11.png)



Notice that when the cell is in the `OPEN` state, 
the order of the cells in the `CellType` enum is the same as the texture.

So, to get the index of the `OPEN` cells, 
you can just typecast the `cell_type` value into an integer.

Is there a way to convert an enum value into an integer?

Obviously, there is. Here's how you can convert an enum value into an integer:

`Cell.cpp`

```cpp
void Cell::setCellTexture()
{
    int index = static_cast<int>(cell_type);
}
```



Now for all the `OPEN` cells, you can set the **left coordinate** by just multiplying the `index` variable and `tile_size` and the rest of the dimensions(`Top-coordinate`, `width` and `height`) remain fixed as discussed in the** **[**video**](https://www.loom.com/share/8ecdf138d05c4fcabfa317205a4781bb?sid=5852b976-e863-426b-93e6-7eb7ff6f2e71) earlier in this lesson:

`Cell.cpp`

```cpp
void Cell::setCellTexture()
{
    int index = static_cast<int>(cell_type);

    switch (current_cell_state)
    {
    //OPEN state
    case CellState::OPEN:
        cell_button->setTextureRect(sf::IntRect(index * tile_size, 0, tile_size, tile_size));
        break;
    }
 }
```

We reduced 10 lines of code into just a single line by handling all the cells in the `OPEN` state in a single line! 💪🏼

`OPEN` cells are now correctly handled 😌



## Handling FLAGGED and HIDDEN Cells


---

Now, you need to handle the `FLAGGED` and `HIDDEN` states. 

Here's how you can do this:

For a `HIDDEN` cell, you need to set the Left coordinate to `10 * tile_size` as it is in the 11th position and has 10 Cells before it.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/02_19_2025__07_02_15.png)



`Cell.cpp`

```cpp
void Cell::setCellTexture()
{
    int index = static_cast<int>(cell_type);

    switch (current_cell_state)
    {
    //OPEN state
    case CellState::OPEN:
        cell_button->setTextureRect(sf::IntRect(index * tile_size, 0, tile_size, tile_size));
        break;
        
    //HIDDEN STATE
    case CellState::HIDDEN:
        cell_button->setTextureRect(sf::IntRect(10 * tile_size, 0, tile_size, tile_size));
        break;
    }
}
```



Then, you need to set the texture for the FLAGGED cell:

As it is in the 12th position and has 11 cells before it, its left coordinate will be `tile_size * 11`



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/02_19_2025__07_05_42.png)



`Cell.cpp`

```cpp
    void Cell::setCellTexture()
    {
        int index = static_cast<int>(cell_type);

        switch (current_cell_state)
        {
	        //OPEN state
		    case CellState::OPEN:
		        cell_button->setTextureRect(sf::IntRect(index * tile_size, 0, tile_size, tile_size));
		        break;
	    	//HIDDEN STATE
		    case CellState::HIDDEN:
		        cell_button->setTextureRect(sf::IntRect(10 * tile_size, 0, tile_size, tile_size));
		        break;
        //FLAGGED state
        case CellState::FLAGGED:
            cell_button->setTextureRect(sf::IntRect(11 * tile_size, 0, tile_size, tile_size));
            break;
        }
    }
```



**Note: **Currently, we are not changing the `CellState` or `CellType` anywhere. Hence the CellState is set to `HIDDEN` by default. You'll change it in the ***Opening Cells*** chapter.



The `setCellTexture` method is ready!

Lastly, you just need to call the `setCellTexture` method before rendering the `cell_button`.



> **TODO**
> ✅In `Cell.cpp` implement the `setCellTexture()` method
> ✅In the `Cell::render` method call the `setCellTexture()` method before `cell_button->render()`



Click here to see the solution.

> **Summary📃**

> Here's what is added in the `Cell.cpp` file:

> 🔸Slicing of cell based on cell's state and type.
> 🔸Set the cell's texture before rendering the cell.



`Cell.cpp`

```cpp
void Cell::setCellTexture()
{
    int index = static_cast<int>(cell_type);

    switch (current_cell_state)
    {
    case CellState::HIDDEN:
        cell_button->setTextureRect(sf::IntRect(10 * tile_size, 0, tile_size, tile_size));
        break;
    case CellState::OPEN:
        cell_button->setTextureRect(sf::IntRect(index * tile_size, 0, tile_size, tile_size));
        break;
    case CellState::FLAGGED:
        cell_button->setTextureRect(sf::IntRect(11 * tile_size, 0, tile_size, tile_size));
        break;
    }
}

void Cell::render(sf::RenderWindow& window)
{
		//set cell's texture
    setCellTexture();
    
    //render the cell button
    if (cell_button)
        cell_button->render(window);
}
```



Click Here to see the expected output!

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_13_2025__12_32_43.png)





Now you have a perfect-looking cell, you just need to move it to the correct position.

**See you in the next lesson 👋**
