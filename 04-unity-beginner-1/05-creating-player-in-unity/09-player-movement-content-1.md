You've captured Mr. Blocks' input, but he's still standing still. Let's change that!

Imagine Mr. Blocks standing on a grid:

- When you press D, he should move **right** on this grid.
- Press A, he moves **left,**
- W to move Up,
- Ans S to move Down.

But how do you translate this idea into code? 🤔



## Determining the Direction


---

First, you need to figure out which way Mr. Blocks should move. You'll use the input values for this:

`horizontalInput` tells us left (-1) or right (1)

`verticalInput` tells us down (-1) or up (1)

You can combine these into a direction using a `Vector3`:



> 📖🎮 **Unity Dictionary **
> **Vector3**: In Unity, a **Vector3** represents a point or direction in 3D space. It is made up of three numbers or "coordinates" that describe a position along the **X**, **Y**, and **Z** axes.




```csharp
Vector3 moveDirection = new Vector3(horizontalInput, verticalInput, 0);
```



## Applying Speed


---

Now, you need to make Mr. Blocks move at the speed you want:



```csharp
moveDirection = moveDirection * speed;
```



## Making Movement Frame-Rate Independent


---

To ensure smooth movement on all devices, you'll use `Time.deltaTime`:



```csharp
moveDirection = moveDirection * speed * Time.deltaTime;
```



> 💡 Pro Tip: `Time.deltaTime`
> 
> `Time.deltaTime` helps make movement smooth across different frame rates. You'll explore this more in the ***Obstacle Behaviour*** chapter!



## Moving Mr. Blocks


---

Finally, update Mr. Blocks' position:



```csharp
transform.position += moveDirection;
```



This moves Mr. Blocks in the direction we calculated.

Now that you understand each step, you need to put it all together in a new `MovePlayer()` method:



```csharp
public float speed;

private void MovePlayer()
{
    Vector3 moveDirection = new Vector3(horizontalInput, verticalInput, 0);
    Vector3 moveDelta = moveDirection * speed * Time.deltaTime;
    transform.position += moveDelta;
}
```



> **TODO: **`**Player.cs**` 
> ✅ Create a `public float speed = 5f;` variable.
> ✅ Implement the `MovePlayer()` method in the `Player.cs` script.



Lastly, `MovePlayer()` needs to be called in the `Update()` method:



```csharp
private void Update()
{
    GetInput();
    MovePlayer();
}
```



> **TODO: **`**Player.cs**` 
> ✅ In the `Update()` method call the `MovePlayer()` method after `GetInput()` 
> ✅ Save the script and test the movement in Unity.



## Normalizing the Direction


---

But wait! If you press two keys at once (like up and right), Mr. Blocks would move faster diagonally.

You don't want that. To fix this, you "normalize" the direction:



Here’s a much more detailed explanation.(Only open this if you like Maths 😶)

## The Problem: Speedy Diagonals


---

Without normalization, diagonal movement becomes faster than horizontal or vertical movement. Here's why:

Assume your character moves at a speed of 5 units per second.

- Moving right: velocity = (5, 0) Distance traveled = √(5² + 0²) = 5 units
- Moving diagonally: velocity = (5, 5) Distance traveled = √(5² + 5²) ≈ 7.07 units

🖼️ Image Placeholder: Diagram showing character movement paths, with diagonal paths longer.

Your character moves about 1.4 times faster, diagonally! This can make your game feel inconsistent and potentially break your level design.



## The Solution: Normalization


---

Normalization adjusts the velocity so that diagonal movement covers the same distance as horizontal or vertical movement.

Here's how it works mathematically:

1. Calculate the magnitude of the velocity vector: magnitude = √(x² + y²)
2. Divide each component by this magnitude: normalized_x = x / magnitude normalized_y = y / magnitude
3. Multiply by the desired speed

For our diagonal movement:

1. magnitude = √(5² + 5²) ≈ 7.07
2. normalized_x = 5 / 7.07 ≈ 0.707 normalized_y = 5 / 7.07 ≈ 0.707
3. Final velocity = (0.707 * 5, 0.707 * 5) ≈ (3.54, 3.54)

Now, let's check the distance: √(3.54² + 3.54²) ≈ 5 units

🖼️ Image Placeholder: Diagram showing normalized movement paths, with all directions covering equal distance.

With normalization, your character moves the same distance in all directions, making the gameplay feel consistent and fair.

In Unity, you can achieve this simply with:



```csharp
moveDirection = moveDirection.normalized * speed;
```



This one line ensures your character moves at a consistent speed, regardless of direction!





```csharp
moveDirection = moveDirection.normalized * speed * Time.deltaTime;
```



This ensures Mr. Blocks moves at a consistent speed in all directions.

Great! Mr. Blocks is now moving smoothly. But what if you want to use him in different levels?

Do you need to create Mr. Blocks again?!🤨

Recreating Mr. Blocks from scratch each time would be time-consuming. This is where Prefabs come in handy!

In the next chapter, we'll explore Prefabs, making it easy to use him throughout your game.
