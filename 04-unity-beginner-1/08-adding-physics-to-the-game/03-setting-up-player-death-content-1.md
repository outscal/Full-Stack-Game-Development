The player character still doesn’t has a collider and a `Rigidbody`

Let’s start by adding a collider!



## Adding Collider to Mr. Blocks


---

Which collider do you think is best for the Mr. Blocks?🤔

Box Collider 2D? Yup! That’s right!

Here’s how you can add a collider to the `Player` game object:

1. Select the `Player` game object in the `Hierarchy`.
2. In the `Inspector`, click "`Add Component`" and search for "`Box Collider 2D`".
3. With the `Player` object selected, find the `Box Collider 2D` component in the `Inspector`.
4. Click "`Edit Collider`" to adjust its size and position.
5. Make sure the Collider covers the whole object for accurate collision detection.




<iframe src="https://www.loom.com/embed/c93084f76e474b99a3ca9c6cf38812e2" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ Add a `Box Collider 2D` to `Player` game object. 
> ✅ Adjust the Collider to match the shapes of your object



You have added a collider, but for collision to work you also need to add a `Rigidbody`.



## Adding Rigidbody to Mr. Blocks


---

> **Pro Tip**💡 
> For collision detection, only one game object needs a `Rigidbody`!



Here’s how you can add `Rigidbody` to Mr. Blocks:

1. Select `Player` in the `Hierarchy`.
2. In the `Inspector`, click "`Add Component`" and search for "`Rigidbody 2D`".
3. Click to add the `Rigidbody2D` component.




<iframe src="https://www.loom.com/embed/9be7dcb6b9dc4c0e89c28ac4883dfdf8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ Add a `Rigidbody 2D` component to Mr. Blocks 
> ✅ Play the game!



Mr. Blocks and spikes are now colliding!

But, how will Mr. Blocks know he hit an obstacle? 🤔

Here’s when **Tags** come in handy!



## Tags


---

In Unity, you can use tags to label and categorize objects.

They're like name tags for game elements, helping us identify and interact with specific objects in code.

Tags are incredibly useful for:

- Identifying specific types of objects (like players or enemies)
- Triggering events when particular objects interact
- Quickly finding game objects in your code




<iframe src="https://www.loom.com/embed/e39a6826bce749eb86c6a69f946d3d42" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ Add a "Player" tag to Mr. Blocks 
> ✅ Add an "Obstacle" tag to all your spike objects



Collision is successfully set up!

In the next lesson, you’ll implement player death using code.
