As we saw in the previous section, once our Player selects the Action and Target, 

- The Input Service being the **Client **creates an instance of the required unit command 
- And passes its reference to the GameService to process it.

![](/Full-Stack-Game-Development/images/36acb7968068e7bb.png)



So open `**InputService.cs**` and refactor it accordingly. Go to the method called `**OnTargetSelected(UnitController targetUnit)**` and see what's happening inside that method:

```javascript
public void OnTargetSelected(UnitController targetUnit)
{
    // Set the input state to EXECUTING_INPUT when a target unit is selected.
    SetInputState(InputState.EXECUTING_INPUT);
    
    // This line triggers the execution of the selected action (selectedActionType) on the target unit.
    GameService.Instance.PlayerService.PerformAction(selectedActionType, targetUnit);
}
```



You need to remove the second line of code in this method which calls the `**PerformAction()**` method on `**PlayerService**`. Instead you need to create a new command and then pass it to the GameService for processing it further.

```javascript
public void OnTargetSelected(UnitController targetUnit)
{
    // Set the input state to EXECUTING_INPUT when a target unit is selected.
    SetInputState(InputState.EXECUTING_INPUT);
    
    // Create a UnitCommand based on the selected target unit.
    UnitCommand commandToProcess = CreateUnitCommand(targetUnit);

    // This line passes the created command to the GameService for further Processsing.
    GameService.Instance.ProcessUnitCommand(commandToProcess);
}
```



But you have neither defined a method called `**CreateUnitCommand()**` in Input Service yet nor a method called `**ProcessUnitCommand()**` in Game Service. 

So define those methods first.



To create a Unit Command, you will first need to prepare an instance of `**CommandData**` to pass in the constructor. 

```javascript
private CommandData CreateCommandData(UnitController targetUnit)
{
    // Create CommandData with the necessary information for a UnitCommand.
    // It includes the ActiveUnit's ID, TargetUnit's ID, ActivePlayer's ID, and the TargetPlayer's ID.
    return new CommandData(
        GameService.Instance.PlayerService.ActiveUnitID,
        targetUnit.UnitID,
        GameService.Instance.PlayerService.ActivePlayerID,
        targetUnit.Owner.PlayerID
    );
}
```



Start by creating a Unit Command in the `**CreateUnitCommand()**` method as follows:

- Create Command Data based on the selected target unit.
- According to the command type selected by player to execute, create an instance of the corresponding Unit Command

```javascript
private UnitCommand CreateUnitCommand(UnitController targetUnit)
{
    // Create the necessary CommandData based on the target unit.
    CommandData commandData = CreateCommandData(targetUnit);

    // Based on the selected command type, create and return the corresponding UnitCommand.
    switch (selectedCommandType)
    {
        case CommandType.Attack:
            return new AttackCommand(commandData);
        case CommandType.Heal:
            return new HealCommand(commandData);
        case CommandType.AttackStance:
            return new AttackStanceCommand(commandData);
        case CommandType.Cleanse:
            return new CleanseCommand(commandData);
        case CommandType.BerserkAttack:
            return new BerserkAttackCommand(commandData);
        case CommandType.Meditate:
            return new MeditateCommand(commandData);
        case CommandType.ThirdEye:
            return new ThirdEyeCommand(commandData);
        default:
            // If the selectedCommandType is not recognized, throw an exception.
            throw new System.Exception($"No Command found of type: {selectedCommandType}");
    }
}

```



After creating your command you will pass it to the Game Service for further processing.



In the next section you will see how Game Service and other components are going to process this command and how is it going to be invoked by the Command Invoker.
