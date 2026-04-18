In this lesson, let’s understand collisions in Unity!



# Why Do We Need Collisions?


---

Collisions make games feel real and interactive. They let us:

- Detect when objects interact (like Mr. Blocks hitting a spike)
- Create physical reactions between objects

But how do collisions in Unity work?🤔



# Understanding Collisions


---

For a collision to work, you’ll need these components:

- **Colliders**: Defines the physical boundaries of an object, allowing it to interact with other objects.
- **Rigidbody**: At least one object must have a `Rigidbody` component for collisions to work.

Let’s understand Colliders and Rigidbody one by one!



## 2D Colliders Overview


---

For 2D games like Mr. Blocks, Unity offers different types of 2D Colliders:



![Colliders](/Full-Stack-Game-Development/images/2bd243214026a240.png)

**Colliders**

1. Box Collider 2D
2. Circle Collider 2D
3. Polygon Collider 2D
4. Capsule Collider 2D

And more!



## Rigidbody


---



It gives objects physics-related properties like:

- **Mass**: How heavy the object is
- **Velocity**: How fast and in what direction it's moving
- **Collision Detection**: How accurately it detects collisions



Objects without a `Rigidbody` won't react to collisions or forces in the game world.

But, Why?!🤨

This is because Collisions are also a part of Unity’s physics engine!

Now that you understand collisions, you’ll set up a collision between Mr. Blocks and obstacles in the following few lessons!
