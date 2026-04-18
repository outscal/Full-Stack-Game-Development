## Creating the Level Finish Trigger


---

Here’s how you can create a Trigger:

1. Create an empty `GameObject` named `LevelFinishCollider`.
2. Add a `Sprite Renderer` with a visible shape (triangle recommended).
3. Attach a `Polygon Collider 2D` and set it as "`Is Trigger`".
4. Set its Tag to "Finish".




<iframe src="https://www.loom.com/embed/a7ad073a816242fc95dcdc0b86d43983" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅Create the `LevelFinishCollider` GameObject. 
> ✅Set up its visual appearance and collider. 
> ✅Tag it as "Finish" 
> ✅ In `Assets/Prefabs/Level` save it as a prefab.



Now, the `Player` game object needs to detect the finish trigger!



## Detecting the Finish Trigger


---

Just like `OnCollisionEnter2D` is used to detect collision,

`OnTriggerEnter2D` can be used to detect trigger collisions!



> 💡 **Pro Tip**: 
> For 3D games, you can use `OnCollisionEnter` and `OnTriggerEnter` without the "2D" suffix!



```csharp
private void OnTriggerEnter2D(Collider2D other)
{
    if (other.gameObject.CompareTag("Finish"))
    {
        LevelComplete();
    }
}
```



> **TODO:** 
> ✅Implement `OnTriggerEnter2D()` in the Player script. 
> ✅ Create an Empty function for `private void LevelComplete()` 
> ✅Add logic to detect collision with "Finish" tagged object.



## Completing the Level


---

For now, you can just debug “Level Complete!” to test the logic. In the next chapter, you’ll complete the implementation.



```csharp
private void LevelComplete()
{
    Debug.Log("Level Complete!");
}
```



> **TODO:** 
> ✅Add `LevelComplete()` method to `Player` script. 
> ✅Test the level: guide Mr. Blocks to the finish and check for "Level Complete!" in the console.



You have successfully implemented Triggers!👏🏼

In the next lesson, you’ll use physics to implement Mr. Block’s movement!
