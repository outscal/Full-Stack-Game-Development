# Understanding Moving Spike


---



To create your moving spike, you'll combine two behaviors: rotation and back-and-forth movement.



![Moving Spike](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/11_06_2024__13_58_17.gif)

**Moving Spike**



First, you'll set up the basics.

You need to decide how quickly it'll move.

You'll also choose two locations for it to travel between.

When your game starts, you'll place your spike at its starting position and decide its destination.

You need to update two things:

1. You'll keep the spike spinning.
2. You'll move the spike towards its destination.

For the movement, you'll smoothly shift the spike's position.

Once it reaches its target, you'll switch its destination to the starting position.

This creates a continuous back-and-forth motion.



# Creating the Moving Spike


---



Let's create our new spike ball: the SpikeBall_Patrolling!

1. Create a `Circle` `Sprite` in Unity.
2. Rename it to "*SpikeBall_Patrolling*".
3. In the `Inspector`, find the `Sprite Renderer`.
4. Replace the default sprite with the spike ball sprite from your project assets.




<iframe src="https://www.loom.com/embed/50af36b316be4688bfb45995a4e57e83" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> 
> ✅ Create a `circle` `sprite` and rename it to SpikeBall_Patrolling 
> ✅ Replace the circle sprite with the SpikeBall asset in the Sprite Renderer component



# Setting Up the Moving Spike


---

Now, let's give our spike some brains and make it reusable:

1. Create a new C# script and name it "*SpikeBall_Patrolling*".
2. Attach this script to your `SpikeBall_Patrolling` game object in the `Hierarchy`.
3. Drag the `SpikeBall_Patrolling` into the `Assets/Obstacles` folder to create a prefab.




<iframe src="https://www.loom.com/embed/cbb93d89dc2a4eb992eb3000d0ee2a99" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ Create and attach the `SpikeBall_Patrolling.cs` script to the `SpikeBall_Patrolling` game object 
> ✅ Turn the `SpikeBall_Patrolling` into a prefab in the `Assets/Obstacles` folder

# Adding Rotation and Movement in the Script


---



Now that the prefab is set up let's start implementing the patroling spike!

Let's implement the moving spike in the following order:

1. Rotation
2. Setting up movement by creating the required variables.
3. Setting patrol points.
4. Implementing patrol behaviour.

## Rotation


---

Remember how you made the spike rotate? Let's quickly recap the steps:

1. You need a variable to control how fast the spike rotates.
2. You create a method to apply the rotation.
3. You can use Unity's `transform.Rotate()` function actually to rotate the spike.



Now it's your turn to implement this!

> **TODO:** 
> ✅ Add a `rotationAngle` variable to your script 
> ✅ Create a method to rotate the spike ball 
> ✅ Call this method in `Update()` to make it rotate continuously



Click here to see the solution.

`**SpikeBall_Patrolling.cs**`

```csharp
public float rotationAngle = 90f;

private void Update()
{
    RotateSpikeBall();
}

private void RotateSpikeBall()
{
    transform.Rotate(Vector3.forward, rotationAngle * Time.deltaTime);
}
```





Let's now start with implementing the movement of the spike!!



## Creating Movement Variables


---

Now, let's understand the variables required for spike patrol movement:

- A speed for the patrol movement.
- Two points for the spike to move between.
- A way to track which point the spike is heading towards.

Try implementing these variables in your script!



> **TODO:**
> ✅Add variables for **patrol speed** and **two patrol points**
> ✅Add a variable to track the current **target point**



Click here to see the solution.

`**SpikeBall_Patrolling.cs**`

```csharp
float patrolSpeed = 2f;
public Vector3 pointA;
public Vector3 pointB;
private Vector3 targetPoint;
```





## Setting Initial Patrol Points


---

Before the spike starts moving, you need to:

1. Place it at its starting position.
2. Set its initial target.

Can you write a method to do this?



> **TODO:**
> ✅Create a method `private void SetPatrolPoints()` to set the initial position and target
> ✅Call this method when the game starts



Click here to see the solution.

`**SpikeBall_Patrolling.cs**`

```csharp
private void Start()
{
    SetPatrolPoints();
}

private void SetPatrolPoints()
{
    transform.position = pointA;
    targetPoint = pointB;
}
```





## Implementing Patrol Movement


---

Now is the exciting part - making our spike move!

Movement can be broken down into three parts:

1. **Update Method:**

```csharp
private void Update()
{
    RotateSpikeBall();  // Keep rotating the spike
    PatrolSpikeBall();  // Move the spike between points
}
```

- This method ensures that our spike both rotates and moves each frame.



`**PatrolSpikeBall()**` method:

1. **Moving Towards Target:**

> 📖🎮 **UNITY DICTIONARY** 
> `**Vector3.MoveTowards**`: A Unity function that moves a game object towards a target position. It takes three parameters: the **current position**, the **target position**, and the **maximum distance to move**.



```csharp
transform.position = Vector3.MoveTowards(transform.position, targetPoint, patrolSpeed * Time.deltaTime);
```



- Uses `Vector3.MoveTowards` to smoothly move the spike towards the current target point.
- `patrolSpeed * Time.deltaTime` ensures consistent movement speed regardless of frame rate.



1. **Switching Target Points:**

- Check if the spike has reached the current target point.
- If so, switch the target to another point using a ternary operator.



```csharp
if (transform.position == targetPoint)
{
    targetPoint = (targetPoint == pointA) ? pointB : pointA;  // Switch between A and B
}
```



This implementation creates a back-and-forth patrol movement for the spike between two points.



> **TODO:** 
> 
> ✅ Implement the `PatrolSpikeBall` method in your code 
> ✅ Use `Vector3.MoveTowards` to move the spike between `pointA` and `pointB` 
> ✅ Test your game and adjust `patrolSpeed` to see how different speeds affect gameplay.



Click here to see the complete code.

`**SpikeBall_Patrolling.cs**`

```csharp
using UnityEngine;
public class SpikeBall_Patrolling : MonoBehaviour
{
    public float rotationAngle = 90f;
    public float patrolSpeed = 2f;
    public Vector3 pointA;
    public Vector3 pointB;
    private Vector3 targetPoint;
    private void Start() => SetPatrolPoints();
    private void Update()
    {
        RotateSpikeBall();
        PatrolSpikeBall();
    }
    private void SetPatrolPoints()
    {
        transform.position = pointA;
        targetPoint = pointB;
    }
        private void RotateSpikeBall() => transform.Rotate(Vector3.forward, rotationAngle * Time.deltaTime);
        private void PatrolSpikeBall()
    {
        transform.position = Vector3.MoveTowards(transform.position, targetPoint, patrolSpeed * Time.deltaTime);
        if (transform.position == targetPoint)
        {
            targetPoint = (targetPoint == pointA) ? pointB : pointA;
        }
    }
}
```





## Experimenting with Patrol Speed, Distance, and Rotation


---



Remember, game design is all about finding the right balance. Experiment with these values until you find a challenging but fair combination!



> **💡 PRO TIP:** 
> The best obstacles aren't always the fastest or the biggest. They're the ones that complement your game's rhythm and challenge players in interesting ways.



> **TODO:** 
> ✅Experiment with `patrolSpeed` and `rotationAngle` values 
> ✅Observe how different speeds affect gameplay difficulty. 
> ✅Adjust the distance between patrol points.



You've just created a dynamic, moving obstacle!💪

In the next lesson, we'll explore making obstacles even more interesting by implementing scaling behaviours.
