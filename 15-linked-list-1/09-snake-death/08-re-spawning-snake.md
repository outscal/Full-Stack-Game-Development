![Handling Snake Death](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_04_2024__14_14_30.png)

**Handling death in **`**SnakeController**`



Let's look at this diagram carefully...

very... very... carefully



Did you notice `restart_duration`?

Of course, you did!



See, you can't just restart the game immediately after the player dies, they need time to process the tragic loss of their snake.



So here is what you are going to do when Snake dies:

1. You stop the snake movement
2. You Start a restart timer
3. When the timer ends, you reset the snake and the game restarts



Basically, death should trigger the **restarting** process.



Here is the function call tree: 

![Snake Death Function Call Tree](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_20_2024__11_12_52.png)

**Snake Death Function Call Tree**



## Resetting the snake


---

Before resetting all variables, let's create the variables needed for the reset timer



> **TODO: **`**SnakeController**` 
> ✅ Create 		`const float restart_duration = 2.f`



Cool, now you can reset everything

But what?

What all properties will you need to reset in `SnakeController` so it goes back to its original state?



Think! Think and implement!

Of course, you can just see the code below, but before that just try to think on your own.

Whenever you get an opportunity to come up with solutions on your own, you should utilise those opportunities.



> **TODO: **`**SnakeController**` 
> ✅ Create and implement `void SnakeController::reset()`



Click here to see `reset()`: DON'T OPEN 🚫 WITHOUT TRYING YOURSELF

```cpp
void SnakeController::reset()
{
	current_snake_state = SnakeState::ALIVE;
	current_snake_direction = default_direction;
	elapsed_duration = 0.f;
	restart_counter = 0.f;
}
```



 

## Respawning the Snake


---

You have a dead snake on your screen, what will you do to re-spawn the snake?

Well, first you need to delete the old snake by removing all nodes, remove the waste from the screen

Then you'll have to reset the properties 

and at the end spawn a new snake! 



> **TODO: **`**SnakeController**` 
> ✅ Create and implement `void SnakeController::respawn()`



Click here to see `respawn()`: DON'T OPEN 🚫 WITHOUT TRYING YOURSELF

```cpp
void SnakeController::respawnSnake()
{
	single_linked_list->removeAllNodes();
	reset();
	spawnSnake();
}
```



 

## Handling Restart Timer


---

Again, nothing new. You are a champ at this

You have to create a timer and whenever it reaches `restart_duration` you call `respawnSnake()` 



> **TODO: **`**SnakeController**` 
> ✅ Create and implement `void SnakeController::handleRestart()` 
> ✅ Call it inside `update()` when Snake is `DEAD`



Click here to see `handleRestart()`: DON'T OPEN 🚫 WITHOUT TRYING YOURSELF

```cpp
void SnakeController::handleRestart()
{
	restart_counter += ServiceLocator::getInstance()->getTimeService()->getDeltaTime();

	if (restart_counter >= restart_duration)
	{
		respawnSnake();
	}
}
```






---



The snake is reborn...

But life needs balance...

So in the next chapter, there shall be obstacles
