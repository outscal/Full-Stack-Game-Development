Handling the collision can be divided into three parts

1. Ball hitting paddles (The core gameplay!)
2. Ball hitting top/bottom (Keeping the ball in play)
3. Ball going out of bounds(Left and Right boundaries) (Scoring!)

Let’s start with the ball and paddle collision!



## Making the Ball Bounce Off Paddles


---



Here’s how you can implement this step by step:

Update the `Paddle.h` file:



Click here to see the `Paddle.h` file.

`Paddle.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
using namespace sf;

namespace Gameplay
{
	class Paddle
	{
	private:
		RectangleShape paddle_sprite;

		const float paddle_width = 20.0f;
		const float paddle_height = 140.0f;

		float paddleSpeed = 0.8f;
		float topBoundary = 20.0f;
		float bottomBoundary = 700.0f;

		void createPaddle(float position_x, float position_y);
		void movePaddle(bool move_up_key_pressed, bool move_down_key_pressed);

	public:
		Paddle(float position_x, float position_y);

		RectangleShape getPaddleSprite();
		void reset(float position_x, float position_y);

		void update(bool move_up_key_pressed, bool move_down_key_pressed);
		void render(RenderWindow* game_window);
	};
}
```





First, you need the getter for paddle sprite:

`Paddle.cpp`

```cpp
RectangleShape Paddle::getPaddleSprite()
{
    return paddle_sprite;
}
```

Now, in the ball class, you can add a new function to handle the collision with paddles. (`void handlePaddleCollision(Paddle* player1, Paddle* player2)`)

Here’s how this function looks!

`Ball.cpp`

```cpp
void Ball::handlePaddleCollision(Paddle* player1, Paddle* player2)
{
    // 1. Get our sprites
    const RectangleShape& player1Paddle = player1->getPaddleSprite();
    const RectangleShape& player2Paddle = player2->getPaddleSprite();

    // 2. Check their bounds
    FloatRect ball_bounds = pong_ball_sprite.getGlobalBounds();
    FloatRect player1_bounds = player1Paddle.getGlobalBounds();
    FloatRect player2_bounds = player2Paddle.getGlobalBounds();

    // 3. Handle collisions
    if (ball_bounds.intersects(player1_bounds) && velocity.x < 0)
    {
        velocity.x = -velocity.x;  // Bounce!
    }
    if (ball_bounds.intersects(player2_bounds) && velocity.x > 0)
		{
		    velocity.x = -velocity.x;  // Reverse horizontal direction
		}
}
```

Reading the function and variable names, you can understand what’s happening in this function.

But, do you know how it is really working?🤔

Don’t worry! I’ll explain how these functions work!

Think about it:

- Objects have positions
- Objects have sizes
- Objects can overlap

SFML uses two functions to handle this: `getGlobalBounds()` and `intersects()`

*How does SFML measure where things are?*

`Ball.cpp`

```cpp
FloatRect ball_bounds = pong_ball_sprite.getGlobalBounds();
```

`getGlobalBounds()` gives you four crucial measurements:

- `ball_bounds.left` → X coordinate of the top left corner 
- `ball_bounds.top` → Y coordinate of the top left corner
- `ball_bounds.width` → How wide the box is
- `ball_bounds.height` → How tall the box is

Notice that there are no other coordinates(top-right, bottom-left and bottom-right)!

Why?🤔

Well, you just need the top-left coordinate, and then you can just use the width and height to calculate the rest of the points!

Top-Right: (Left+Width, Top)

Bottom-Left: (Left, Top+Height)

Bottom-Right: (Left+Width, Top+Height)

But, there's a catch!

Let's understand it with an example:
Suppose, that the ball is at (Left**:10**, Top**:** **15**) position in the game window, and the width and height of the sprite are **30** and **25**, respectively.

Then, this is how the global bounds are calculated:



