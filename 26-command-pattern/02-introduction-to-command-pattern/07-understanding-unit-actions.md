Now that you have an idea about the architecture of the current project, you need to understand where does Command Pattern fits in this.



To figure that out you first need to understand how Units communicate with the Action Service when they need to Perform an Action. 

So open up `ActionService.cs` and lets take a look at it.



Before we dive into this scripts, you might already be wondering why do we need a separate Service for Actions? 

Actions are just a part of Unit behavior so shouldn't the logic to execute these actions be inside the `UnitController` itself?



Its a valid question and certainly we can have implement it that way, but its not the most optimal way to do things and it also violates some of our Object Oriented Principles. Lets see how:



Imagine that a designer in the company you work for requests you to make a Unit called a **Wizard** which would have the following 2 Actions, **Attack & Heal**

So you create a `**WizardController.cs**` with all the Unit related logic in it along with two extra methods: 

- `**Attack()**`
- `**Heal()**`



Now you get another request to create a **Mage** with **Attack & Heal** which have the same logic as before. So you create a `**MageController**`** **with the methods:

- `**Attack()**`
- `**Heal()**`



Again you get a request to make a **Healer** Unit with the Actions **Heal & Cleanse. **So again you create a `**Healer.cs**`** **with the following methods:

- `**Heal()**`
- `**Cleanse()**`

