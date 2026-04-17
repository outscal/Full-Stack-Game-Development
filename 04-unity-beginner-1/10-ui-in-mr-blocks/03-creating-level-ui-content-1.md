You'll create a Level UI for Mr. Blocks using Unity's UI system.

Your level UI will include a level number, and a game over UI.

In this lesson, you’ll display the level number.

To create the level UI, you need to create a new canvas.

What’s a Canvas?🤔



# Understanding the Canvas


---



Everything you want to display on the screen needs to be a child of the Canvas.



> 📖 🎮 **UNITY DICTIONARY **
> **Canvas:** "A GameObject in Unity that acts as a container for all UI elements. It manages the rendering and scaling of UI across different screen sizes and resolutions."



Now that you understand the canvas, it’s time to create one!



# Creating a Canvas


---

Here’s how you can create a canvas:

In the `Hierarchy` create (UI → Canvas) Rename it to `Canvas_Level`



> **TODO**: 
> ✅ Create a new `Canvas`



Now, you must set up the canvas to be consistent for different resolutions!

You can do this using the `Canvas Scaler` component of the `Canvas` game object.



## Configuring Canvas Scaler


---

> 📖 🎮 **UNITY DICTIONARY** 
> **Canvas Scaler**: "The Canvas Scaler component controls the **overall scale** and **pixel density** of UI elements in the Canvas. This scaling affects everything under the Canvas, including font sizes and image borders."



You need to set the `UI scale mode` to `**Scale With Screen Size**`



> 💡 **PRO TIP**: 
> Scale With Screen Size: Makes UI elements bigger the bigger the screen is.



In the Canvas Scaler component, you can see there are some properties.

Here are the important ones:

- **Reference Resolution: (Recommended: 1920 X 1080)** The resolution is used as a reference. If the screen resolution is larger than the reference resolution, the UI will be scaled up, and if it's smaller, the UI will be scaled down.
- **Match:(Recommended: 0.5)** Determines if the scaling is using the width or height as a reference, or a mix in between




[Watch video](https://www.loom.com/embed/725414bd423b48b28fbe894b6ec1d589?sid=8daf94f0-28c2-4b4b-8d20-830927974125)





> **TODO:** 
> ✅ Configure the recommended Canvas Scaler settings



The canvas is now set up.

Now, you’ll start creating the Level UI.



# Creating the Level UI in Mr. Blocks


---

Level UI will have a separate panel under the Canvas.

Currently, it will only display the level number.

In the future, you can implement the UI for additional features like health under the level panel.



## Creating a Level Panel


---

Here’s how you can add a panel to group the UI elements:




[Watch video](https://www.loom.com/embed/73b5516957fc4a129ab4882e677445ce?sid=81220674-4452-466d-80b3-d8f400fab876)





1. Right-click on `Canvas_Level` and select `UI` → `Panel`
2. Rename it to `Level_Panel`



Now, you need to turn the panel transparent, as this is the panel that the players will see during the gameplay.

1. In the `Color` property of the `Image` Component, set the `Alpha` to 0.



> **TODO:** 
> ✅ Create a `Level_Panel` under the `Canvas_Level` 
> ✅ In the `Color` property of the `Image` Component, set the `Alpha` to 0.



Now, you need a text under this panel, to display the level number.



## Adding the Level Text


---

The level number can be displayed using `Text-TextMeshPro`:



> 📖 🎮 **UNITY DICTIONARY **
> `**Text-TextMeshPro**`: "A Unity package that provides high-quality text rendering with advanced features like custom fonts, rich text, and better performance than Unity's built-in text components."




[Watch video](https://www.loom.com/embed/4f190e0370b046ffa75ce06eafa34fa5?sid=115f75ee-f562-4d06-b479-3adeb4ee9c6d)





1. Right-click on `Level_Panel` and select `UI → Text-TextMeshPro`.
2. Rename it to `Level_Text`
3. In the `TextMeshPro - Text(UI)` component of the `Level_Text` game object:
4. - Change the text to "Level: 1".
  - Set `Font Size` to 60.
  - Set Alignment to `Center`



> **TODO:** 
> ✅ Create a `Level_Text` under the `Level_Panel`



Now, you must change the level number for different levels using a script!



## Creating the LevelUI Script


---

Time to make our level number dynamic. You'll create this script step by step.

1. Create a new script called "`LevelUI`" and open it.
2. First, you need to use `TextMeshPro`. Add the namespace for `TextMeshPro` at the top of your script:



```csharp
using UnityEngine;
using TMPro;
```



Now, you need to add the required variables. 
You need to access the level panel and the text that needs to be changed and set a level number for every level.



```csharp
public class LevelUI : MonoBehaviour
{
		public GameObject levelPanel;
    public TextMeshProUGUI levelText;
    public int levelNumber;
}
```



Next, you need a method to update the level text:

**Note: **You'll need to change the level number for all the scenes, otherwise all the levels will display Level: 1.

```csharp
private void UpdateLevelText()
{
    levelText.text = "Level: " + levelNumber;
}
```



This method can be called when the script enables:

```csharp
private void Start()
{
    UpdateLevelText();
}
```



Lastly, you need a method to hide the level panel. You’ll need to hide the panel when the `GameOverUI` appears:

```csharp
private void HideLevelPanel()
{
    levelPanel.SetActive(false);
}
```



Your final script should look like this:

`**LevelUI.cs**`

```csharp
using UnityEngine;
using TMPro;

public class LevelUI : MonoBehaviour
{
    public TextMeshProUGUI levelText;
    public int levelNumber = 1;

    private void Start()
    {
        UpdateLevelText();
    }

    private void UpdateLevelText()
    {
        levelText.text = "Level: " + levelNumber;
    }

    private void HideLevelPanel()
    {
        levelPanel.SetActive(false);
    }
}
```





> **TODO:**
> ✅ In the `Scripts/UI` folder create a `LevelUI` script.
> ✅ Implement the `LevelUI` script.



Lastly, you need to attach the script to the Canvas!



## Connecting the Script


---

1. Select your `Canvas_Level` in the Hierarchy.
2. In the `Inspector`, click `Add Component` and choose the `LevelUI` script.
3. Drag your `Level_Text` object into the `Level Text` field in the `LevelUI` component.
4. Drag your `Level_Panel` object into the `Level Panel` field in the `LevelUI` component.
5. Set the Level Number to 1 (or whichever level you're starting with).



> **TODO:** 
> ✅ Attach the `LevelUI` script to the `Canvas_Level` 
> ✅ Assign the `Level Panel`, `Level Text`, and `Level Number` variables.





Great job! You've created a dynamic Level UI for Mr. Blocks.

But, is this(Center) the best place to display the level number?🤔

Well, not really.

In the next lesson, you’ll learn about some of the properties of UI elements! 
Using these properties, you will position the level number.
