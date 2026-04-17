## Understanding Level Manager


---

You've got Mr. Blocks moving around, but who's keeping track of his progress in every level? Enter the Level Manager! 🎮

How do you think you can keep tabs on Mr. Block’s progress? 🤔

- When Mr. Blocks finishes a level, it cheers! and load the next level
- If Mr. Blocks meets a spike, it starts the level over.



## Creating Level Manager


---

Here's how you can create a Level Manager:

1. Add a `LevelManager` game object in all the levels in Unity
2. Create a new script called `LevelManager.cs`
3. Add a method to track the completion of a level:



```csharp
public class LevelManager : MonoBehaviour
{
    public void OnLevelComplete()
    {
        Debug.Log("Level Complete!");
    }
}
```



> **TODO:** 
> ✅Create the `LevelManager` script with the `OnLevelComplete()` method. 
> ✅In Unity, create an empty GameObject, name it "`LevelManager`", and attach our new script to it. 
> ✅In `Assets/Prefabs/Level` save the `LevelManager` object as a prefab.



## Connecting Mr. Blocks to the Level Manager


---

Now, you need to make sure Mr. Blocks can call for help when he needs it!

Update your Player script like this:



```csharp
public LevelManager levelManager;

private void LevelComplete()
{
    levelManager.OnLevelComplete();
}
```



> **TODO:** 
> ✅Add the `LevelManager` reference to the Player script. 
> ✅Update the `LevelComplete()` method to call the Level Manager. 
> ✅In Unity, drag the `LevelManager` object onto the Player's `levelManager` field in the `Inspector`.



Great job! You've just created a powerful ally for Mr. Blocks. 💪

In the next lesson, you’ll implement the transition between levels when a level is complete!
