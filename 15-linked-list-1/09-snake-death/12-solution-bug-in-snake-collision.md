I hope you have implemented the solution yourself!

Don't even dare to see these solutions before trying the solution yourself!



`SnakeController.h` 

```cpp
//.... other code
enum class InputState
{
	WAITING,
	PROCESSING
};

class SnakeController
{
	//.... other code
	InputState current_input_state;
	//.... other code
}
```





`SnakeController::processPlayerInput()` 

```cpp
void SnakeController::processPlayerInput()
{
	if (current_input_state == InputState::PROCESSING)
		return;

	EventService* event_service = ServiceLocator::getInstance()->getEventService();

	if (event_service->pressedUpArrowKey() && current_snake_direction != Direction::DOWN)
	{
		current_snake_direction = Direction::UP;
		current_input_state = InputState::PROCESSING;
	}
	else if (event_service->pressedDownArrowKey() && current_snake_direction != Direction::UP)
	{
		current_snake_direction = Direction::DOWN;
		current_input_state = InputState::PROCESSING;
	}
	else if (event_service->pressedLeftArrowKey() && current_snake_direction != Direction::RIGHT)
	{
		current_snake_direction = Direction::LEFT;
		current_input_state = InputState::PROCESSING;
	}
	else if (event_service->pressedRightArrowKey() && current_snake_direction != Direction::LEFT)
	{
		current_snake_direction = Direction::RIGHT;
		current_input_state = InputState::PROCESSING;
	}
}
```





`SnakeController::delayedUpdate()` 

```cpp
void SnakeController::delayedUpdate()
{
	elapsed_duration += ServiceLocator::getInstance()->getTimeService()->getDeltaTime();

	if (elapsed_duration >= movement_frame_duration)
	{
		elapsed_duration = 0.f;
		updateSnakeDirection();
		processSnakeCollision();

		if(current_snake_state != SnakeState::DEAD)
			moveSnake();
		
		current_input_state = InputState::WAITING;
	}
}
```





`SnakeController::reset()` 

```cpp
void SnakeController::reset()
{
	current_snake_state = SnakeState::ALIVE;
	current_snake_direction = default_direction;
	elapsed_duration = 0.f;
	restart_counter = 0.f;
	current_input_state = InputState::WAITING;
}
```





Now GO!

**Enjoy a bug free Snake Ride!**
