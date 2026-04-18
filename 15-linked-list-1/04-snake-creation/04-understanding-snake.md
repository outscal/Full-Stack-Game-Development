**LET'S UNCOVER THE SECRETS OF YOUR SLITHERY FRIEND! 🐍**



So far, you have covered and discovered a few key things about your snake:

- The snake moves in a grid-based system.
- The snake moves in the direction its head is facing.
- Different foods change the snake in different ways.
- Players control the snake's path using keys**.**
- When the snake collides with its body it dies.



Let's explore the entire life of snake! 

From its beginning to its end, you'll discover how it's born, lives, and eventually passes away.

Your snake gets the full human treatment: it’s born, eats, grows, dies, and rises again! 🐍♻️ 

![Image](/Full-Stack-Game-Development/images/8b078e4cdd2ed84a.gif)

***Lifecycle of Human***

Rise Again!?

YES! Because who wants a one-time game? 

Time to outscore your friend! 😎

## **understanding SnakeController                                                                                                                                                                     **


---



`**SnakeController**` manages the behavior and lifecycle of the snake in the game. 

It takes care of everything from processing player inputs, directing the snake's movements, checking for collisions (ouch!), game restarts, etc. 

Its main purpose is to handle all snake-related functionalities to keep the game running smoothly.



Before performing any operation on your snake, it is necessary to check its **state** to see if it is alive or dead.

You need to keep a record of this so that your game stays **updated**.



As the word state suggests, it should be an Enum. So what are you waiting for?



Create an Enum class as `SnakeState` you can do it in your `SnakeController.h` file only


`enum class SnakeState`

```cpp
namespace Player
{
	enum class SnakeState
	{
		ALIVE,
		DEAD,
	};

	class SnakeController
	{
			//... other code
	};
}
```



> **TODO: **`**SnakeController**`** **
> ✅ Create `enum class SnakeState` based on above code in `SnakeController.h`




## Understanding Snakecontroller’s functions


---

To handle the snake's lifecycle, you need to understand some important functions

- `**spawnSnake()**`: To perform any operation on a snake, first, you have to spawn your snake. 
- `**processPlayerInput()**`: To handle all the inputs performed by the Player and process them.
- `**updateSnakeDirection()**`**:** To update snake's direction
- `**moveSnake()**`**: **To handle the movement of the snake.
- `**processSnakeCollision()**`**:** To check and process if any collision happened.
- `**handleRestart()**`**: **To reset the game and respawn your Snake when it is dead.
- **Getter and Setter of **`**SnakeState**`**:** To keep track of the snake's state, you need to create its getter and setter so that it can be accessed and changed in the game.
- `**reset()**`**: **This will be used to set the property values to default. Whenever the game begins or restarts.



> **TODO: **`**SnakeController**`
> ✅ Create a empty method `void spawnSnake()` in `SnakeController` and call it from `spawnPlayer()` method in `PlayerService`
> ✅  Create below properties in `SnakeController.h`:

> `const int initial_snake_length = 10;`
> `SnakeState current_snake_state;`

> ✅ Create the following empty methods:

> `void processPlayerInput()`
> `void updateSnakeDirection()`
> `void moveSnake()` 
> `void processSnakeCollision()`
> `void handleRestart()`
> `void reset()`
> `void respawnSnake()`

> ✅ Create a method `void setSnakeState(SnakeState state)` and inside it, set `current_snake_state = state`
> ✅ Create a method `SnakeState getSnakeState()` and return `current_snake_state`.



Well, to keep your game updated, update the '`**update()**`' method to update your `SnakeController` code! 🤪 

Just updating you on our updating situation!



In the `update()` method, you'll handle different actions depending on whether the current snake snake is `ALIVE` or `DEAD`. 

This will help you implement more detailed functionalities specific to each state of the snake.



> **TODO: **`**SnakeController**`
> ✅ Call `processPlayerInput(), moveSnake(), processSnakeCollision()` when the `current_snake_state = ALIVE` and call `handleRestart()` when `current_snake_state = DEAD` in `update()`





**Click here to see **`spawnPlayer()`in** **`PlayerService````cpp
void PlayerService::spawnPlayer()
{
	snake_controller->spawnSnake();
}
```

**Click here to see **`SnakeController.h`** **```cpp
#pragma once

namespace Player
{
	enum class SnakeState
	{
		ALIVE,
		DEAD,
	};

	class SnakeController
	{
	private:
		const int initial_snake_length = 10;

		SnakeState current_snake_state;

		void processPlayerInput();
		void updateSnakeDirection();
		void moveSnake();
		void processSnakeCollision();
		void handleRestart();
		void reset();
		void destroy();

	public:
		SnakeController();
		~SnakeController();

		void initialize();
		void update();
		void render();

		void spawnSnake();
		void respawnSnake();
		void setSnakeState(SnakeState state);
		SnakeState getSnakeState();
	};
}
```

**Click here to see **`SnakeController.cpp`** **```cpp
#include "Player/SnakeController.h"

namespace Player
{

	SnakeController::SnakeController() { }

	SnakeController::~SnakeController()
	{
		destroy();
	}

	void SnakeController::initialize() { }

	void SnakeController::update()
	{
		switch (current_snake_state)
		{
		case SnakeState::ALIVE:
			processPlayerInput();
			updateSnakeDirection();
			processSnakeCollision();
			moveSnake();
			break;

		case SnakeState::DEAD:
			handleRestart();
			break;
		}
	}

	void SnakeController::render() { }

	void SnakeController::processPlayerInput() { }
	
	void SnakeController::updateSnakeDirection() { }

	void SnakeController::moveSnake() { }

	void SnakeController::processSnakeCollision() { }

	void SnakeController::handleRestart() { }

	void SnakeController::spawnSnake() { }

	void SnakeController::reset() { }

	void SnakeController::respawnSnake() { }

	void SnakeController::setSnakeState(SnakeState state)
	{
		current_snake_state = state;
	}

	SnakeState SnakeController::getSnakeState()
	{
		return current_snake_state;
	}

	void SnakeController::destroy() { }
}
```



Phew, you made it through this section! 

Feeling a bit tired or still full of energy? 



> **🤔FUN TRIVIA: **
> **What word--which shares its name with a popular soda brand--describes a 2D bitmap image, such as a video game character, that's integrated into a larger scene? 🎮**



Click here to check the answerThe word you're looking for is "**Sprite**."



**See you in the next section👋🏼**
