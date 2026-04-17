Now that you have a `LevelManager`.

You'll update the `LevelManager` to handle the transitions between levels.



## Introducing Scene Management


---

Unity uses a class called `SceneManager` to handle scenes.

`SceneManager` class is under the `UnityEngine.SceneManagement` namespace Let's add it to the Level Manager script:



```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class LevelManager : MonoBehaviour
{
    // previous code
}
```



> **TODO:** 
> ✅ Add the `using UnityEngine.SceneManagement;` to your `LevelManager` script



## Keeping Track of Current Level


---

You need a way to keep track of the current level.

You can use the build index to track the current level.

Here’s when you can use build index to access the level from the script.

- `SceneManager.GetActiveScene().buildIndex` gives the build index of the current scene in our build settings.
- `currentSceneIndex` stores the build index of the current level.



```csharp
public class LevelManager : MonoBehaviour
{
    private int currentSceneIndex;

    private void Start()
    {
        currentSceneIndex = SceneManager.GetActiveScene().buildIndex;
    }

}
```



> **TODO:** 
> ✅ Add and initialize the `currentSceneIndex` variable and `Start` method to your `LevelManager` script



## Moving to the Next Level


---

It’s time transition to the next level:

You need to calculate the next level's index and also total no. of scenes:



```csharp
private void LoadNextLevel()
{
    int nextSceneIndex = currentSceneIndex + 1;
    int totalNumberOfScenes = SceneManager.sceneCountInBuildSettings;
}
```



Now, you need to check if the next level exists in the build settings:



```csharp
private void LoadNextLevel()
{
		int nextSceneIndex = currentSceneIndex + 1;
    int totalNumberOfScenes = SceneManager.sceneCountInBuildSettings;
    
    if(nextSceneIndex < totalNumberOfScenes)
    {
    }
}
```



If it does, then load the next level:



```csharp
private void LoadNextLevel()
{
    int nextSceneIndex = currentSceneIndex + 1;
    int totalNumberOfScenes = SceneManager.sceneCountInBuildSettings;
    
    if (nextSceneIndex < totalNumberOfScenes)
    {
        SceneManager.LoadScene(nextSceneIndex);
    }
}
```



Handle game completion:



```csharp
private void LoadNextLevel()
{
    int nextSceneIndex = currentSceneIndex + 1;
    int totalNumberOfScenes = SceneManager.sceneCountInBuildSettings;
    
    if (nextSceneIndex < totalNumberOfScenes)
    {
        SceneManager.LoadScene(nextSceneIndex);
    }
    else
    {
        Debug.Log("You've completed all levels!");
    }
}
```



Lastly, you need to call the `LoadNextLevel` method in the `OnLevelComplete` method.



> **TODO:** 
> ✅ Implement the `LoadNextLevel` method to your `LevelManager` script 
> ✅ In the `OnLevelComplete` method call the `LoadNextLevel` method.



## Restarting the Current Level


---

You also need a way to restart the level if Mr. Blocks dies:



```csharp
public void OnPlayerDeath() => RestartLevel();

private void RestartLevel => SceneManager.LoadScene(currentSceneIndex);
```



This simply reloads the current scene, restarting the level.



> **TODO:** 
> ✅ Implement the `OnPlayerDeath` method to your `LevelManager` script



Here's how your complete LevelManager script should look:



Updated `LevelManager.cs`

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class LevelManager : MonoBehaviour
{
    private int currentSceneIndex;

    private void Start() => currentSceneIndex = SceneManager.GetActiveScene().buildIndex;
    
		public void OnLevelComplete() => LoadNextLevel();
		
    private void LoadNextLevel()
		{
	    int nextSceneIndex = currentSceneIndex + 1;
	    int totalNumberOfScenes = SceneManager.sceneCountInBuildSettings;
	    
	    if (nextSceneIndex < totalNumberOfScenes)
	    {
	        SceneManager.LoadScene(nextSceneIndex);
	    }
	    else
	    {
	        Debug.Log("You've completed all levels!");
	    }
		}

    public void OnPlayerDeath() => RestartLevel();

		public void RestartLevel => SceneManager.LoadScene(currentSceneIndex);
}
```





## Connecting Player and LevelManager


---

Your Player script should already be set up to use these new `LevelManager` functions.

Double-check that it has these methods:



Updated `Player.cs`

```csharp
public class Player : MonoBehaviour
{
    public LevelManager levelManager;

    // ... other Player code ...

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Finish"))
        {
            LevelComplete();
        }
    }

    private void OnCollisionEnter2D(Collision2D other)
    {
        if (other.gameObject.CompareTag("Obstacle"))
        {
            PlayerDied();
        }
    }

    private void PlayerDied()
    {
        levelManager.OnPlayerDeath();
        Destroy(gameObject);
    }

    private void LevelComplete()
    {
        levelManager.OnLevelComplete();
        gameObject.SetActive(false);
    }
}

```





> **TODO:** 
> ✅ Make sure your Player script has these methods 
> ✅ In the Unity Editor, assign the `LevelManager` to the Player in the Inspector



## Testing Level Transitions


---

Time to test your work:

1. Start your game from Level 1.
2. Guide Mr. Blocks to the finish line. You should see the next level load!
3. Then, intentionally hit an obstacle. The current level should restart.



> **TODO:** 
> ✅ Play your game and test both level transition and level restart



Great job! Mr. Blocks can now progress through levels and restart when he dies.

In the next chapter, you'll add more polish to your game, perhaps with a user interface. Keep up the great work!💪🏼
