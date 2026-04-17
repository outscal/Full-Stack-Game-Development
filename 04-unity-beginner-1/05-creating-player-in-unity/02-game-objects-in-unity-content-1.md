# What's a Game Object?


---

In Unity, everything present in the scene is a Game Object. You’ll learn more about game object as you read this lesson.



# Creating Player Game Object


---

Now that you know a bit about game objects let’s create one for Mr. Blocks!

You need to create a game object for the Player.




[Watch video](https://www.loom.com/embed/4b82dac72c9448d995a523fbf02547e0)





> **TODO:** 
> ✅Create an empty game object 
> ✅Rename the new Game Object to `Player`.



Congratulations! Your Player Character now exists in the game... but where is he?

Don't worry, he's there, just not visible in the scene.

You can make him visible, but before that you need to know about an important part of game objects: **Components!**



# Introducing Components


---

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/11_06_2024__13_28_35.png)

**Transform Component**



See that Transform component? It's the Player's built-in positioning system. Every Game Object has one!

The Transform component, controls:

- Position: Where a Game Object is in the game world.
- Rotation: Which way the Game Object is facing.
- Scale: How big (or small) the Game Object is.



> 📖🎮**UNITY DICTIONARY**: 
> **Components**: Functional pieces that can be attached to `GameObjects` to add specific functionality.



But `Transform` isn't the only component out there.

Game Objects can have many different components. Some other common ones include:

- `Rigidbody`: For realistic physics behaviour
- `Collider`: For detecting collisions with other objects
- `Audio Source`: For playing sounds

You'll be adding more components to the Player as you go along!



# Making The Player Visible


---

Right now, Mr, Blocks is like a ghost - he exists, but you can't see him. Let's give him a makeover!

You need to add a sprite to the player game object, to make him visible.



> **📖🎮Game Dev Dictionary **
> ***Sprite*****: **Sprite is a 2D image used for visualizing game objects.



But how do you add a sprite?🤔

There is a component: `Sprite Renderer`




[Watch video](https://www.loom.com/embed/ac5699bc53754d0ba6fdd1fff9230c62?sid=93ae1bce-86b8-42cc-ad2a-262cf1de7168)





> **TODO:** 
> ✅Select `Player` game object in the `Hierarchy`. 
> ✅In the `Inspector`, click `Add Component`. 
> ✅Search for `Sprite Renderer` and select it. 
> ✅Drag the sprite from `Assets/Sprites/Player` into the `Sprite` field of the `Sprite Renderer`.



The Player should now be visible in the Scene view.

Now that the Player is in the game world, how will you make him move?

In the next lesson, you'll learn about *scripts* (custom components)

👋🏻
