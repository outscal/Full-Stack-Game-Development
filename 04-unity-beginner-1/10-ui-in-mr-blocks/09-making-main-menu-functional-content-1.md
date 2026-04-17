## Defining Button Functions


---

First, let's create a script with the functions our buttons will use:

Play Button: Loads the first level

Quit Button: Quits the game.



> **TODO**: 
> ✅ Create a new script called `MainMenuUI` and open it 
> ✅ Define the `int firstLevel` constant 
> ✅ Implement the Play and Quit methods



```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class MainMenuUI : MonoBehaviour
{
    private const int firstLevel = 1;  // Define the first level to load

    public void Play()
    {
        SceneManager.LoadScene(firstLevel);  // Load the first level
    }

    public void Quit()
    {
        Application.Quit();  // Quit the game
        Debug.Log("Game quit"); // Unity doesn't quit in the editor, so we log it
    }
}
```



Now, you already know how to add listeners for the buttons.

But, there’s one more method to add listeners for buttons!



## Adding Listeners using the Inspector


---

This method is quick and easy, perfect for simple projects:



🎥 Video Placeholder: Setting up button functionality using the Inspector



> **TODO**: 
> ✅Attach the `MainMenuUI` script to your `Canvas_MainMenu` 
> ✅Set up the Play button:
> 
> - Select the Play button in the `Hierarchy`
> - In the `Inspector`, in the `Button` component and the `OnClick()` section
> - Click '+' to add a new event
> - Drag the Canvas (with `MainMenuUI` script) into the object field
> - Select `MainMenuUI` > `Play()` from the function dropdown
> 
> ✅Repeat the process for the Quit button, but select `Quit()` function



> 💡 **PRO TIP**: 
> The Inspector method is great for quick setups, but it can be harder to manage in larger projects.



## Adding Listeners Using a Script


---

For more control and easier management in larger projects, you can add listeners for the buttons in the `MainMenuUI` script:



> **TODO**: 
> ✅ Add public Button variables for `playButton` and `quitButton` 
> ✅ Implement the `Awake` method to initialize listeners 
> ✅ Implement the `AddListeners` method



Click here to see the solution.

`MainMenuUI.cs`

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;
using UnityEngine.UI;

public class MainMenuUI : MonoBehaviour
{
    public Button playButton;
    public Button quitButton;

    private const int firstLevel = 1;

    private void Awake()
    {
        AddListeners();
    }

    private void AddListeners()
    {
        playButton.onClick.AddListener(Play);
        quitButton.onClick.AddListener(Quit);
    }

    // Play and Quit methods remain the same
}
```





After saving your script:



> **TODO**: 
> ✅ Attach the `MainMenuUI` script to your Canvas 
> ✅ In the `Inspector`, assign your `Play` and `Quit` buttons to the respective fields 
> ✅ Test your Main Menu functionality



That's it! Your Main Menu is now functional. 🎉



## Which Method to Choose?


---

- Use the Inspector method for quick prototypes or simple UIs.
- Use the script method for larger projects or when you need more control.



In the next chapter, you’ll learn about sound in games!
