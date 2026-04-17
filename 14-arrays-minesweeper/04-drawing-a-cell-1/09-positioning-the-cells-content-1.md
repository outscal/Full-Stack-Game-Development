In this lesson, you'll position the cell on the board.

But how to position the cell?🤔



## positioning the cell


---

You have to move the cell from the screen's origin *(0,0)* to the board's top-left. 

A Straightforward approach is to create *offset*s for both width and height and add to the current cell's position.



> 📖🎮**Game Dev Dictionary**
> **Offset:** *"an offset is a numerical value that represents a displacement or difference from a particular reference point or position."*



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/02_09_2024__05_40_45.png)

**Cell Offset**



`Cell.h`** **

```cpp
private:
const float cell_top_offset = 274.f;
const float cell_left_offset = 583.f;
```

You can use these values to set the position of the cell and place it in the perfect spot.



> **TODO: **`**Cell.cpp**`
> ✅ Create these properties in the `Cell.h` file:
> `const float cell_top_offset = 274.f`
> `const float cell_left_offset = 583.f`
> ✅In the `Cell.h` create `private` a function `sf::Vector2f getCellScreenPosition() const` 
> ✅Use `getCellScreenPosition()` to set the position while initializing the button.



Click here to see the solution.

**NOTE: **Previously, in `initialize()` function, you typecasted integer value to float value. Now, you can directly pass the left and top offsets.



`Cell.cpp`

```cpp
void Cell::initialize(float width, float height, sf::Vector2i position)
{
    this->position = position;
    //Get cell position
    sf::Vector2f cellScreenPosition = getCellScreenPosition();
    cell_button = new Button(cell_texture_path, cellScreenPosition, width * slice_count, height);
}

sf::Vector2f Cell::getCellScreenPosition() const
{
    float xScreenPosition = cell_left_offset;
    float yScreenPosition = cell_top_offset;
    return sf::Vector2f(xScreenPosition, yScreenPosition);
}
```





Expected Output.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/01_13_2025__12_43_55.png)







You have a perfect cell now! right?

Well almost.

**You have an interesting thing left to implement,** **we'll discuss it in the next lesson👋**
