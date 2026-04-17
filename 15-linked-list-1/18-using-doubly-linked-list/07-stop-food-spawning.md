The project is almost done!

All the features are implemented!

There is just a teeny tiny feature that you need to implement!



See, right now, once the Food Spawning starts, it doesn't stop even after the player is dead, you need to implement it!



## Implementing Food Spawn Stop


---

Inside `FoodService`'s `handleFoodSpawning()` you need to exit the function if the player is dead.

The flow to achieve this is very simple:

1. `FoodService` will ask `PlayerService` if the Player is dead
2. `PlayerService` will ask the `SnakeController` if the Snake is dead
3. `SnakeController` will inform if the snake is dead



> **TODO**
> ✅ In `SnakeController`: Create `bool SnakeController::isSnakeDead()`, inside it returns true if the snake is dead
> ✅ In `PlayerService`: Create `bool PlayerService::isPlayerDead()`, inside it return if the player is dead using `SnakeController::isSnakeDead()` 
> ✅ In `FoodService`: inside `handleFoodSpawning()` exit the function if the player is dead. Check this using `PlayerService`'s `isPlayerDead()`



Click here to see the above-discussed functions

**SnakeController**

```cpp
bool SnakeController::isSnakeDead()
{
	return current_snake_state == SnakeState::DEAD;
}
```



**PlayerService**

```cpp
bool PlayerService::isPlayerDead()
{
	return snake_controller->isSnakeDead();
}
```



**FoodService**

```cpp
 void FoodService::handleFoodSpawning()
 {
 	if (ServiceLocator::getInstance()->getPlayerService()->isPlayerDead()) return;

	if (elapsed_duration >= spawn_duration)
	{
		destroyFood();
		reset();
		spawnFood();
	}
}
```
