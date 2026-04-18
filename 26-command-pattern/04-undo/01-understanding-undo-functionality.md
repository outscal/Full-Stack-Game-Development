> It’s time to create a new feature branch for the upcoming game features.

> 

> Make a new feature branch out of your main branch called → **[ **`**Feature-3-Undo**`** ]**

> Let’s start working on the new feature now!



You've already implemented the Command Pattern in your game development project, but you haven't harnessed its power for features like **Undo** or **Replay**. 



Consider games like **Civilization** or **Chess**. In these turn-based strategy games, every action taken, from moving a unit to launching an attack, is encapsulated as a command. The game maintains a list of these commands in chronological order. If you regret a move or decision, the game simply takes the command on top of the stack and reverses it. Voila, you've undone your action! This is an elegant application of the Command Pattern in gaming. It's all about capturing player actions as commands and having the power to rewind the game whenever you want. Its like going back in time and correct your past mistakes.



![](https://tenor.com/view/flashpoint-paradox-gif-22362407.gif)



In your existing Command Pattern, you have classes that represent various unit actions in your game. These classes encapsulate the logic required to execute these actions. Now, it's time to repurpose them for the undo functionality. Here is what you will be able to do after the end of this chapter:




<iframe src="https://www.loom.com/embed/920aefdb12604991870feb228f6422e6" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





You have created a Stack (**Command Registry**) that stores these command objects. When a player chooses to performs an action, you push the corresponding command on top of the stack.



Each Command object right now has a method to **Execute()** itself. To enable the **Undo** feature, you need to implement a method that can reverse the last command. When the player chooses to undo an action, pop the last command from the stack and call its **undo()** method.



Each command class should have an **Undo()** method that knows how to reverse the action it originally performed. For example, if the command was to move the player forward, the **Undo()** method should move the player backward.



Since it is going to be a common method for all commands. Lets add it in our abstract command classes, `**ICommand**` and `**UnitCommand**`**.** For now, you just need to declare a method called **Undo()** we will implement it later.



```javascript
public interface ICommand
{
    public void Execute();

    public void Undo();
}
```



```javascript
public abstract class UnitCommand : ICommand
{
    ....
		....
	  public abstract void Undo();
		....
		....
}
```



In the next section you are going to implement this Undo() method according to each unit action's logic.
