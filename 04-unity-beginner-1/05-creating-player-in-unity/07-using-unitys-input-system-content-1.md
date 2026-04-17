Unity uses axes to help us capture player input for movement.



# Understanding Axes in Unity


---

Imagine Mr. Blocks standing in the middle of a giant coordinate system:



![Axes In Unity](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/11_06_2024__13_37_16.gif)

**Axes In Unity**



- The X-axis runs left to right.
- The Y-axis runs down to up.
- The Z-axis runs backward to forward.

For 2D games like Mr. Blocks, we primarily care about two of these:

- Horizontal movement (left and right) happens along the X-axis.
- Vertical movement (up and down) happens along the Y-axis.



Input  

Direction

D

Positive X(RIGHT)

A

Negative X(LEFT)

W

Positive Y(UP)

S

Negative Y(DOWN)



# Capturing Player Input


---

Now that you understand axes, let's see how Unity uses them for input.

The `GetAxisRaw()` method can be used to get the player’s input.



> 💡 **Pro Tip:** `Input.GetAxisRaw("Axis Name")`: Returns input values Axis Names: "Horizontal" (X-axis), "Vertical" (Y-axis)
> 
> Input
> 
> Value
> 
> Right Arrow/D
> 
> : 1 (positive X)
> 
> Left Arrow/A:
> 
> -1 (negative X)
> 
> Up Arrow/W:
> 
>  1 (positive Y)
> 
> Down Arrow/S: 
> 
> -1 (negative Y)
> 
> No input:          
> 
>  0



## Setting Up Player


---

Firstly, you need variables to store these input values!

These variables will hold values representing movement along the horizontal (X) and vertical (Y) axes.



```csharp
private float horizontalInput, verticalInput;
```



> **TODO: **`**Player.cs**` 
> ✅ Create the `private float` variables `horizontalInput` and `verticalInput`



## Getting Player Input


---

The player’s input can be stored in a separate function, `GetInput()` The role of this function is to get the player’s input, as the name suggests.

```csharp
private void GetInput()
{
    horizontalInput = Input.GetAxisRaw("Horizontal");
    verticalInput = Input.GetAxisRaw("Vertical");

    Debug.Log($"Horizontal: {horizontalInput}, Vertical: {verticalInput}");
}
```



> **TODO: **`**Player.cs**` 
> ✅ Create the `private void GetInput()` method in your `Player.cs` script 
> ✅ Use the `Input.GetAxisRaw("Axis Name")` method to get the player’s input. 
> ✅ Store the input for X-Axis and Y-Axis in the `horizontalInput` and `verticalInput` variable. 
> ✅ Print the input value on the console.



Now, using this method, you need to continuously keep track of the player’s input.



## Calling GetInput Method


---

To continuously check for input, you’ll call the `GetInput()` method in Unity's `Update()` function:



```csharp
private void Update() => GetInput();
```



`Update()` is called every frame, making it perfect for checking continuous actions like input.



> **TODO:** 
> ✅ Add the `Update()` method to your `Player` script 
> ✅ Save the script and return to Unity



Complete Script.

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    private float horizontalInput, verticalInput;

    private void Update() => GetInput();

    private void GetInput()
    {
        horizontalInput = Input.GetAxisRaw("Horizontal");
        verticalInput = Input.GetAxisRaw("Vertical");

        Debug.Log($"Horizontal: {horizontalInput}, Vertical: {verticalInput}");
    }
}
```





> **TODO:** 
> ✅ In Unity, ensure the script is attached to Mr. Blocks 
> ✅ Run the game in Unity 
> ✅ Press arrow keys or WASD and watch the console for input values 
> ✅ Observe how the values change as you press different keys



In the next lesson, you'll use this input to make Mr. Blocks move based on the input values!
