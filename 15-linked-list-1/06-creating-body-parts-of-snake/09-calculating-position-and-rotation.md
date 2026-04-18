The body part is placed on a grid and you have got its position on the grid:  `grid_position` 


You need to convert this grid position into the screen's position, i.e. pixel position.



## CALCULATING Screen Position


---

**Drawing the body part at index (0,0):** 

If you set: `bodypart_image->setPosition(sf::Vector2f(0,0))`  

Then, the body part will be drawn at the top-left corner of the screen with only some part of it visible



![BodyPart at (0,0)](/Full-Stack-Game-Development/images/10e048648a3621f2.png)

`**BodyPart**`** at screen **`**(0,0)**`



If you want to draw the image at (0,0) of the grid, 

then you just **CAN'T** use: `bodypart_image->setPosition(0,0)`. This will draw the image at the corner

To draw the image on grid's (0,0), you'll have to add border offsets and image's half width and height



The code for this will look like:

```cpp
sf::Vector2f BodyPart::getBodyPartScreenPosition()
{
	float x_screen_position = LevelView::border_offset_left + (grid_position.x * bodypart_width) + (bodypart_width / 2);
	float y_screen_position = LevelView::border_offset_top + (grid_position.y * bodypart_height) + (bodypart_height / 2);

	return sf::Vector2f(x_screen_position, y_screen_position);
}
```



> **TODO: **`**BodyPart**` 
> ✅ Create `sf::Vector2f::getBodyPartScreenPosition()` as above



## Updating Rotation


---



![OG Snake Rotating like CRAZY](/Full-Stack-Game-Development/images/75c42a9da235ecbb.gif)

***OG snake rotating like crazy***



See! The snake needs to rotate!

Go help it!



![Rotation Angles of BodyPart](/Full-Stack-Game-Development/images/4f974c7ed60b5202.png)

**Rotation Angles of **`**BodyPart**`** **



You need to rotate the snake based on the above angels. 

You need to update the rotation angle based on the direction.



> **TODO: **`**BodyPart**` 
> ✅ Create `float BodyPart::getRotationAngle()` 
> ✅ Inside it, use a `switch-case` to return the angle based on the direction. Refer to the above image for the Direction-Angle relation



Click here to see `BodyPart`'s `getRotationAngle()` 

```cpp
float BodyPart::getRotationAngle()
{
	switch (direction)
	{
	case Direction::UP:
		return 270.f;
	case Direction::DOWN:
		return 90.f;
	case Direction::RIGHT:
		return 0;
	case Direction::LEFT:
		return 180.f;
	}
}
```





Now you just need to use this function to set `bodypart_image`'s rotation



## Updating Direction


---

The direction depends on user input, so it'll be updated by some other class.

You can create a function to set the direction

> **TODO: **`**BodyPart**` 
> ✅ Create `public void BodyPart::setDirection(Direction direction)` that updates the direction



Click here to see `BodyPart`'s `setDirection()` 

```cpp
void BodyPart::setDirection(Direction direction)
{
	this->direction = direction;
}
```





## Updating Position and Rotation


---

All you have to do now is just use all the functions you calculated to set `BodyPart`'s position and rotation'



```cpp
void BodyPart::updatePosition()
{
	bodypart_image->setPosition(getBodyPartScreenPosition());
	bodypart_image->setRotation(getRotationAngle());
	bodypart_image->update();
}
```



> **TODO: **`**BodyPart**` 
> ✅ Create and  Implement `updatePosition()` like in the above code



Good going so far

In the next section, you'll start developing the foundation to move the snake.

**See you there!👋🏼 **