![ ](//outscal.github.io/Full-Stack-Game-Development/images/f2a3c50ea0de4973.png)

**Ball Bounds**

Points **included** in global bounds:

**Top-Left: **(Left, Top): **(10, 15)**

**Top-Right**: (Left+Width, Top): (10 + 29.9, 15) = **(39.9, 15)**

**Bottom-Left**: (Left, Top+Height): (10, 15 + 24.9) = **(10, 39.9)**

**Bottom-Right**: (Left+Width, Top+Height): (10 + 29.9, 15 + 24.9) = **(39.9, 39.9)**

Any points beyond the included points are excluded!

Why?🤔

That's because sprites and shapes use a `**FloatRect**`** **! For precision, SFML excludes the last point of the rectangle.



Now comes the fun part: *How do we know when objects collide?*

SFML's `intersects()` function answers one simple question: "Do these two boxes share any space/area?"

Look at these scenarios:

![ ](//outscal.github.io/Full-Stack-Game-Development/images/d19a168226ae4560.png)

**Intersection**



> 💡**PROTIP**: 
> Objects must share an area to intersect- just touching at one point or even multiple points(edge) aren't enough!



Now, you need to check:

- If the ball **intersects **with the paddle

**AND**

- If the ball is moving towards the paddle

If both these conditions are true, reverse the velocity direction in the x-axis!

`Ball.cpp`

```cpp
		if (ball_bounds.intersects(player1_bounds) && velocity.x < 0)
    {
        velocity.x = -velocity.x;  // Bounce!
    }
    if (ball_bounds.intersects(player2_bounds) && velocity.x > 0)
		{
		    velocity.x = -velocity.x;  // Reverse horizontal direction
		}
```

**Note: **Checking the velocity is important for consistent collision behavior. If you remove the check, collision will work fine, but sometimes the ball might stick to the wall! Trust me I have faced this issue🥹



> **TODO** 
> ✅In `Ball.cpp` implement `void handlePaddleCollision(Paddle* player1, Paddle* player2)`



You have the ball and paddle collision ready!!

Now, let’s understand how you can handle the collision between top and bottom boundaries!



## Keeping the Ball in Play


---



*What should happen when the ball hits the top or bottom?*

Think about it:

It’s no different from the paddle collision!

**OR**

You can compare the Y-Coordinate of the top-left point and the positions of the top and bottom boundaries instead.

Here's how you can do it:

**Note:**

You'll need these variables in the `Ball.h` file:

`Ball.h`

```cpp
        const float top_boundary = 20.0f;
        const float bottom_boundary = 700.0f;
```

These are the exact positions in pixels that can be used to compare the ball's bounds.

1. Compare the Y-coordinate of the top-left point of the ball with the `top_boundary` 
  **AND** 
  if the ball is moving towards the top boundary(velocity in y axis < 0)
2. Compare the Y-coordinate of the bottom-left corner with the `bottom_boundary`
  **AND**
  if the ball is moving towards the bottom boundary(velocity in y axis > 0)

If **either** of the above conditions are true, the ball has collided with the boundaries(top or bottom), and it needs to go in the opposite direction.

`Ball.cpp`

```cpp
void Ball::handleBoudaryCollision()
{
    FloatRect ball_bounds = pong_ball_sprite.getGlobalBounds();

    if ((ball_bounds.top <= top_boundary && velocity.y < 0) ||
        (ball_bounds.top + ball_bounds.height >= bottom_boundary && velocity.y > 0))
    {
        velocity.y = -velocity.y;  // Reverse vertical direction
    }
}
```

Next is the left and right boundary collision(out of bounds)



## Out of Bounds Collision


---



What happens when the ball goes out of bounds?🤔

If the ball goes out of bounds on the left side, then player 2(right paddle) scores a point.

And vice versa.

Then, the ball comes back in the middle, and the next round starts!

Currently, there’s no way to keep track of the score, for now let’s just reset the ball position to middle.

Here's how you can implement this:

Just like the top and bottom boundaries, you must also check the collision with the left and right boundaries!

`Ball.h`

```cpp
        const float left_boundary = 0.0f;
        const float right_boundary = 1280.0f; 
        
        //Center Position
        const float center_position_x= 615.0f;
        const float center_position_y= 325.0f;
```

Now, just like the top and bottom boundaries, compare the ball bounds with the left and right boundary

`Ball.cpp`

```cpp
void Ball::handleOutofBoundCollision()
{
    FloatRect ball_bounds = pong_ball_sprite.getGlobalBounds();

    if (ball_bounds.left <= left_boundary)
    {
        reset();        // Player 2 scores!
    }
    else if (ball_bounds.left + ball_bounds.width >= right_boundary)
    {
        reset();        // Player 1 scores!
    }
}

void Ball::reset()
{
    pong_ball_sprite.setPosition(center_position_x, center_position_y);
    velocity = Vector2f(ball_speed, ball_speed);
}

```



> **TODO: **`**Ball.cpp**` 
> ✅Implement `void handleBoudaryCollision()` 
> ✅Implement `void handleOutofBoundCollision()` 
> ✅Implement `void reset()`



The ball collision is complete!!

Now, you need all these pieces to work together:

`Ball.cpp`

```cpp
void Ball::update(Paddle* player1, Paddle* player2)
{
    move();
    onCollision(player1, player2);
}

void Ball::onCollision(Paddle* player1, Paddle* player2)
{
    handleBoudaryCollision();
    handlePaddleCollision(player1, player2);
    handleOutofBoundCollision();
}
```

**Note: **You'll need to update the `Ball::update()`'s definition and function call to avoid errors.



> **TODO** 
> ✅Implement the `onCollision()` method. 
> ✅Update the `Ball::update()` function. 
> ✅Test all collision types.



You have successfully implemented collision in your game!!🥳

There’s still a problem though🤔

```cpp
The paddles can still go out of bounds!!
```

Let’s fix that 💪🏼



## Adding Paddle Constraints


---



Lastly, you just need to add constraints to the paddle’s movement, just like the ball collision with top and bottom boundaries.

`Paddle.cpp`

```cpp
void Paddle::movePaddle(bool move_up_key_pressed, bool move_down_key_pressed)
{
	if (move_up_key_pressed && paddle_sprite.getPosition().y > topBoundary)
	{
		paddle_sprite.move(0, -paddleSpeed);
	}
	if (move_down_key_pressed && paddle_sprite.getPosition().y + paddle_sprite.getSize().y < bottomBoundary)
	{
		paddle_sprite.move(0, paddleSpeed);
	}
}
```



> **TODO: **`**Paddle.cpp**` 
> ✅Update `void movePaddle()`



Now, you have a complete gameplay ready!!

In the next chapter, you’ll learn frame rates and how they affect the movement of paddles and the ball!
