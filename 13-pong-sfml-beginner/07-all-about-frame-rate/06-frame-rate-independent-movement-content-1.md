Let’s directly start the implementation!

Firstly, the gameplay manager needs to initialize and update the delta time.

`GameplayManager.h`

```cpp
TimeService* time_service;
```

`GameplayManager.cpp`

```cpp
GameplayManager::GameplayManager(EventManager* manager)
{
 		time_service = new TimeService()
    time_service->initialize();// Start our time tracking
    //previous code
}

void GameplayManager::update()
{
    time_service->update();
    //previous code
}
```

**Note**:

- You need to update the declaration(pass the time_service as a parameter) of the `update()` and **movement methods** in the ball and paddle class as they’ll need to access the `time_service` object.

After this, you are ready to make the movement frame rate independent.



## Paddle Movement


---

Now, you just need to multiply the delta time with paddle speed to make the movement frame rate independent.

Here's how:

`Paddle.cpp`

```cpp
void Paddle::movePaddle(bool move_up_key_pressed, bool move_down_key_pressed, TimeService* time_service)
{
	if (move_up_key_pressed && paddle_sprite.getPosition().y > topBoundary)
	{
		paddle_sprite.move(0, -paddleSpeed * time_service->getDeltaTime() * speedMultiplier);
	}
	if (move_down_key_pressed && paddle_sprite.getPosition().y + paddle_sprite.getSize().y < bottomBoundary)
	{
		paddle_sprite.move(0, paddleSpeed * time_service->getDeltaTime() * speedMultiplier);
	}
}
```

**Note**: You can add a `int speedMultiplier = 10` as delta time significantly decreases the paddle speed.



## Ball Movement


---

Ball movement is no different:

`Ball.cpp`

```cpp
void Ball::move(TimeService* time_service)
{
        pong_ball_sprite.move(velocity * time_service->getDeltaTime() * speed_multiplier);
}
```



> **TODO** 
> ✅Update `GameplayManager` with `TimeService` 
> ✅Modify Paddle movement to use delta time 
> ✅Modify Ball movement to use delta time 
> ✅Play the game



The movement is fair for all devices now!

But, do you see a problem in the ball movement?🤔

The ball starts its movement as soon as the game window opens, players will not have the time to react to the ball’s movement.

You can fix this by adding a delay before the ball starts moving.



## Adding Initial Delay


---



How to add the initial delay?

You can use the `TimeService` to do this!

To do this, you’ll need a new variable to keep track of the delay time(`float elapsed_delay_time`).

Then, you can keep on adding the delta time to it at every frame(implement a new function for this): `updateDelayTime(float delta_time)`

Initially, the ball will not move, and the ball will start moving when the `elapsed_delay_time` reaches a certain delay(`float delay_duration`).

Let’s say the `delay_duration` is 2, then the ball will not move until delta time is 2, no matter how many frames are completed during this duration.

But how will you control the movement of the ball?🤔

You can use enum(`BallState`) to create states(`Idle`,`Moving`) to handle this!



> **TODO** 
> In `Ball.h` 
> ✅Add `float elapsed_delay_time` and `float delay_duration` 
> ✅Add `void updateDelayTime(float delta_time)` method. 
> ✅Add a `BallState` enum with `Idle` and `Moving` states.
> ✅Add a variable `BallState current_state`
> 
> In `Ball.cpp` 
> ✅Initialize the `current_state` to IDLE.
> ✅Implement `void updateDelayTime(float delta_time)` method.
> ✅Update the `void move(TimeService* timeService)` method.



Click here to see the solution.

`Ball.h`

```cpp
namespace Gameplay{
enum class BallState
{
    Idle,
    Moving
};

class Ball{
private:
//previous code
float delay_duration = 2.0f;
float elapsed_delay_time = 0.0f;

BallState current_state;

void move(TimeService* timeService);
void updateDelayTime(float deltaTime);

public:
void update(Paddle* player1, Paddle* player2, TimeService* timeService);
//previous code
```



`Ball.cpp`

```cpp
   void Ball::initializeVariables()
   {
   //previous code
   		current_state = BallState::Idle;
   }
   
   void Ball::move(TimeService* timeService)
    {
        updateDelayTime(timeService->getDeltaTime());
				//PREVIOUS CODE
    }
    
    void Ball::updateDelayTime(float deltaTime)
    {
        if (current_state == BallState::Idle)
        {
            elapsed_delay_time += deltaTime;
            if (elapsed_delay_time >= delay_duration)
            {
                current_state = BallState::Moving;
            }
            else
            {
                return;
            }
        }
    }
```





Movement is now complete💪🏼

Your game is close to complete!

You now need to display the scores!
