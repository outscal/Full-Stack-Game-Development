Let's discuss an important issue: **frame rate dependency**.

In our current implementation, assume that the ball moves 100 pixels per frame.(For easier calculations)

This seems fine at first, but it can lead to inconsistent behavior across different devices or under varying performance conditions.

Why?🤔 
Because the number of frames per second (FPS) can vary:

- A powerful computer might run your game at 120 FPS
- A slower device might only manage 30 FPS
- FPS can even fluctuate during gameplay on the same device

This means that on a faster device, the ball will move much faster than on a slower device!

Let's illustrate this: Suppose, the ball speed is 100 pixels per frame:

At 60 FPS:

- **Over one second: 100 * 60 = 6000 pixels!**

At 30 FPS:

- **Over one second: 100 * 30 = 3000 pixels!**

At 120 FPS:

- **Over one second: 100 * 120 = 12000 pixels!**

As you can see, the ball's speed is directly tied to the frame rate, which can vary widely. In the same amount of time (1 second), the distance traveled varies dramatically!

You can do it if you want your game to be Pay To Win🤷 

But we don't do that here!



![ ](/Full-Stack-Game-Development/images/fc37453e78fd6c15.gif)



So, how can you fix this issue?🤔 This is when **delta time** comes in handy



## What is delta time?


---



> 📖 🎮 **GAME DEV DICTIONARY **
> ***Delta Time***: "The time in seconds it took to complete the last frame. Use this value to make your game frame rate independent."



Let’s understand how this delta time makes the movement independent of the frame rate:

At 30 FPS:

- delta_time ≈ 0.0333 seconds (1/30)
- The ball moves 100 * 0.0333 ≈ 3.33 pixels per frame
- **Over one second: 3.33 * 30 frames = 100 pixels**

At 60 FPS:

- delta_time ≈ 0.0167 seconds (1/60)
- The ball moves 100 * 0.0167 ≈ 1.67 pixels per frame
- **Over one second: 1.67 * 60 frames = 100 pixels**

At 120 FPS:

- delta_time ≈ 0.0083 seconds (1/120)
- The ball moves 100 * 0.0083 ≈ 0.83 pixels per frame
- **Over one second: 0.83 * 120 frames = 100 pixels**

No matter the FPS, the ball moves **100 pixels in 1 second.**

This approach:

1. Makes the game fair across all devices
2. Ensures consistent gameplay experience
3. Makes your game more professional



You’ll implement this in your project in the next lesson!
