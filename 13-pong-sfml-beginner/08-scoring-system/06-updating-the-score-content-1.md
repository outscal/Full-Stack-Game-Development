Remember our nicely formatted scores from before?

```text
Player 1: 03  vs  Player 2: 12
```

Now we have the display ready, but when should these scores update? 🤔

Think about it:

- Ball moves left, who scores?
- Ball moves right, who scores?
- How do we track these movements?



## Tracking Out-of-Bounds State


---



Let's track where your ball goes out! First, let's think:

When does Player 1 score?

- When ball hits right boundary
- We need to track right collisions
- Then update Player 1's score

When does Player 2 score?

- When ball hits left boundary
- We need to track left collisions
- Then update Player 2's score

First, let's track left boundary hits:



Click here to see the updated `Ball.h`

`Ball.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "../../Header/Gameplay/Paddle/Paddle.h"
#include "../../Header/Utility/TimeService.h"

using namespace sf;
using namespace std;
using namespace Utility;

namespace Gameplay
{
    //previous code

    class Ball
    {
    private:
        //previous code

        bool had_left_collison = false;
        bool had_right_collison = false;

        //previous code

    public:

        Ball();

        bool isLeftCollisionOccurred();
        void updateLeftCollisionState(bool value);

        bool isRightCollisionOccurred();
        void updateRightCollisionState(bool value);

       //previous code
    };
}
```





`Ball.cpp`

```cpp
bool Ball::isLeftCollisionOccurred() {
    return had_left_collison;
}

void Ball::updateLeftCollisionState(bool value) {
    had_left_collison = value;
}
```

You have already implemented a function for handling out of bounds collision.

Now, you just need to update the left collision state.

`Ball.cpp`

```cpp
void Ball::handleOutofBoundCollision()
{
    FloatRect ball_bounds = pong_ball_sprite.getGlobalBounds();

    // Check for out-of-bounds on the left or right boundary
    if (ball_bounds.left <= left_boundary)
    {
        updateLeftCollisionState(true);
        reset();
    }
    else if (ball_bounds.left + ball_bounds.width >= right_boundary)
    {
        //set right boundary to true
        reset();
    }
}
```



> **TODO**: `Ball.cpp` 
> ✅Implement `bool isLeftCollisionOccurred()` and `void updateLeftCollisionState(bool value)` function. 
> ✅Implement `bool isRightCollisionOccurred()` and `void updateRightCollisionState(bool value)` function. 
> ✅Update the `handleOutofBoundCollision()` function.



Click here to see the solution.

`Ball.cpp`

```cpp
bool Ball::isRightCollisionOccurred() {
    return had_right_collison;
}

void Ball::updateRightCollisionState(bool value) {
    had_right_collison = value;
}
```

`Ball.cpp`

```cpp
void Ball::handleOutofBoundCollision()
{
    FloatRect ball_bounds = pong_ball_sprite.getGlobalBounds();

    // Check for out-of-bounds on the left or right boundary
    if (ball_bounds.left <= left_boundary)
    {
        updateLeftCollisionState(true);
        reset();
    }
    else if (ball_bounds.left + ball_bounds.width >= right_boundary)
    {
        updateRightCollisionState(true);
        reset();
    }
}
```







You now have a way to track the side of out-of-bounds collision!

Next, you just need to update the score and reset the round in this way!



## Making Scoring Work


---



Now comes the exciting part - actually updating those scores!

Think about the flow:

1. Ball goes out left → Player 2 scores
2. Ball goes out right → Player 1 scores
3. Reset player positions for the next round

This is pretty straight forward, let's implement this logic:

`GameplayManager.cpp`

```cpp
void GameplayManager::UpdateScore() {
    // Left side out - Player 2 scores!
    if (ball->isLeftCollisionOccurred()) {
        ui_service->incrementPlayer2Score();
        ball->updateLeftCollisionState(false);
        resetPlayers();  // You'll implement it next
    }

    // Right side out - Player 1 scores!
    if (ball->isRightCollisionOccurred()) {
        ui_service->incrementPlayer1Score();
        ball->updateRightCollisionState(false);
        resetPlayers();  // You'll implement it next
    }
}
```

You already have the positions of player 1 and player 2, using which you can just reset the players!



> 🎮 **FACT**: The original Pong by Atari didn't reset paddle positions after scoring - this made the game more challenging!



`GameplayManager.cpp`

```cpp
void GameplayManager::resetPlayers() {
    player1->reset(player1_position_x, player1_position_y);
    player2->reset(player2_postion_x, player2_postion_y);
}
```

Lastly, you need to call the `UpdateScore()` method and update the text on game window using `UIService`

`GameplayManager.cpp`

```cpp
void GameplayManager::update() {
    //rest of the code
    UpdateScore();       // Check for scoring events
    ui_service->update(); // Update score display
}

void GameplayManager::render(RenderWindow* game_window) {
    //previous code
    ui_service->render(game_window); // Show those beautiful scores!
}
```



> **TODO**: `Ball.cpp` 
> ✅Implement `void UpdateScore()` and `void resetPlayers()` functions. 
> ✅Update the `update()` and `render()` functions. 
> ✅Test the score update!



You have a complete UI ready!!!

Next up: Making your game sound as good as it looks with a sound system! 🎶
