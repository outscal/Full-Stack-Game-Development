In this lesson, you'll create the core gameplay elements of Pong using basic shapes.

Let's think about Pong's most basic elements:

- A ball bouncing around
- Two paddles moving up and down

Now, here's an interesting question: *How would you represent these elements in the simplest way possible?*

The answer is surprisingly simple:

- Ball → Circle
- Paddle → Rectangle



> 💡 **PROTIP**: 
> Great game developers start with the simplest solution and build complexity only when needed.



So, let’s see how you can create a ball!



## Creating the Ball


---



Before writing any code, let's brainstorm:

*What properties does our ball need?*

Think about it:

- Shape type for rendering? (`CircleShape`)
- Size? (`radius`)
- Starting position in pixels? (x, y coordinates)

Let's build it step by step.



Click here to see the folder structure.

![ ](/Full-Stack-Game-Development/images/8cae9b683b7d48e7.png)

**Folder Structure**





**The Ball Header File**

First, include the necessary SFML graphics library:

`Ball.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
using namespace sf;
```

**Properties of the Ball**

Now, define what makes a ball a ball:

Add all the properties discussed earlier in this lesson:

`Ball.h`

```cpp
namespace Gameplay
{
    class Ball
    {
    private:
        CircleShape ball_sprite;
		    const float radius = 10.0f;
		    const float position_x = 615.0f;
		    const float position_y = 335.0f
    };
}
```



> 💡**PROTIP**: 
> Using `const` for values that shouldn't change makes your code more robust and easier to maintain.



**Ball’s Lifecycle functions**

Finally, let's add the constructor and the lifecycle functions:

`Ball.h`

```cpp
namespace Gameplay
{
    class Ball
    {
    //previous code
			public:
		    Ball();
		    void update();
		    void render(RenderWindow* game_window);
    };
}
```

Why might we need an update function even though the ball isn't moving yet?

Obviously, you’ll add the movement logic in the future. But, for now, let’s see how you can render the ball!



## Rendering the Ball


---



First, you need to initialize the ball to the defined radius and position:

`Ball.cpp`

```cpp
Ball::Ball()
{
    ball_sprite.setRadius(radius);
    ball_sprite.setPosition(position_x, position_y);
}
```

Then, draw the ball in the game window:

`Ball.cpp`

```cpp
void Ball::render(RenderWindow* game_window)
{
    game_window->draw(ball_sprite);
}
```



> **TODO **
> **✅** In `Header/Gameplay/Ball` folder create the `Ball.h` file. 
> **✅** In `Source/Gameplay/Ball` folder create the `Ball.cpp` file. 
> ✅ Implement the `Ball.h` and `Ball.cpp` files.



You have written the logic to render the ball!

Now, you need to write the rendering logic for paddles!



## Creating the Paddles


---



Now that we have ball, let's create the paddles that will try to keep it in play.

*What makes a paddle different from a ball in terms of properties?*

Let's break it down step by step.



**Properties of the Paddle**

Now, let's define what makes a paddle a paddle:

`Paddle.h`

```cpp
class Paddle
{
private:
    RectangleShape paddle_sprite;

    const float paddle_width = 20.0f;
    const float paddle_height = 140.0f;
```



*Think about it: Why did we choose these specific dimensions? What would happen if we made the paddle wider or taller?*



> 💡 **PROTIP**: 
> Game design is all about balance. A paddle that's too tall makes the game too easy, while one that's too short might make it frustratingly difficult.



**Paddle’s Lifecycle Function**

Then, the lifecycle functions of the paddle!

`Paddle.h`

```cpp
public:
    Paddle(float position_x, float position_y);
    void update();
    void render(RenderWindow* game_window);
```



Now, just like the ball, the rendering of the paddles!



## Rendering the Paddle


---



Time to bring our paddles to life! Let's start with the constructor:

`Paddle.cpp`

```cpp
Paddle::Paddle(float position_x, float position_y)
{
    paddle_sprite.setSize(Vector2f(paddle_width, paddle_height));
    paddle_sprite.setPosition(position_x, position_y);
}
```

Just like the ball, render the paddle:

`Paddle.cpp`

```cpp
void Paddle::render(RenderWindow* game_window)
{
    game_window->draw(paddle_sprite);
}
```

