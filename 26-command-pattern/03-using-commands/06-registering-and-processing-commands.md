Continuing from where we left in the previous section, we have created and given a command to the Game Service for processing it further.



Here is a reminder of how its going to be processed:

![](/Full-Stack-Game-Development/images/183849087d6f85a3.png)

The command will pass through the player service, allowing each component to add necessary data to it.

Here is how you can do that:

```javascript
public class GameService : GenericMonoSingleton<GameService>
{
	....
	....
	public void ProcessUnitCommand(ICommand commandToProcess) => PlayerService.ProcessUnitCommand(commandToProcess as UnitCommand);
}
```



```javascript
public class PlayerService
{
	....
	....	
	public void ProcessUnitCommand(UnitCommand commandToProcess)
	{
		// Set unit references for the command.
		SetUnitReferences(commandToProcess);
	
		// Delegate unit command processing to the corresponding player.
		GetPlayerById(commandToProcess.commandData.ActorPlayerID).ProcessUnitCommand(commandToProcess);
	}
	
	private void SetUnitReferences(UnitCommand commandToProcess)
	{
		// Get actor and target units based on the command data.
		var actorUnit = GetPlayerById(commandToProcess.commandData.ActorPlayerID).GetUnitByID(commandToProcess.commandData.ActorUnitID);
		var targetUnit = GetPlayerById(commandToProcess.commandData.TargetPlayerID).GetUnitByID(commandToProcess.commandData.TargetUnitID);
	
		// Set the actor and target units for the command.
		commandToProcess.SetActorUnit(actorUnit);
		commandToProcess.SetTargetUnit(targetUnit);
	}
}
```



```javascript
public class PlayerController
{
	....
	....	
	public void ProcessUnitCommand(UnitCommand commandToProcess)
	{
		GetUnitByID(commandToProcess.commandData.ActorUnitID).ProcessUnitCommand(commandToProcess);
	}
}
```



```javascript
public class UnitController
{
	....
	....
	public void ProcessUnitCommand(UnitCommand commandToProcess) => GameService.Instance.CommandInvoker.ProcessCommand(commandToProcess);
}
```



The Unit Controller instructs the Command Invoker to process the commands.



In line with the previous Command Invoker implementation:

1. It registers and stores the command in the command registry.
2. It calls the Execute() method of that command.



That's all there is to it. You've now integrated unit commands using the Command Invoker.

Ensure your unit scriptable objects are correctly configured, especially since you renamed the `**ActionType**` Enum. 

Play the game, and it should function as before. 




<iframe src="https://www.loom.com/embed/9f4bd64a0f9840d789eaacfb7872d6b2" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





While you won't notice significant gameplay changes yet, you've successfully integrated the command pattern into your project, so congratulations!



![](/Full-Stack-Game-Development/images/6e8ff1ea6e096f87.gif)



In the next chapter, you'll discover how to utilize the implemented command pattern for advanced game mechanics like **Undo** and **Replay**.
