One of the main responsibilities of `SnakeController` is keeping the snake moving in the correct direction and quickly changing direction whenever the player hits the keys.


Let's give power to the Player through code to control Snake.🎮

But how would it be possible?? 


## Understanding Movement


---



![Image](https://media.discordapp.net/attachments/823251706044481619/1236758306312290455/image.png?ex=66392c6e&is=6637daee&hm=d285a683d52c8be3dc3c69007e6e4746f28535030ee658a9c9343231658a571a&=&format=webp&quality=lossless)

![Image](//outscal.github.io/Full-Stack-Game-Development/images/e06221819cc6d89d.png)



Have a look at the above picture. 

Any comments? 💬

The direction your snake's head moves, its whole body will follow that direction only.

If you know the position and direction of the Head, it will be easy for you to find the position and direction of the rest of the body because they are all connected.



The direction of the snake is dependent on the player's input.

Whatever input the player gives, the snake's head will update it and pass the knowledge to the rest of the body frame by frame.

However, to determine which direction the player wants the snake to move, you must store the current direction of the snake and update it according to the Player's Input.


For that you have to create `enum class Direction`, as the name suggests, is an enum that describes the snake's direction. 


`enum class Direction`

```cpp
namespace Player
{
	enum class Direction
	{
		UP,
		DOWN,
		LEFT,
		RIGHT,
	};
}
```



> **TODO: **
> **SnakeController**
> ✅  Create below properties in `SnakeController.h`:
> `const sf::Vector2i default_position = sf::Vector2i(25, 13);`
> `const Direction default_direction = Direction::RIGHT;`
> `Direction current_snake_direction;`
> 
> **Direction**
> ✅ Create `Direction.h` in `include/Player`  
> ✅ Create `enum class Direction` inside it



**Click here to see **`SnakeController.h`** **```cpp
#pragma once
#include <SFML/System/Vector2.hpp>

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

		const sf::Vector2i default_position = sf::Vector2i(25, 13);
		const Direction default_direction = Direction::RIGHT;

		SnakeState current_snake_state;
		Direction current_snake_direction;

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



That's all for this section...

Are you ready for some more chit-chat ahead? 


**See you in the next section 👋**
