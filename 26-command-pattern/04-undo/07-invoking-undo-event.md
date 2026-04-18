The first thing you need is an Undo Button to interact with. This will a part of your gameplay UI, So open your `**GameplayUIView**` and add a `SerializeField` for a new Button. Call this the `undoButton`. 



Since all the business logic resides inside the Controller, create a method called `OnUndoButtonClicked()` in your `**GameplayUIController**` and set this as a listener to the `undoButton` in `**GameplayUIView**`.



```javascript
public class GameplayUIView : MonoBehaviour, IUIView
{

    [SerializeField] Button undoButton;
    
    public void SetController(GameplayUIController controllerToSet) 
    {
        controller = controllerToSet;
        undoButton.onClick.AddListener(controller.OnUndoButtonClicked);
        missedText.canvasRenderer.SetAlpha(0);
    }
}
```



```javascript
public class GameplayUIController : IUIController
{
	.....
	.....
    public void OnUndoButtonClicked() => GameService.Instance.CommandInvoker.Undo();
}
```



Congratulations on successfully implementing the undo functionality in your game project using the Command Pattern. Go ahead and try it out. 

- Make sure you have implemented Undo() functionality in each concrete command class correctly. 
- Select any existing battle or create a new one. 
- The Undo button should be visible to you.
- Choose a unit action for your current active unit. 
- When the next unit becomes active, press the undo button.
- The first unit should become active again and it's previous turn's affects should be reverted as well.
- Try it with different units in different battles to check if everything is working correctly or not.



It's like a wizardry of the digital realm! feels like we're conjuring spells instead of writing code.



![](//outscal.github.io/Full-Stack-Game-Development/images/17f58080b3c00127.gif)



As you continue to create these digital realms, know that a little bit of black magic – or rather, coding mastery – goes into enhancing the player experience and making your game more user-friendly.



In the next chapter you will learn how you can further leverage the command pattern to implement a **Replay** functionality in your game.
