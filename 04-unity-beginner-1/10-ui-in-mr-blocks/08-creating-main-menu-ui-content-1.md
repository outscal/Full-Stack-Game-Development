In this lesson, you'll create a Main Menu for Mr. Blocks.

Your menu will include a title, two buttons (Play and Quit), and a background image.

To create the menu, you need to create a new scene.



# Creating Main Menu Scene


---



In Unity, each major section of your game, like the main menu, typically has its own scene. This helps organize your project and manage game states more effectively.




[Watch video](https://www.loom.com/embed/a40508ce74c84f4dbe7ec78ee510921d?sid=df2f38f4-2329-4abb-87d6-b91d615b9b4c)





> TODO: 
> ✅ Go to File → New Scene (or use the shortcut Ctrl+N) 
> ✅ Choose 'Basic (Built-in)' template 
> ✅ Save the scene (File → Save As...) and name it `MainMenu` 
> ✅ Add the `MainMenu` scene in the build settings. Make sure its the first scene in the build settings



Now, to start creating the main menu, you need to understand Unity’s `Canvas`



# Creating a Canvas


---

Here’s how you can create a canvas:

In the Hierarchy, (Create → UI → Canvas) Rename it to "`Canvas_MainMenu`"



> TODO: 
> ✅ Create a new `Canvas` and rename it to `Canvas_MainMenu`



Now, you must set up the canvas to be consistent for different resolutions!

You can do this using the `Canvas Scaler` component of the `Canvas` game object.



## Configuring Canvas Scaler


---

You need to set the `UI scale mode` to `**Scale With Screen Size**`



> 💡 PRO TIP: 
> Scale With Screen Size: Makes UI elements bigger the bigger the screen is.



In the Canvas Scaler component, you can see there are some properties.

Here are the important ones:

- **Reference Resolution: (Recommended: 1920 X 1080)** The resolution the UI layout is designed for. If the screen resolution is larger, the UI will be scaled up, and if it's smaller, the UI will be scaled down.
- **Match:(Recommended: 0.5)** Determines if the scaling is using the width or height as reference, or a mix in between



> **TODO:** 
> ✅ Configure Canvas Scaler settings



The canvas is now set up.

It’s time to add UI elements to the canvas!



# Adding a background image


---

You need a background image for the main menu!

Now, you need to make this background fill the entire screen.

To fill the entire screen, its Anchor preset should `Stretch-Stretch`




[Watch video](https://www.loom.com/embed/1c9362035a11422a98497a24df875be5?sid=8bc2722b-6156-4232-805e-8faded6cf311)





> TODO: 
> ✅ Right-click on the `Canvas` in the `Hierarchy` 
> ✅ Select `UI → Image` 
> ✅ Rename it to "`MainMenuBG`" 
> ✅ Assign `Assets/Sprites/UI/Mr_Blocks_Menu` to the `Source Image` of the `Image` component. 
> ✅ Set the Anchor Preset to `Stretch-Stretch`.



It’s time to add the Title Text in the Main Menu!



# Adding Title Text


---

The title can be added using `Text-TextMeshPro` in the top-center of the background image.



> TODO: 
> ✅ Right-click on the Canvas in the `Hierarchy` 
> ✅ Select `UI`→ `Text - TextMeshPro` 
> ✅ Rename it to "TitleText"



Let's configure our title:



> TODO: 
> ✅ Set the text to "MR. BLOCKS" 
> ✅ Choose a fun, bold font 
> ✅ Set the font size to something large (like 72) 
> ✅ Set the color to something eye-catching 
> ✅ Set the Anchor Preset to `Top-Center` and adjust the position of the Title



# Adding Buttons


---

Now you need to create the `Play` and `Quit` buttons:




[Watch video](https://www.loom.com/embed/76b1277220e547ff9bebfef821bc4bb3?sid=7dfbe8b7-3404-46c8-904e-787f0f8873d2)





> TODO: 
> ✅ Right-click on the `Canvas_MainMenu` → `UI`→ `Button - TextMeshPro` 
> ✅ Rename it to `PlayButton` 
> ✅ Change the button text to `PLAY` 
> ✅ Duplicate the button (Ctrl+D) 
> ✅ Rename the duplicate to `QuitButton` 
> ✅ Change its text to `QUIT`



Now, position these buttons using Anchor Presets and adjust the Height and width of the buttons.



> TODO: 
> ✅ Select both buttons in the Hierarchy 
> ✅ In the `RectTransform` component, set the Anchor Preset to `Middle Center` 
> ✅ Adjust the `Height` and `Width` to make them easily clickable 
> ✅ Use the Position Y property to space them vertically



Your Main Menu UI is ready!

Now, you need to add functionalities for the buttons!

But before that, you need to complete the Game Over UI.

Remember the Menu button in the Game Over UI is still not functional?!



# Completing The Game Over UI


---

Currently, the level manager is handling the loading of different levels.

So to load the Main Menu also you need to add a functionality in the Level Manager.



> **TODO**: 
> ✅ In the `LevelManager.cs` implement a `public void LoadMainMenu()`



Click here to see the solution.

```csharp
using UnityEngine;
using TMPro;
using UnityEngine.SceneManagement;
using UnityEngine.Serialization;

public class LevelManager : MonoBehaviour
{
    private const int mainMenuIndex = 0;
    //previous code
    
    public void LoadMainMenu() => SceneManager.LoadScene(mainMenuIndex);
    
}

```





Now, you can complete the Game Over UI using `LoadMainMenu()` method.



```csharp
using TMPro;
using UnityEngine;
using UnityEngine.UI;

public class LevelUI : MonoBehaviour
{
    public Button menuButton;
		//previous code
    private void AddListeners()
    {
        menuButton.onClick.AddListener(MainMenuButton);
        restartButton.onClick.AddListener(RestartButton);
    }

    private void MainMenuButton()
    {
        levelManager.LoadMainMenu();
    }
}
```



> TODO: 
> ✅ Complete the `LevelUI.cs` script.



Your Game Over UI is now complete!!

Now, it’s time to complete the Main Menu UI!
