You have implemented the **Undo** functionality in all your unit commands by now but who is going to use this functionality?



To invoke the execute or undo functionality on any command object is the job of Command Invoker. It maintains a stack of all the previously used command. 

If you want to undo the last command, you will need to pop the command on top of the stack (command registry), as it is the command which was executed most recently and call the Undo() method on it.



Open your Command Invoker script and create an Undo() method which implements the above logic.

```javascript
public void Undo()
{
    commandRegistry.Pop().Undo();
}
```



There are a couple of edge cases in this which will cause some bugs in our game. Can you detect them and fix it?

![](//outscal.github.io/Full-Stack-Game-Development/images/48d3a4f0340db4ab.gif)





















Click here to check bugs in the above code:- If the command registry is empty you will get a stack underflow exception. You will need to add a base check for this before performing a pop() operation on the stack.
- If the last executed command does not belongs to the current active player, you don't want to Undo that command.
- A player should only be able to Undo() it's own Unit Actions not the other player's action.



Create 2 helper methods inside command invoker names `**RegistryEmpty()**` and `**CommandBelongsToActivePlayer()**` both of them should return a Boolean:

```javascript
private bool RegistryEmpty() => commandRegistry.Count == 0;

private bool CommandBelongsToActivePlayer() 
{
		(commandRegistry.Peek() as UnitCommand).commandData.ActorPlayerID == GameService.Instance.PlayerService.ActivePlayerID;
}
```



Using these methods, add some checks inside the Undo() method of Command Invoker:

```javascript
public void Undo()
{
		if (!RegistryEmpty() && CommandBelongsToActivePlayer())
    commandRegistry.Pop().Undo();
}
```



Now you have almost implemented Undo mechanic in your game. All you need to do is call this **Undo()** method.



![](//outscal.github.io/Full-Stack-Game-Development/images/a2dde8831fa3abfd.gif)



In the next section you will see how you can modify your UI Logic and invoke an event which will undo the last performed unit action of the current active player.
