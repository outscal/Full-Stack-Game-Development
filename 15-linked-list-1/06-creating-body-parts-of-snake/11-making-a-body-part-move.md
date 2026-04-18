Alright alright alright



I just got to know you are about to create the foundation for Snake Movement in `BodyPart` 

Let me be the Old Saint and guide you!



![Old Game Dev Saint](//outscal.github.io/Full-Stack-Game-Development/images/a3d0b74fa8e3c48f.png)

***Old Game Dev Saint***



You see, the snake is always moving. There is an old saying in the land of snakes...

> ***"If it lives, it moves"***
> ***- ***Old Snake Saint



To follow this saying, you have to make sure that the snake's position changes on every frame

The snake should move in the direction of user input!



## Calculating BodyPart's Next Position


---

![Position on Grid](//outscal.github.io/Full-Stack-Game-Development/images/2fa84711cf194192.png)

`**BodyPart**`**'s position on Grid**



If the Body Part is at the Grid Position = (x,y) and it is moving to the Left then the next grid position will be (x-1,y) 

Similarly, you can refer to the above image to know how the next position will be calculated using the current position and direction



Since there are 4 directions, then you need to create functions to calculate next position in all 4 directions.

You can create 4 different functions to return next position in each direction and then call them in a parent function `getNextPosition()` 



![Function Tree for getNextPosition()](//outscal.github.io/Full-Stack-Game-Development/images/d54c6cd689d76e80.png)

**Function hierarchy for **`**getNextPosition()**`



In the above function hierarchy, `getNextPosition()` will call its helper functions depending on the direction



For example: `getNextPositionLeft()` should look like this: 

```cpp
sf::Vector2i BodyPart::getNextPositionLeft()
{
	return sf::Vector2i(grid_position.x - 1, grid_position.y);
}
```



But before you jump on implementing all other functions, you need to take care of something...

Take a guess, what can go wrong in calculating the next position?



Think think, I'm not telling you the answer

If you can figure out and solve the problem then great!

Otherwise we'll fix it in upcoming chapters after you are actually able to move the snake



> **TODO: **`**BodyPart**`** **
> ✅ Implement `sf::Vector2i getNextPositionUp()`, `sf::Vector2i getNextPositionDown()`, `sf::Vector2i getNextPositionLeft()`, `sf::Vector2i getNextPositionRight()`. Refer to the above code for reference 
> ✅ Create `sf::Vector2i getNextPosition()` and call all 4 questions based on the value of `direction`. Use `switch-case` for it



Click here to see all 5 functions

```cpp
sf::Vector2i BodyPart::getNextPosition()
{
	switch (direction)
	{
	case Direction::UP:
		return getNextPositionUp();
	case Direction::DOWN:
		return getNextPositionDown();
	case Direction::RIGHT:
		return getNextPositionRight();
	case Direction::LEFT:
		return getNextPositionLeft();
	default:
		return grid_position;
	}
}

sf::Vector2i BodyPart::getNextPositionDown()
{
	return sf::Vector2i(grid_position.x, grid_position.y + 1);
}

sf::Vector2i BodyPart::getNextPositionUp()
{
	return sf::Vector2i(grid_position.x, grid_position.y - 1);
}

sf::Vector2i BodyPart::getNextPositionRight()
{
	return sf::Vector2i(grid_position.x + 1, grid_position.y);
}

sf::Vector2i BodyPart::getNextPositionLeft()
{
	return sf::Vector2i(grid_position.x - 1, grid_position.y);
}
```



**⚠️ WARNING!:** The above code has some issues. If you can figure them out and solve them here, that'll be great! We'll solve them in future chapters anyway.



## UPdating Direction


---

Let's create a simple setter function.



> **TODO: **`**BodyPart**`** **
> ✅ Create `void BodyPart::setPosition(sf::Vector2i position)` that sets the value of `direction`



Create here to see `BodyPart`'s `setPosition()` 

```cpp
void BodyPart::setPosition(sf::Vector2i position)
{
	grid_position = position;
}
```





## Updating Position


---

To update the position, you need to calculate the `BodyPart`'s screen position and then update `bodypart_image`'s position and rotation and then call its `update()` 

```cpp
void BodyPart::updatePosition()
{
	bodypart_image->setPosition(getBodyPartScreenPosition());
	bodypart_image->setRotation(getRotationAngle());
	bodypart_image->update();
}
```



Last thing, your position and direction are stored in `BodyPart`, but other classes might also need them in the future, so let's create getter functions for both `direction` and `grid_position` 



> **TODO: **`**BodyPart**`** **
> **✅**Create and implement `void BodyPart::updatePosition()` like in above code
> ✅Create getter `Direction getDirection()` and `sf::Vector2i getPosition()` that return `direction` and `grid_position` respectively
