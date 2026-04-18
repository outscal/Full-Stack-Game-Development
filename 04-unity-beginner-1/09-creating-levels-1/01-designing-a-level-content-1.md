It's time to create Mr. Block’s first adventure playground.

You’ll make a level that's both fun and functional!



## What Makes a Good First Level?


---

Before you start creating, let's think about what makes a great first level:

1. It should be easy! You want players to learn the ropes without getting frustrated.
2. It needs boundaries to keep Mr. Blocks from wandering off into the void.



## Building the Boundaries


---

You need to create walls that will keep him in the play area.

Think about a simple rectangle shape - four walls, one on each side.

You'll use `Box Collider 2D` component on these walls.




<iframe src="https://www.loom.com/embed/c7a1da0680f84bf19d4c2cac808b3e0c" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ Create four walls in your Unity scene 
> ✅ Add `Box Collider 2D` to each wall 
> ✅ Test that Mr. Blocks can't escape the level



## Keeping It Simple


---

Remember, this is where players are just getting to know Mr. Blocks and how he moves.

Let's think about what you really need for the first level:

- Walls to keep Mr. Blocks in bounds
- A finish line to end the level



![Level 1](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/11_06_2024__14_12_33.png)

**Level 1**



That's it! No tricky obstacles or complex paths for now. You want players to get comfortable with the basic movement.



> **TODO:** 
> ✅ Position Mr. Blocks at the level start 
> ✅ Add a `LevelFinishCollider` at the level end 
> ✅ Test that Mr. Blocks can reach the finish with no obstacles



## Tidying Up Our Scene


---

You need to keep your workspace organized. In Unity, this means keeping our `Hierarchy` neat and tidy.

You can group similar objects together, like putting all walls into an empty "Walls" game object.




<iframe src="https://www.loom.com/embed/a500648300384cf3ad62bb3f4d4852c9" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ Create an empty `Walls` GameObject and group your walls



Congratulations! You've just designed your first level. It might seem simple, but it's got all the basics:

- Boundaries to define the play area
- A clear finish line
- A difficulty level perfect for new players

In the next lesson, we'll learn about Scenes in Unity and how they'll help us create multiple levels.

Get ready to expand Mr. Blocks' world!
