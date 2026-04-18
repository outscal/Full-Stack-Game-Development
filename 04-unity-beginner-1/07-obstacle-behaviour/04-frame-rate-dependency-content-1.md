# Frame Rate Dependency Problem


---



Now that you are aware of the frame rate, let's discuss an important issue: **frame rate dependency**.

In the current implementation, the spike ball rotates by `rotationAngle` degrees every frame. 

This seems fine at first, but it can lead to inconsistent behaviour across different devices or under varying performance conditions.



Why?🤔 Because the number of frames per second (FPS) can vary:

- A powerful computer might run your game at 120 FPS
- A slower device might only manage 30 FPS or 60 FPS
- FPS can even fluctuate during gameplay on the same device



This means that on a faster device or when the game is running smoothly, the spike will rotate much faster than on a slower device or when the game struggles to maintain frame rate.

Let's illustrate this:

1. If `rotationAngle = 90` and the game runs at 60 FPS:
2. - The spike rotates 90° * 60 = 5400° per second (15 full rotations!)
3. If `rotationAngle = 90` and the game runs at 30 FPS:
4. - The spike rotates 90° * 30 = 2700° per second (7.5 full rotations)



As you can see, the rotation speed is directly tied to the frame rate, which can vary widely.

In the same amount of time(1 second), the number of rotations varies!

You can do it if you want your game to be Payt To Win🤷

But we don't do that here!

![ ](/Full-Stack-Game-Development/images/b280981f2f00ac5a.bin)



![ ](/Full-Stack-Game-Development/images/fc37453e78fd6c15.gif)





So, how can you fix this issue?🤔

You need to make the rotation independent of the frame rate!



# Fixing Rotation Logic


---

Rotation can be made independent of frame rates by knowing each frame's time to complete!

This is where Unity's `Time.deltaTime` comes in handy.



> **📖 🎮 UNITY DEV DICTIONARY** 
> ***Time.deltaTime:*** "The time in seconds it took to complete the last frame. Use this value to make your game frame rate independent."



If you multiply `Time.deltaTime` to the `rotationAmount` the rotation will be independent of the frame rate.



```csharp
private void RotateSpikeBall() => transform.Rotate(Vector3.forward, rotationAngle * Time.deltaTime);
```



> **TODO**
> **✅**Multiply `Time.deltaTime` to the `rotationAngle` in `RotateSpikeBall()` method.



Let's understand this with the same example used above:


If `rotationAngle = 90` and the game runs at 60 FPS:

- Time.deltaTime(Time taken by 1 frame assuming constant 60 FPS) ≈ 0.0167 seconds (1/60)
- The spike rotates 90° * 0.0167 ≈ 1.5° per frame
- **Over one second: 1.5° * 60 frames = 90°**

If `rotationAngle = 90` and the game runs at 30 FPS:

- Time.deltaTime ≈ 0.0333 seconds (1/30)
- The spike rotates 90° * 0.0333 ≈ 3° per frame
- **Over one second: 3° * 30 frames = 90°**

No matter the fps, the spike rotates **90° in 1 second.**

Now, the rotation logic is complete!💪
