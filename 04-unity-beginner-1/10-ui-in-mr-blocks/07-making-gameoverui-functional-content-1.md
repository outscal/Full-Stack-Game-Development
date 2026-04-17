You have created the Game Over UI, but it’s not yet responding.

It’s time to make it functional!



## Understanding the Game Over UI


---



Before you start coding, let's understand what you're going to create:



1. A panel that appears when the game ends
2. Text that changes based on whether the player wins or loses
3. A button for restarting the level
4. A button for returning to the Main Menu



## Controlling Your Game Over Panel


---



You need a way to enable/disable the Game Over Panel so that you can display it at the right time!



`LevelUI.cs`

```csharp
public GameObject gameOverPanel;

private void SetGameOverPanel(bool isActive)
{
    gameOverPanel.SetActive(isActive);
}
```



> **TODO**: 
> ✅ Add the `gameOverPanel` variable and `SetGameOverPanel` method to your script 
> ✅ Assign the `Game Over Panel` in the Unity Inspector



Now, you can add functionality to the restart button!



## Setting Up the Restart Button


---



Restarting a level is Level Manager’s job. 
So you need a reference to the Level Manager using which you can call the `RestartLevel` method of the Level Manager class.

Then, you also need a listener for the `Restart Button`



> 📖 🎮 **UNITY DICTIONARY** 
> ***AddListener***: "A method that assigns a function to be called when a UI element (like a button) is interacted with."



`LevelUI.cs`

```csharp
using UnityEngine.UI;

public Button restartButton;
public LevelManager levelManager;

private void AddListeners()
{
    restartButton.onClick.AddListener(RestartButton);
}

private void RestartButton()
{
    levelManager.RestartLevel();
}
```



> **TODO**: 
> ✅ Add the `restartButton` and `levelManager` variables to your script 
> ✅ Implement the `AddListeners` and `RestartButton` methods 
> ✅ Assign the `Restart Button` and `LevelManager` in the Unity Inspector



Now, you need to customize the Game Over UI based on whether the player lost the level or completed all levels.



## Displaying Win/Lose Message


---



Firstly, you need to enable the `GameOverPanel` as it’s disabled at the start.

You need to the access to the text of the `GameOverPanel` to customize the text.

Then, the level panel needs to be hidden.



`LevelUI.cs`

```csharp
public TextMeshProUGUI gameOverText;

public void ShowGameWinUI()
{
    SetGameOverPanel(true);
    
    gameOverText.text = "Game Completed!!";
    gameOverText.color = Color.green;
    HideLevelPanel();
}

public void ShowGameLoseUI()
{
    SetGameOverPanel(true);
    
    gameOverText.text = "Game Over!!";
    gameOverText.color = Color.red;
    HideLevelPanel();
}
```



> **TODO**: 
> ✅ Add the `gameOverText` variable to your script 
> ✅ Implement the `ShowGameWinUI` and `ShowGameLoseUI` methods 
> ✅ Assign the `Game Over Text` in the Unity Inspector



Now, when do you call these methods?🤔



## Connecting to LevelManager


---



Show the Game Lose UI when the player dies.

Show the Game Win UI when all the levels are complete.

Both of these logics are present in the `LevelManager`!



```csharp
public class LevelManager : MonoBehaviour
{
		//previous code
		public LevelUI levelUI;
		
    public void OnPlayerDeath() => levelUI.ShowGameLoseUI();

		//previous code
    private void LoadNextLevel()
    {
        //previous code

        if(currentSceneIndex + 1 < totalNumberOfScenes)
            SceneManager.LoadScene(currentSceneIndex + 1);
        else
            levelUI.ShowGameWinUI();
    }
}
```



> **TODO**: 
> ✅ Update your `LevelManager` script
> ✅ Test the win and lose scenarios in your game





That’s it your Game Over UI is almost ready!

Almost?!🤨

Well, the Main Menu button is still not functional!

But to make it functional, you need to create the Main Menu first!!

In the next lesson, you’ll create the Main Menu UI!
