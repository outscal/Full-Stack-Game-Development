![Snake Moving Fast](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_20_2024__07_50_51.gif)



Ayo! Where is that snake going!?

Someone stop it!

Why is it in such a hurry?

Slow it down!



## Why is The Snake moving so fast?


---

You are updating the direction and position of the snake on every frame, and the frame rate is very high!

That is why the snake is moving so fast!

Now what should you do?



If you were not using a grid then you could have decreased the distance it travels per frame. But since you are using a grid-based movement,  it moves 1 frame at a time.



How about you do NOT update the snake on every frame?



Rather than updating on every frame you could update it after a particular interval.



This will give you control over the speed of the snake.

 

Let's call this feature `**delayedUpdate()**` 



## How will `**delayedUpdate()**` work?


---

You can use `deltaTime` from `TimeService` for this



It works like a normal timer, where you keep adding `deltaTime` and when it reaches a certain limit you call the delayed features and then reset the timer.



> **TODO: **`SnakeController.h`**   **
> ✅ Create `const float movement_frame_duration = 0.1f` 
> ✅ Create `void delayedUpdate()` and write the logic to call certain features after `movement_frame_duration` time is completed and then reset the timer
> ✅ Call `delayedUpdate()` inside `update()` when the snake is `ALIVE`



Click here to see how `SnakeController.h` should look

```cpp
void SnakeController::delayedUpdate()
{
	elapsed_duration += ServiceLocator::getInstance()->getTimeService()->getDeltaTime();

	if (elapsed_duration >= movement_frame_duration)
	{
		elapsed_duration = 0.f;
		//Code to be called after a delay
	}
}
```





Now you have move your logic to `delayedUpdate()` 

```cpp
void SnakeController::delayedUpdate()
{
	elapsed_duration += ServiceLocator::getInstance()->getTimeService()->getDeltaTime();

	if (elapsed_duration >= movement_frame_duration)
	{
		elapsed_duration = 0.f;
		updateSnakeDirection();
		processSnakeCollision();
		moveSnake();
	}
}
```



> **TODO: **`SnakeController`
> ✅ Implement `delayedUpdate()` like in above code



Why did you move `processSnakeCollision()`?

Well, you only need to check for collisions once the snake moves to a new position. So, there is no point in calling it inside the normal `update()`.




> ***"We optimise the code wherever we can!😎" ***
