# Understanding Scaling Spike


---

To create your scaling spike, you'll combine two behaviors: rotation and size change.



![Scaling Spike](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/11_06_2024__13_59_55.gif)

**Scaling Spike**



First, you'll set up the basics.

You need to decide how quickly it'll change size.

You'll also choose the minimum and maximum sizes for the spike.

When your game starts, you'll set the spike to its initial size.

You need to update two things:

1. You'll keep the spike spinning.
2. You'll change the spike's size.

For the scaling, you'll smoothly adjust the spike's scale.

Once it reaches its maximum or minimum size, you'll reverse the scaling direction.

You'll also add a brief pause at the extreme sizes.

This creates a continuous grow-shrink-pause cycle



# Creating the Scaling Spike


---



Let's create our new obstacle: the SpikeBall_Scaling!

1. Create a `Circle` `Sprite `in Unity.
2. Rename it to "*SpikeBall_Scaling*".
3. In the `Sprite Renderer`, replace the default sprite with the `SpikeBall` sprite from your assets.




[Watch video](https://www.loom.com/embed/542c5f1790f94433a0c158e5f4f00166?sid=b7ca679b-8ce1-4490-a3e1-3caa8e70e1c6)





> **TODO:** 
> ✅ Create a circle sprite and rename it to *SpikeBall_Scaling *
> ✅ Replace the circle sprite with the `SpikeBall` asset in the `Sprite Renderer` component



# Setting Up the Scaling Spike


---



Now, let's give our spike some brains:

1. Create a new C# script called "`SpikeBall_Scaling.cs`".
2. Attach this script to the `SpikeBall_Scaling` GameObject in the Hierarchy.
3. Drag the SpikeBall_Scaling GameObject into the `Assets/Obstacles` folder to create a prefab.




[Watch video](https://www.loom.com/embed/12fa0fc0585c4fbab86b29be2686c782?sid=adb6d543-35fe-4a8f-b48e-56fb047e8942)





> **TODO:** 
> ✅ Create and attach the `SpikeBall_Scaling.cs` script to the `SpikeBall_Scaling` game object 
> ✅ Turn the `SpikeBall_Scaling` into a prefab in the `Assets/Obstacles` folder



## Adding Rotation


---



Remember how you made the spike rotate? It's the same for scaling spike as well.

You can quickly add it to the script!



> **TODO:** 
> ✅ Add a `public float rotationAngle` variable and set it to 90f 
> ✅ Create a `private void RotateSpikeBall()` method 
> ✅ In the `Update()` method, call `RotateSpikeBall()`



Click here to see the solution.

`**SpikeBall_Scaling.cs**`

```csharp
public float rotationAngle = 90f;

private void RotateSpikeBall()
{
    transform.Rotate(Vector3.forward, rotationAngle * Time.deltaTime);
}

private void Update()
{
    RotateSpikeBall();
}
```





# Adding Scaling and Delay to Spike


---

Scale Spike can be implemented in the following order:

1. Setting up variables for scaling
2. Scaling without delay
3. Adding delay



Let's implement them one by one.



## Creating Variables for Scaling


---



Now, you'll create variables for scaling.

Before you start, think about these questions:

- Why do you need `minScale` and `maxScale`?
- How does `scalingFactor` control the direction of scaling (growing or shrinking)?



> **TODO:** 
> ✅ Add `public float` variables for `scalingFactor`, `scalingSpeed`, `minScale`, and `maxScale` 
> ✅ Add a `private float currentScale` variable.

Click here to see the solution.

`SpikeBall_Scaling.cs`

```csharp
private float scalingFactor = 1f;   // Controls scaling direction
private float currentScale;        // Current scale value
public float scalingSpeed = 15f;   // Speed at which the spike scales
public float minScale = 0.5f;      // Minimum size
public float maxScale = 1.5f;      // Maximum size
```





Now that we have the required variables, let's implement the scaling logic. 



## Scaling Without Delay


---

The spike will smoothly grow and shrink between `minScale`and `maxScale`.

Here's how scaling can be done:



**Implementing **`**ScaleSpikeBall()**`:

1. Adjusting and Limiting Scale:



> 📖🎮 **UNITY DICTIONARY** 
> `**Mathf.Clamp**`: A Unity function that constrains a value within a specified range. It takes three parameters: the **value to clamp**, the **minimum** allowed value, and the **maximum** allowed value.



```csharp
currentScale += scalingFactor * scalingSpeed * Time.deltaTime;
currentScale = Mathf.Clamp(currentScale, minScale, maxScale);
```



- Changes `currentScale` based on `scalingFactor`, `scalingSpeed`, and `Time.deltaTime`.
- Ensures `currentScale` stays between `minScale` and `maxScale`.



1. Handling Direction Change:



```csharp
if (currentScale == maxScale || currentScale == minScale)
{
    scalingFactor = -scalingFactor;
}
```



- When reaching min or max scale, reverses the scaling direction by changing the sign of scale.



1. Applying Scale to GameObject:

```csharp
ApplyCurrentScale();
```

- Calls `ApplyCurrentScale()` to update the actual size of the spike in the game.



**Implementing **`**ApplyCurrentScale()**`**:**

```csharp
private void ApplyCurrentScale()
{
    transform.localScale = new Vector3(currentScale, currentScale, 1);  // Update the spike's size
}
```

- The scale of the spike is updated.



> **TODO:** 
> ✅ Implement the `ScaleSpikeBall()` method as shown above 
> ✅ Create the `ApplyCurrentScale()` method to update the spike's size 
> ✅ Ensure you understand how the scaling factor affects the spike's behavior



Click here to see the complete code.

`**SpikeBall_Scaling.cs**`

```csharp
private void Update()
{
    RotateSpikeBall();
    ScaleSpikeBall();
}
private void ScaleSpikeBall()
{
    currentScale += scalingFactor * scalingSpeed * Time.deltaTime;  // Adjust the scale
    currentScale = Mathf.Clamp(currentScale, minScale, maxScale);   // Keep the scale within boundaries
    
     if (currentScale == maxScale || currentScale == minScale)  // If the spike reaches its limits
    {
        scalingFactor = -scalingFactor;  // Reverse the scaling direction
    }
    
    ApplyCurrentScale();  // Apply the updated scale to the spike
}
private void ApplyCurrentScale()
{
    transform.localScale = new Vector3(currentScale, currentScale, 1);  // Update the spike's size
}
```





## Adding the Delay


---



The spike is scaling, but it doesn't pause at its limits. Let's add a delay at both the `minScale` and `maxScale` to make the spike pause before changing direction.



Think about these questions:

- How will a delay change the gameplay?
- How can we implement a waiting state so the spike pauses when it reaches its maximum and minimum sizes?



**Implementing the delay**:

1. New Variables:

```csharp
public float scaleDelay = 2f;  // Delay between scaling up and down
private bool isWaiting = false;  // Is the spike in a waiting state?
private float timer = 0f;  // Tracks the waiting period
```

These variables control the delay behaviour.



1. Updated `Update()` Method:

```csharp
private void Update()
{
    RotateSpikeBall(); 

    if (isWaiting)
        HandleWaiting();  // Handle waiting logic
    else
        ScaleSpikeBall();  // Scale the spike
}
```

This method now decides whether to scale or wait based on the `isWaiting` flag. 

Now, the scaling happens only when the spike is not waiting.



1. New `HandleWaiting()` Method:

- Increments the timer each frame
- Check if the timer has reached scaleDelay
- Resets the waiting state and the timer when the delay is over



```csharp
private void HandleWaiting()
{
    timer += Time.deltaTime;

    if (timer >= scaleDelay) //If timer reaches the delay time
    {
        isWaiting = false;  // End the waiting period
        timer = 0f;  // Reset the timer
    }
}
```



1. Modified `ScaleSpikeBall()` Method:

```csharp
private void ScaleSpikeBall()
{
    // old scaling code

    if (currentScale == maxScale || currentScale == minScale)  // If the spike reaches its limits
    {
        // Old code to Reverse the scaling direction
        isWaiting = true;  // Enter waiting state
    }

     //Old code to Apply the updated scale
}
```

The changes here:

- When reaching min or max scale, we now set `isWaiting` to true
- This triggers the waiting state, pausing the scaling.



This implementation makes the spike pause for `scaleDelay` seconds at its minimum and maximum sizes before changing direction, adding a new dynamic to the obstacle's behavior.



> **TODO:** 
> ✅ Add `public float scaleDelay`, `private bool isWaiting`, and `private float timer` variables 
> ✅ Modify `ScaleSpikeBall()` to enter waiting state at min/max scales 
> ✅ Implement the `HandleWaiting()` method to manage the delay 
> ✅ Update the `Update()` method to handle both scaling and waiting states.



Click here to see the complete code.

`**SpikeBall_Scaling,cs**` 

```csharp
using UnityEngine;
public class SpikeBall_Scaling : MonoBehaviour
{
		//rotation variables
    public float rotationAngle = 90f;
    
    //scaling variables
    private float scalingFactor = 1f;
    private float currentScale;
    public float scalingSpeed = 15f;
    public float minScale = 0.5f;
    public float maxScale = 1.5f;
    
    //delay variables
    public float scaleDelay = 2f;
    private float timer = 0f;
    private bool isWaiting = false;
    
    private void Start()
    {
        currentScale = minScale;
        ApplyCurrentScale();
    }
    private void Update()
    {
        RotateSpikeBall();
        if (isWaiting)
            HandleWaiting();
        else
            ScaleSpikeBall();
    }
    
    private void RotateSpikeBall()
    {
        transform.Rotate(Vector3.forward, rotationAngle * Time.deltaTime);
    }
    
    private void ScaleSpikeBall()
    {
        currentScale += scalingFactor * scalingSpeed * Time.deltaTime;
        currentScale = Mathf.Clamp(currentScale, minScale, maxScale);
        if (currentScale >= maxScale || currentScale <= minScale)
        {
            scalingFactor = -scalingFactor;
            isWaiting = true;
        }
        ApplyCurrentScale();
    }
    
    private void ApplyCurrentScale()
    {
        transform.localScale = new Vector3(currentScale, currentScale, 1);
    }
   
    private void HandleWaiting()
    {
        timer += Time.deltaTime;
        if (timer >= scaleDelay)
        {
            isWaiting = false;
            timer = 0f;
        }
    }
}
```





Congratulations! You've created a spike that not only rotates but also scales up and down with a delay.🥳
In the next chapter, let's make the game tough for the player!
