This lesson is going to be a quick creation of the Game Over UI!

Here’s how the Game Over UI looks:



![Game Over UI](//outscal.github.io/Full-Stack-Game-Development/images/71d41ea75ac9a63d.png)

**Game Over UI**



## Setting Up the Game Over Panel


---



Firstly, you need to set up a panel for Game Over UI

- Create a new `Panel` under `Canvas_Level`
- Set the panel's background to a dark color.




<iframe src="https://www.loom.com/embed/a78ea5ba716648c7bc9255526bb37846" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> TODO: 
> ✅ Create `Panel`, rename to `GameOver_Panel` 
> ✅ Set Image color to a dark color.



Now, you need a text at the center of the panel!



## Adding the "Game Over" Text


---



You can add the text using the below steps:

- Add a `TextMeshPro` component to the panel
- Set the text.
- Center the text on the screen using Anchor Preset




<iframe src="https://www.loom.com/embed/967889864133450b94f4cc70b492bffd" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO**: 
> ✅ In `GameOver_Panel` add `Text-TextMeshPro`, rename to `GameOverText` 
> ✅ Set text to Game Over, color to red, font size to 50 
> ✅ Set `Anchor Preset` to `middle-center`



It’s time add a new UI element: Buttons!



## Adding Buttons


---



> 📖 🎮** UNITY DICTIONARY** 
> ***Button***: "A UI element that responds to a click or touch event by executing assigned functionality."



Here’s how you can create a button:




<iframe src="https://www.loom.com/embed/0c34ee1ee54d4530be6fa45e185a98a4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





- Right-click on `GameOver_Panel`→ `UI`→ `Button-TextMeshPro`
- Rename to `RestartButton`, change the text to `RESTART`, set its `Anchor Preset` to `Top-Left`.
- Duplicate button (Ctrl+D), rename to `MenuButton`, set it `Anchor Preset` to `Top-Right`, delete the text and Image component and assign the image from `Assets/Sprites/UI`
- Adjust Height and Width for easy clicking
- Use Position Y to space vertically



> **TODO**: 
> ✅ Create Restart and Menu buttons from UI 
> ✅ Position the buttons on the screen using Anchor Presets



You have successfully added the Buttons!

But for the buttons to work, make sure the `Event System` is present in the `Hierarchy`.



## What’s an Event System?


---



> 📖 🎮 UNITY DICTIONARY 
> ***Event System***: "A Unity component that manages input and event handling for UI elements."



The Event System is crucial for interactive UI elements like buttons. It:

- Detects user inputs (mouse clicks, touch, keyboard)
- Determines which UI element is being interacted with
- Triggers appropriate responses (e.g., button clicks)



> **PRO TIP**💡: 
> If your UI isn't responding to input, check if an Event System is present in your scene.



Unity automatically creates an Event System when you add your first UI element. You typically don't need to modify it, but understanding its role is important.



## Disabling the Game Over Panel


---



Now, you need to disable the Game Over Panel in the Inspector.

You won’t want the players always to see the Game over panel.

- Select the `GameOver_Panel` in the `Hierarchy`
- Disable the `GameObject` in the Inspector




<iframe src="https://www.loom.com/embed/652d686e0eb24414a968e73ef9e93775" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO**: 
> ✅ Uncheck the checkbox next to `GameOver_Panel` in the `Inspector`. 
> ✅ In the `Assets/Prefabs/UI` folder, prefab the `Canvas_Level`.





Great job! You've set up a complete Game Over UI with interactive buttons.

Next, you'll code the logic to display this UI when the game ends and handle button clicks.
