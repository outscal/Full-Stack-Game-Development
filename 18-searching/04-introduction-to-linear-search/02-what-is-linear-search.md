> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your main branch called → [ `**Feature-1-Linear-Search**` ]

> 

> Let’s start working on the new feature now!



## linear search


---



Linear search is a simple search algorithm for finding a specific element within a list. 

It works by sequentially (one-by-one) checking each element of the list until a match is found or the whole list has been searched.



Let's look at the individual steps the algorithm uses before moving forward:

1. ***Start from the first stick***: Begin at the first stick in the list.
2. ***Check each stick***: Compare each stick's length to the target length.
3. ***Found it***: If the current stick matches the target stick, return the index of the current stick.
4. ***Keep looking***: If the current stick does not match the target stick, move to the next stick.
5. ***Repeat***: Repeat steps 2-4 until the element is found or the list ends.
6. ***Not found***: If the end of the list is reached without finding the target stick, return -1.





## **Examples of LINEAR SEARCH IN Game development**


---



Linear search is not just a theoretical concept but is widely used in game development. 

Let's look at a few examples:



**Checking for Collision**

As you already know, collision detection is important for determining if the player's character collides with anything in a game.



The game constantly tracks the players collider and position.

The game then linearly searches over the objects in the game to check if anything overlaps the player.

If there is an overlap, then you can damage the player or run whatever logic you need to.



![collision detection in 2D games](//outscal.github.io/Full-Stack-Game-Development/images/5b80e2f91efa9ab2.gif)

*Collision detection in games*





**FindObject()**

As you know, in Unity, the `FindObject()` method searches for and retrieves a `GameObject` by its name from the hierarchy.

This means that it sequentially checks each `GameObject` in the scene and compares it to the one you are looking for.



If Unity finds a `GameObject` that matches, it returns a reference to that `GameObject`. 

If no match is found, Unity returns `null`, indicating that the `GameObject` with the specified name does not exist in the scene.



![   ](//outscal.github.io/Full-Stack-Game-Development/images/9835183f1a62d2fe.png)

*Hierarchy of *`*GameObjects*`* in the scene*



> 💡Pro tip: `FindObject()` is an in-built Unity function that is considered inefficient and time-consuming because it sequentially checks each `GameObject` in the scene.





Now you know how the Linear Search algorithm works!

In the upcoming lessons, you will create the architecture for visualizing this algorithm.