Notice something interesting? Unlike the `Ball` class, the Paddle constructor takes position parameters.

*Why do you think we did this differently from the Ball?*

Think about it:

- The ball always starts in the center
- But paddles need to be on opposite sides of the screen
- Each paddle needs its own unique position



> **TODO **
> **✅** In `Header/Gameplay/Paddle` folder create the `Paddle.h` file. 
> **✅** In `Source/Gameplay/Paddle` folder create the `Paddle.cpp` file. 
> ✅ Implement the `Paddle.h` and `Paddle.cpp` files.



Rendering logic for paddles is complete!

But, who will handle the ball’s rendering and other logic?

`GameLoop`? No.

Why? 🤔

`GameLoop`’s responsibility is to handle the overall flow of the game.

Ball is a part of the gameplay. Hence, it should be handled by a `GameplayManager`



> **TODO **
> **✅** In `Header/Gameplay` folder create the `GameplayManager.h` file. 
> **✅** In `Source/Gameplay` folder create the `GameplayManager.cpp` file.



## Setting Up the Gameplay Manager


---



First, you need to include the gameplay elements:

`GameplayManager.h`

```cpp
#pragma once
#include "Paddle/Paddle.h"
#include "Ball/Ball.h"

namespace Gameplay
{
	class GameplayManager
	{
			//data members
	};
}
```

Now, let's think about paddle positioning:

`GameplayManager.h`

```cpp
private:
    float player1_position_x = 40.0f;
    float player1_position_y = 300.0f;

    float player2_postion_x = 1210.0f;
    float player2_postion_y = 300.0f;
```

*Why these specific positions? How would different positions affect gameplay?*

These positions are at the center of the left and right edge of the game window. You'll see it when you render the paddles and ball later in this lesson.

Let's create the paddle objects:

`GameplayManager.h`

```cpp
    Ball* ball;
    Paddle* player1;
    Paddle* player2;
```

Then, you need the lifecycle functions:

`GameplayManager.h`

```cpp
private:
	void initialize();

public:
	GameplayManager();
	void update();
	void render(RenderWindow* game_window);
```



Then, you must implement the logic to render the paddles and the ball.



## Rendering Paddles and Ball


---

Initialize the paddles and ball objects:

`GameplayManager.cpp`

```cpp
GameplayManager::GameplayManager() {
	initialize();
}

void GameplayManager::initialize() {
	ball = new Ball();
	player1 = new Paddle(player1_position_x, player1_position_y);
	player2 = new Paddle(player2_postion_x, player2_postion_y);
}
```

Lastly, rendering the paddles and the ball:

`GameplayManager.cpp`

```cpp
void GameplayManager::render(RenderWindow* game_window)
{
    ball->render(game_window);
    player1->render(game_window);
    player2->render(game_window);
}
```



> **TODO** 
> ✅Implement the `GameplayManager.h` and `GameplayManager.cpp` files. 
> ✅Run the code to test the rendering.



What happened? Nothing rendered?🤔

Why? That’s because `GameplayManager::render` is not being called anywhere!



> **TODO** 
> ✅ Create and initialize an object of the `GameplayManager` in the `GameLoop` class. 
> ✅ Call the `GameplayManager::render` function in `GameLoop::render`



Click here to see the solution.`GameLoop.h`

`GameLoop.h`

```cpp
//other header files
#include "../../Header/Gameplay/GameplayManager.h"

//other namespaces
using namespace Gameplay;

namespace Core
{
	class GameLoop
	{
	private:
		//other objects
		GameplayManager* gameplay_manager;
		
		//previous code
	}
}

```

`GameLoop.cpp````cpp
namespace Core
{
	void GameLoop::initialize()
	{
		//other objects
		gameplay_manager = new GameplayManager();
	}
	
	void GameLoop::render()
	{
		game_window_manager->clearGameWindow();
		//render the paddles and ball
		gameplay_manager->render(game_window_manager->getGameWindow());
		
		game_window_manager->displayGameWindow();
	}
}
```







You have rendered graphics for the first time💪🏼

Take a moment to appreciate what you've accomplished😌

But this is just the beginning.

In the next lesson, you’ll make the ball look more realistic!
