# Understanding Rotating Spikes


---

Remember the obstacles we talked about in the last lesson? 

It's time to bring one to life: the Rotating Spike!



But first, let's think:

- Why make a spike rotate?
- How does it add to the game's difficulty?



A spike ball isn't just a static obstacle. 

It's dynamic.

The spike rotates continuously, and players must avoid it by positioning themselves correctly. 

If they fail? Ouch! 🫣 They get hit.



> 📖 🎮 **GAME DEV DICTIONARY**

> ***Dynamic Obstacle***: "An obstacle that moves or changes over time, requiring players to adapt their strategy and timing continuously."



Now that you understand the rotating spike let's start creating it!



# Creating the Spike Ball


---



Steps to create a spike ball:

1. Create a `Circle` `Sprite`.
2. Rename it to "*SpikeBall*".

Now, let's give it the correct appearance:

1. In the Inspector, find the `Sprite Renderer` component.
2. Set the spike ball sprite from the project assets as the `Image`.




<iframe src="https://www.loom.com/embed/de9cd1f2dea94c3ab8e26514b8d6d5f9" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO**
> ✅In `Hierarchy` create a circle sprite and rename it to `SpikeBall` 
> ✅Replace the circle sprite with the spike ball asset.





# Setting Up the Spike Ball


---

Time to add our script:

1. Create a `C# Script` and name it `SpikeBall` in `Assets/Scripts/Obstacles/`
2. Attach the new `SpikeBall.cs`  script onto your `SpikeBall` game object in the `Hierarchy`.

Finally, let's turn our spike ball into a prefab:

1. Drag the `SpikeBall` game object in `Assets/Obstacles` to turn it into a prefab.
2. The `SpikeBall` game object in the `Hierarchy` should now appear blue, indicating it's a prefab instance.




<iframe src="https://www.loom.com/embed/ea97286b72294ced914760fce4f9b099" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ Create and attach the `SpikeBall.cs` script to the `SpikeBall` game object.
> ✅ Turn the `SpikeBall` game object into a prefab in the Obstacles folder



Great! Now you have a spike ball prefab ready to use in your game. 

Let's move on to scripting its behaviour.



# Bringing Spike Ball To Life!


---

Before you start coding, let's brainstorm and understand the task:

1. You need to **rotate** an object in Unity.
2. You need to control the **angle** of rotation.



Now that we've brainstormed let's write the script to make our spike rotate!



# Writing the Script for the Rotating Spike


---

The script for rotating the spike can be divided into parts:

- Setting up required variables.
- Setting up the rotation to happen at every frame.
- Implementing rotation logic.
- Testing rotation of the spike



## Setting Up the Variables


---

First, you need a parameter to control how fast the spike rotates:



`**SpikeBall.cs**`

```csharp
public float rotationAngle = 90f;
```



This `rotationAngle` variable will adjust how much the spike will rotate at each frame.

Feel free to change this value to see different effects!



## Rotating the Spike Every Frame


---

Now, let's set up the spike to rotate continuously:



How can the spike rotate continuously?🤔

The `Update()` method runs once per frame in Unity. 

Perfect for continuous actions like rotation!



> **TODO:** 
> ✅ Open the SpikeBall script in your code editor 
> ✅ Add a `public float` variable named `rotationAngle` and set it to `90f `
> ✅ Create a method named `private RotateSpikeBall()` 
> ✅ In the `Update()` method, call `RotateSpikeBall()`



Click here to see the solution.

`**SpikeBall.cs**`

```csharp
using UnityEngine;
public class SpikeBall : MonoBehaviour
{
    public float rotationAngle = 90f;
    private void Update() => RotateSpikeBall();
    private void RotateSpikeBall() {};
}
```





## Implementing the Rotation Logic


---

Here's where the magic happens:



`**SpikeBall.cs**`

```csharp
private void RotateSpikeBall()
{
    transform.Rotate(Vector3.forward, rotationAngle);  // Rotate around Z-axis
}
```



Let's break this down:

`transform.Rotate`:

- This is a Unity function that rotates a `GameObject`.
- It's part of the `Transform` component, which every `GameObject` has.
- The function takes two parameters: the rotation **axis** and the rotation **angle**(in degrees).



`Vector3.forward`:

- In Unity, `Vector3.forward` represents the Z-axis (0, 0, 1).
- In 2D games, rotating around the Z-axis makes objects spin like a pinwheel.
- You can use this to rotate the spike ball in its 2D plane.



`rotationAngle`:

- This determines how much to rotate in the current frame.
- `rotationAngle` is degrees per frame.
- So if the `rotationAngle` is 90f, then the spike ball will rotate by 90 degrees at each frame.



![Rotation Along Z-Axis](/Full-Stack-Game-Development/images/353b6cc389fd2901.gif)

**Rotation Along Z-Axis**



> **TODO:**
> ✅ In `RotateSpikeBall()`, use `transform.Rotate(Vector3.forward, rotationAngle)` to rotate the spike ball 
> ✅ Save your script and return to Unity 
> ✅ Adjust the `rotationAngle` in the `Inspector` to see different rotation angle





Click here to see the final code.

```csharp
using UnityEngine;
public class SpikeBall : MonoBehaviour
{
    public float rotationAngle = 90f;
    private void Update() => RotateSpikeBall();
    private void RotateSpikeBall() => transform.Rotate(Vector3.forward, rotationAngle);
}
```





The rotation logic is not yet complete. There's a problem with this code.

To understand the problem, you first need to know about Frame Rates.

In the next lesson, let's discuss about frame rates!
