![Game Dev Monk](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_27_2024__12_32_34.png)



> **Peace...**
> **Inner Peace...🧘🏼**



It is time to rethink the code you wrote earlier

It is **time to REFACTOR!**



## Why and What to Refactor?


---

```cpp
void SnakeController::processSnakeCollision()
	{
		if (single_linked_list->processNodeCollision())
		{
			current_snake_state = SnakeState::DEAD;
		}
	}
```

This is your current logic for handling collisions inside the snake



But right now, the snake only collides with itself, it literally passes through food and obstacles!

You need to fix it and to fix it you need to do some minor refactoring in `SnakeController`.



Fixing means, creating a structure that supports collision detection for all objects in the game.

1. Snake's Body
2. Elements
3. Food



This new structure handles all kind of collisions

![Collision Detection Flow](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__09_31_38.png)

***Collision Detection Flow***



> **TODO: **`**SnakeController**`** **
> ✅ Create the following empty functions:

> `void processBodyCollision()`
> `void processElementsCollision()`
> `void processFoodCollision()`
> ✅ Shift the logic for Snake-to-Snake collision from `processSnakeCollision()` to `processBodyCollision()` and play Death sound using `SoundService`
> ✅ Call the newly created functions inside `processSnakeCollision()`





Click here to see how the code should look for the above-mentioned functions

```cpp
void SnakeController::processSnakeCollision()
{
	processBodyCollision();
	processElementsCollision();
	processFoodCollision();
}

void SnakeController::processBodyCollision()
{
	if (single_linked_list->processNodeCollision())
	{
		current_snake_state = SnakeState::DEAD;
		ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::DEATH);
	}
}

void SnakeController::processElementsCollision()
{
}

void SnakeController::processFoodCollision()
{
}
```





**Here is a fun brain exercise!**

> **🧠THINK!**
> Why are we checking for collisions inside `SnakeController` and not individually inside each object?