![](//outscal.github.io/Full-Stack-Game-Development/images/6ac89fe44f69afb5.png)



Doing so, not only you are repeating the code inside these methods, but you are also restricting your code architecture. 

Consider that in future your designer friend comes to you and say that the Wizard does not need to perform Attack and Heal actions, instead it should now perform some other new Actions, you will need to open up your `WizardController.cs` and change those methods. 

It doesn't stop here. Now you designer friend wants to define a different kind of behavior for the Attack Action. And that means that whenever you need to modify a behavior, you’re forced to track down and change it in all the different classes where that behavior is defined, probably introducing new bugs along the way!

Luckily there is an object oriented design principle just for this situation:



> ***Identify the aspects of your application that vary and separate them from what stays the same.***



In other words, if you’ve got some aspect of your code that is changing, say with every new requirement, then you know you’ve got a behavior that needs to be pulled out and separated from all the stuff that doesn’t change.



Following the above principle, we should pull out Action behavior from the Unit class. Since apart from the Action behavior, all the other logic inside all Unit Controllers remain the same, we can represent each Unit with a common `**UnitController.cs**` script. 



You can have numerous kinds of Actions but they all follow a common set of rules. So lets define these set of rules inside an `**IAction**`** **interface 

```javascript
// An interface indicating a unit action.
public interface IAction
{
    // Get the type of target this action requires.
    TargetType TargetType { get; }

    // Perform the action with the given actor and target units.
    void PerformAction(UnitController actorUnit, UnitController targetUnit);

    // Check if the action was successfully executed.
    bool IsSuccessful();

    // Calculate the position to move to when targeting a specific unit.
    Vector3 CalculateMovePosition(UnitController targetUnit);
}
```

We have `TargetTypes` declared in the above code snippet which are defined as follows:

```javascript
// Enum representing the type of target for a unit action.
public enum TargetType
{
    Friendly,
    Enemy,
    Self
}
```



There are going to be many different types of actions which will implement this interface. So lets define the them in an enum:

```javascript
public enum ActionType
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



Here is a quick overview of what each Action does:

- **Attack ⇒ **A base attack for a unit. Simply damages the target.
- **Attack Stance ⇒ **Increases attack power for the battle by 20%
- **Heal ⇒ **Heals a friendly unit.
- **Meditate ⇒ **Increases maximum health for the battle by 20%
- **Third Eye ⇒** Converts 25% of current health into additional Power.
- **Cleanse ⇒** Removes target’s buff (20% hit chance)
- **Berserk Attack ⇒** 2x attack power but a 33% chance to damage itself instead of enemy.



```javascript
/// <summary>
/// Class representing an attack action, implementing the IAction interface.
/// </summary>
public class AttackAction : IAction
{
    private UnitController actorUnit;
    private UnitController targetUnit;

    // Indicate that this action targets enemies.
    public TargetType TargetType => TargetType.Enemy;

    /// <summary>
    /// Perform the attack action with the given actor and target units.
    /// </summary>
    public void PerformAction(UnitController actorUnit, UnitController targetUnit)
    {
        this.actorUnit = actorUnit;
        this.targetUnit = targetUnit;

        // Play the attack animation and specify the move position and callback for animation completion.
        actorUnit.PlayBattleAnimation(ActionType.Attack, CalculateMovePosition(targetUnit), OnActionAnimationCompleted);
    }

    /// <summary>
    /// Callback function called when the action animation is completed.
    /// </summary>
    public void OnActionAnimationCompleted()
    {
        if (IsSuccessful())
            targetUnit.TakeDamage(actorUnit.CurrentPower);
        else
            GameService.Instance.UIService.ActionMissed();
    }

    /// <summary>
    /// Check if the attack action is successful. In this case, it always returns true.
    /// </summary>
    public bool IsSuccessful() => true;

    /// <summary>
    /// Calculate the move position when targeting a specific unit (enemy).
    /// </summary>
    public Vector3 CalculateMovePosition(UnitController targetUnit) => targetUnit.GetEnemyPosition();
}
```



Similarly, all other Action classes have been made which implement the `**IAction**` interface and contains the logic to perform that action when requested.

Now open `**ActionService.cs**`** **and you will see that in its constructor we are creating objects of our all our action classes and mapping these objects with an Action Type.

```javascript
/// <summary>
/// Service class responsible for managing and providing different types of actions.
/// </summary>
public class ActionService
{
    private Dictionary<ActionType, IAction> actions;

    /// <summary>
    /// Constructor for the ActionService. Initializes and creates actions.
    /// </summary>
    public ActionService() => CreateActions();

    /// <summary>
    /// Creates and populates the dictionary of actions.
    /// </summary>
    private void CreateActions()
    {
        actions = new Dictionary<ActionType, IAction>();
        actions.Add(ActionType.Attack, new AttackAction());
        actions.Add(ActionType.Heal, new HealAction());
        actions.Add(ActionType.AttackStance, new AttackStanceAction());
        actions.Add(ActionType.Cleanse, new CleanseAction());
        actions.Add(ActionType.Meditate, new MeditateAction());
        actions.Add(ActionType.BerserkAttack, new BerserkAttackAction());
        actions.Add(ActionType.ThirdEye, new ThirdEyeAction());
    }

    /// <summary>
    /// Get an action based on its ActionType.
    /// </summary>
    /// <param name="type">The type of action to retrieve.</param>
    /// <returns>The IAction instance corresponding to the provided type.</returns>
    public IAction GetActionByType(ActionType type)
    {
        if (actions.ContainsKey(type))
            return actions[type];
        else
            throw new System.Exception($"No Action found for the type {type} in the dictionary");
    }

    /// <summary>
    /// Get the target type associated with a specific action type.
    /// </summary>
    /// <param name="actionType">The type of action to retrieve the target type for.</param>
    /// <returns>The TargetType associated with the provided action type.</returns>
    public TargetType GetTargetTypeForAction(ActionType actionType) => actions[actionType].TargetType;
}
```



With creating a separate Action Service class we have successfully separated all the action related logic from the Unit Controller. 
All that the Unit Controller needs to have is a reference of what type of actions it can execute.

```javascript
public class UnitScriptableObject : ScriptableObject
{
	.....
	public List<ActionType> executableCommands;
	.....
}
```

This can be changed by the designer in the scriptable object and that's all you will need to do.



![](//outscal.github.io/Full-Stack-Game-Development/images/8090e6be9d2874ca.png)



Now whenever a Player selects an action in the UI to perform, it can just ask the `**ActionService**`** **to do so. Here is how `**PlayerController**`** **does it in the below method: 

```javascript
/// <summary>
/// Perform the selected action on a target unit.
/// </summary>
/// <param name="actionSelected">The type of action to be performed.</param>
/// <param name="targetUnit">The target unit on which the action is performed.</param>
public void PerformAction(ActionType actionSelected, UnitController targetUnit)
{
    // Get the action by its type from the ActionService and perform it on the active player's unit.
    GameService.Instance.ActionService.GetActionByType(actionSelected).PerformAction(activePlayer.GetUnitByID(ActiveUnitID), targetUnit);
}
```



Now that you have understood how the current architecture works for unit Actions, lets get to our original doubt that we asked in the beginning of this section.

How does Command Pattern fits in all this?



Like in our restaurant example in previous section, where we had a customer which requested for something he desired, here in our game we have a Client (`**PlayerController**`) which desires for an action to be performed on a specific Unit (**Receiver**) 

The problem is that currently there is no mediator like a waiter involved. So the Client is directly telling the Receiver to Perform an Action. 

Since there is no waiter, nobody is creating any Order Slips (**Commands**). There is no record being maintained of Actions being performed.



The Waiter in this analogy is a missing **Command Invoker** and Order Slips are **Commands **if we simply create and fit these 2 missing components we will have implemented Command Pattern in our project and then we can use it to our advantage for implementing exciting mechanics in our game like **Undo** and **Replay.**



In the next section, we will start creating some **Abstract Commands** that can be used to encapsulate method calls to perform unit actions.
