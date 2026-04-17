*Your static Pong elements are about to come alive.*



## Moving the Ball


---



*How would you make something move in a 2D space?*

Think about it:

- To move up/down → Change in Y position.
- To move left/right → Change in X position.
- To move diagonally → Change in both X and Y



## The Ball's Velocity


---

Let's give our ball some speed:

`Ball.h`

```cpp
private:
    float ball_speed = .5f;
    Vector2f velocity = Vector2f(ball_speed, ball_speed);
```

*Why use Vector2f?*

- We need two values (x and y)
- The movement should be smooth (hence float)

Now, you need to move the ball using velocity.

`Ball.h`

```cpp
private:
	void move();
```



Now, let's implement these functions!💪🏼



## Making the Ball Move


---

Now for the fun part:

`Ball.cpp`

```cpp
void Ball::move()
{
    pong_ball_sprite.move(velocity);
}
```

The `move` method updates the ball’s position by adding its velocity to its current position!

*That's it?* Yes! SFML makes it that simple.

Lastly, you just need to keep adding the position at every frame:

`Ball.cpp`

```cpp
void Ball::update()
{
    move();
}
```



> **TODO** 
> ✅Add velocity to `Ball.h` 
> ✅Implement `move()` in `Ball.cpp` 
> ✅Add movement logic in `update()`



Now, to move the ball, you need to call the `Ball::update()` in `GameplayManager::update()`



> **TODO** 
> ✅In GameplayManager::update() call Ball::update()
> ✅Play the game.



The ball movement is ready!💪🏼

Time to move the paddles!



## Moving the Paddles


---



*How should paddles respond to player input?*

Think about controls:

- Player 1: W (up) and S (down)
- Player 2: Up and Down arrows

Think about what happens when a player presses a key:

*How much should the paddle move?*

- We need a speed value
- A `movePaddle`method

Add this to your paddle class:

`Paddle.h`

```cpp
private:
    const float paddleSpeed = 0.5f;
    
    void movePaddle(bool move_up_key_pressed, bool move_down_key_pressed);
    
public:
		void update(bool move_up_key_pressed, bool move_down_key_pressed);
```

*How do we handle the actual movement?*

Think about it:

1. Check if 'up' key is pressed
2. - Move paddle up
3. Check if 'down' key is pressed
4. - Move paddle down



`Paddle.cpp`

```cpp
void Paddle::movePaddle(bool move_up_key_pressed, bool move_down_key_pressed)
{
		//move up
    if (move_up_key_pressed)
    {
        paddle_sprite.move(0, -paddleSpeed);
    }
    //move down
    if (move_down_key_pressed)
    {
        paddle_sprite.move(0, paddleSpeed);
    }
}
```

*Notice something interesting?*

- Moving up → Negative Y
- Moving down → Positive Y



> 💡 **PROTIP**: 
> In SFML, (0,0) is at the top-left corner. Moving up means decreasing Y! unlike the usual coordinate system!



**Updating Movement at every frame**

Note: You must update the `update()` method’s declaration in the `Paddle.h` file.

`Paddle.cpp`

```cpp
void Paddle::update(bool move_up_key_pressed, bool move_down_key_pressed)
{
    movePaddle(move_up_key_pressed, move_down_key_pressed);
}
```



> **TODO** 
> ✅Implement paddle movement in `Paddle.cpp` 
> ✅Call `movePaddle` in `update()`



Movement logic for paddles is also done!

Lastly, you need to call the `Paddle::update()` method of the ball and paddle classes in the Gameplay Manager.

**Note: **You need `EventManager`'s `isKeyPressed` method to pass it in Paddle's `update` method. You can do it by passing the `EventManager` as a parameter in the `GameplayManager` constructor.

`GameLoop.cpp`

```cpp
void GameLoop::initialize()
{
	//previous code
	gameplay_manager = new GameplayManager(event_manager);

	//previous code
}

```

`GameplayManager.h`

```cpp
class GameplayManager
{
private:
	//previous code
	EventManager* event_manager;

public:
	GameplayManager(EventManager* manager);
	//previous code
};

```

`GameplayManager.cpp`

```cpp
GameplayManager::GameplayManager(EventManager* manager)
{
	event_manager = manager;
}

void GameplayManager::update()
{
    //previous code
    player1->update(event_manager->isKeyPressed(Keyboard::W),
                    event_manager->isKeyPressed(Keyboard::S));
    player2->update(event_manager->isKeyPressed(Keyboard::Up),
                    event_manager->isKeyPressed(Keyboard::Down));
}
```



> **TODO** 
> ✅Update `GameplayManager::update()` 
> ✅Play the game.



Your Paddles are moving!🥳 



But there's a problem: *What happens when the ball or paddles reach the screen edges?*

Next lesson, you'll add boundaries in the game window!
