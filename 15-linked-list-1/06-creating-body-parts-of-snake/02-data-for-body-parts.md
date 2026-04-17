## What does a Body Part need?


---

A body part's basic functions are to:

1. Be Visual! How else will you see the snake on screen!?
2. Move! 



**Seeing the Body Part!** 

To see the body part, you can use an `ImageView` and along with that you'll need the dimensions of the body part, i.e. width and height of the image



**Moving the Snake!** 

To move the snake, you need a position on the grid, this can be a `Vector2i` and an `enum Direction`



> **TODO: **`**BodyPart**` 
> ✅ Create the following properties inside `BodyPart`:

> `UI::UIElement::ImageView* bodypart_image`
> `sf::Vector2i grid_position`
> `Direction direction`
> `float bodypart_width`
> `float bodypart_height`



Click here to see `BodyPart.h` 

```cpp
class BodyPart
{
protected:
	UI::UIElement::ImageView* bodypart_image;

	sf::Vector2i grid_position;
	Direction direction;

	float bodypart_width;
	float bodypart_height;
}
```





 In the next chapter, you'll work on creating the `Node` class, that'll be a very quick run!

**See you there!👋🏼**
