Now that you've turned Mr. Blocks into a Prefab, let's learn how to customize and update him.

Sometimes, you might want to update all prefabs in different levels at once. Or maybe you want to make changes to just one prefab without affecting all the others.

**Note**: You don’t have a new level yet, so you can create multiple instances of the player prefab in the same level for this lesson.



> **TODO: **
> **✅** Create two instances of `Player` prefab.
> ✅ Position both of the instances side by side.



Now, let’s see how you can update changes in multiple prefab instances.



## Updating Prefabs


---

If you make changes to a Prefab in the scene (like making Mr. Blocks faster), those changes won't automatically apply to all the prefabs.

You need to use the `Override` feature

Here's how to update all prefabs using `Override`:

1. Select `Player` game object in the `Hierarchy`.
2. Make your changes (like increasing his speed).
3. In the `Inspector`, look for the `Overrides` section.
4. Click `Apply All` to update the Prefab.




[Watch video](https://www.loom.com/embed/bfb24b7bb6ac4ac9ac3664ed4d336c94?sid=af65870e-ac17-4b38-b625-9349ecb3877e)





> 💡** PRO TIP**: 
> You can also update all Prefabs by: Double-clicking the Prefab in the `Project` window, Making your changes, Save and close the Prefab.



> **TODO: **
> ✅ Change the movement speed in any of the `Player` prefab. 
> ✅ Notice that movement speed in the both the prefabs changes.



Now all Mr. Blocks will have the new changes!

But what if you want to make changes to only one of the instances?🤔



## Unpacking Prefabs


---

Unpacking a Prefab turns it back into a regular game object.

This means you can change it without affecting other instances of Mr. Blocks.

Here's how to unpack prefabs:

1. Right click on any one `Player` game object in the `Hierarchy`.
2. Select the `Prefab` dropdown and select `Unpack Prefab`.




[Watch video](https://www.loom.com/embed/577b605fb60448e1903bb63e30d69186?sid=01feb759-79a0-4b40-9807-98d223cff1fb)





> **TODO: **
> ✅ Change the movement speed in the unpacked game object. 
> ✅ Notice that movement speed in the both the prefabs are different.



Now you can modify this Mr. Blocks without changing the others!



## Making Changes in Game View


---

Here's a tricky part:

Those changes aren't saved if you make changes to Mr. Blocks while playing the game.

For example, if you move Mr. Blocks to a new position while testing, he'll go back to his original spot when you stop the game.

This is actually helpful - it prevents accidental changes during testing.

Congratulations! You've learned Prefabs.

In the next chapter, you’ll explore how to create spike balls to challenge Mr. Blocks!

Get ready to put Mr. Blocks to the test!⚔️
