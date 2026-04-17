To change the direction, you need Input from the user and you have `EventService` to register input from the user

These functions from `EventService` will help you know when the input buttons are pressed

`**EventService.cpp**`

```cpp
 namespace Event
 {
	 class EventService()
	 {
		 //... some other code
		 bool EventService::pressedLeftArrowKey()
	
		 bool EventService::pressedRightArrowKey()

		 bool EventService::pressedUpArrowKey()

		 bool EventService::pressedDownArrowKey()
	 //... some other code
	 }
 }
 
```



## How to act on input


---

Well, to change the direction of the snake, you have to update the value of `current_snake_direction` 

To move left, the user will press the left arrow key and the `current_snake_direction` will be set to `Direction::LEFT` 

The same thing will happen when moving in all directions.



But what if the user presses the Left Arrow key while the snake moves to the right?

This will require a 180° turn, and our snake can only take 90° turns

So you have to keep a check for this!



All this movement logic will be implemented inside `SnakeController` as it is responsible for controlling the entire snake



> **TODO: **`**SnakeController**`** **
> ✅ Inside `processPlayerInput()`, use `EventService` to check for Key Presses and update the `current_snake_direction` according to the logic discussed above

Click here to see `SnakeController`'s `processPlayerInput()` 

```cpp
void SnakeController::processPlayerInput()
{
	EventService* event_service = ServiceLocator::getInstance()->getEventService();

	if (event_service->pressedUpArrowKey() && current_snake_direction != Direction::DOWN)
	{
		current_snake_direction = Direction::UP;
	}
	else if (event_service->pressedDownArrowKey() && current_snake_direction != Direction::UP)
	{
		current_snake_direction = Direction::DOWN;
	}
	else if (event_service->pressedLeftArrowKey() && current_snake_direction != Direction::RIGHT)
	{
		current_snake_direction = Direction::LEFT;
	}
	else if (event_service->pressedRightArrowKey() && current_snake_direction != Direction::LEFT)
	{
		current_snake_direction = Direction::RIGHT;
	}
}
```





Well, well, now you can take input and `moveSnake()` is already created.

What are you waiting for? Now go and move your snake wherever you want!
