> It’s time to create a new feature branch for the upcoming game features.

> 

> Make a new feature branch out of your main branch called → **[ **`**Feature-2-Using-Commands**`** ]**

> Let’s start working on the new feature now!



Lets think about how your new architecture and communication flow after implementing concrete commands would look like.



In the updated communication flow the unit which wants to perform an action will tell the Command Invoker to Process a command. Below is the detailed flow of how each piece will communicate with each other:



![](/Full-Stack-Game-Development/images/198d8f254e1bdd0c.png)



- First the Player selects the desired Action and Target.
- The Input Service, acting as a **Client**, creates a **Command** based on the selected Action and Target.
- The Input Service passes the Command to the Game Service for processing.
- The Game Service then passes the Command to the Player Service, Player Controller, and Unit Controller for further processing.
- Each class adds relevant data to the Command object during processing, such as Actor and Target Unit IDs.
- The Unit Controller requests the **Command Invoker** to process the Command.
- The Command Invoker registers and calls the Execute() method of the Command.
- The Command itself has an encapsulated method call to perform an action. 
- When Execute() is called, it invokes the encapsulated method `**ActionService.PerformAction(ActionType)**`
- Action Service fetches the corresponding instance of `**IAction**` and it takes care of executing that Unit Action logic.
- The Command remains stored in the Command Invoker's registry for potential future use.



Now, to implement this architecture, start by renaming "`**ActionType**`" to "`**CommandType**`" in your project. Ensure all references to this Enum are updated.

```javascript
public enum CommandType
    {
        None,
        Attack,
        Heal,
        AttackStance,
        Cleanse,
        Meditate,
        BerserkAttack,
        ThirdEye
    }
```

The types of Commands will align with the previous Action types, as you're creating commands for Unit Actions exclusively.

![](/Full-Stack-Game-Development/images/302712d77c275354.gif)



Before you jump right into making concrete commands, you need to first refactor your abstract commands and Actions a little.

Open your `UnitCommand` class that you created earlier and take a good look at it. There are a few fields for storing the IDs of Players and Units involved in this Unit Command. 

```javascript
public abstract class UnitCommand : ICommand
{
    // Fields to store information related to the command.
    public int ActorUnitID;
    public int TargetUnitID;
    public int ActorPlayerID;
    public int TargetPlayerID;
		
		.....
		.....
		.....
		
}
```

Each Unit Command will need these 4 IDs for executing itself. So lets encapsulate it in a struct. 



Create a struct called `**CommandData**`** **with the above** **properties and simply create an instance of that struct in your `**UnitCommand**` class

```javascript
public struct CommandData
    {
        public int ActorUnitID;
        public int TargetUnitID;
        public int ActorPlayerID;
        public int TargetPlayerID;

        public CommandData(int ActorUnitID, int TargetUnitID,int ActorPlayerID, int TargetPlayerID)
        {
            this.ActorUnitID = ActorUnitID;
            this.TargetUnitID = TargetUnitID;
            this.ActorPlayerID = ActorPlayerID;
            this.TargetPlayerID = TargetPlayerID;
        }
    }
```



Along with an instance of `CommandData` you have references of Actor Unit and Target Unit in your `UnitCommand.`

But how are these values going to be set? Create a Setters for these unit references in your Abstract Command. Your refactored Unit Command should look like this:

```javascript
public abstract class UnitCommand : ICommand
{
    public CommandData commandData;

    protected UnitController actorUnit;
    protected UnitController targetUnit;

    public abstract void Execute();

    public abstract bool WillHitTarget();

    public void SetActorUnit(UnitController actorUnit) => this.actorUnit = actorUnit;

    public void SetTargetUnit(UnitController targetUnit) => this.targetUnit = targetUnit;
}
```



You must have noticed there is a method called `WillHitTarget()` declared above. This method's implementation will decide whether a unit action will successfully hit its target or not. A similar kind of method was already present in your `**IAction**` class. Open it and check. So why do you need to have it in the `**UnitCommand**`** **instead of `**IAction**`?



The `WillHitTarget()` method is used to determine whether a unit action will hit its target. Storing this information in the Command class ensures consistent results when executing the same command multiple times.



Since you have added this method in `UnitCommand` open `IAction` and remove the `IsSuccessful()` method. You don't need that there anymore. Instead we will pass a Boolean called `isSuccessful` in `PerformAction()` as follows:

```javascript
public interface IAction
{
    public TargetType TargetType { get; }

    public void PerformAction(UnitController actorUnit, UnitController targetUnit, bool isSuccessful);

    public Vector3 CalculateMovePosition(UnitController targetUnit);
}
```



Since you have updated your IAction interface you will need to update all Action classes accordingly.

- Open each implementation of IAction and remove the implementation of `**IsSuccessful()**` method.
- Update the `**PerformAction()**` method to take in a boolean as an argument and and store it in a property by the name of `**isSuccessful**`.
- We will use this property when needed.



Your `**AttackAction.cs**` should look like follows after refactoring:

```javascript
public class AttackAction : IAction
{
    private UnitController actorUnit;
    private UnitController targetUnit;
    private bool isSuccessful;
    public TargetType TargetType => TargetType.Enemy;

    public void PerformAction(UnitController actorUnit, UnitController targetUnit, bool isSuccessful)
    {
        this.actorUnit = actorUnit;
        this.targetUnit = targetUnit;
        this.isSuccessful = isSuccessful;

        actorUnit.PlayBattleAnimation(CommandType.Attack, CalculateMovePosition(targetUnit), OnActionAnimationCompleted);
    }

    public void OnActionAnimationCompleted() 
    {
        if (isSuccessful)
            targetUnit.TakeDamage(actorUnit.CurrentPower);
        else
            GameService.Instance.UIService.ActionMissed();
    }

    public Vector3 CalculateMovePosition(UnitController targetUnit) => targetUnit.GetEnemyPosition();
}
```

Similarly update the rest of your Action classes.



Now you are all setup to create concrete Unit Commands for each Action. 

![](/Full-Stack-Game-Development/images/a273aed1b499e6e2.gif)



Let's get it done. 

- Start by creating a `**AttackCommand**` class inside Commands folder which inherits the `**UnitCommand**`.
- In the constructor you will get an instance of `**commandData**` which will be cached for later use. 
- You will need to calculate if it will hit the target or not in the constructor itself so call the `**WillHitTarget()**`** **method and store the value in a Boolean for later use.
- You need to implement this method as well. Since we want that our Attack Action is always successful, we will simply return the value as true.
- In case you wish to have a chance factor involved for this action, you will need to accordingly calculate that chance and update the Boolean.
- Finally implement the `**Execute()**` method in Action Command. Fetch the instance of `**AttackAction**` from `**ActionService**` and invoke its `**PerformAction()**` method. Pass the necessary data as arguments



```javascript
public class AttackCommand : UnitCommand
{
    private bool willHitTarget;

    public AttackCommand(CommandData commandData)
    {
        this.commandData = commandData;
        willHitTarget = WillHitTarget();
    }

    public override bool WillHitTarget() => true;

    public override void Execute() => GameService.Instance.ActionService.GetActionByType(CommandType.Attack).PerformAction(actorUnit, targetUnit, willHitTarget);
}
```



Similarly go ahead and create concrete command classes for the following unit actions as well:

- Heal
- Attack Stance
- Berserk Attack
- Meditate
- Cleanse
- Third Eye



In the next section you will see how to create instances of commands in the input service according to player's selected Action.
