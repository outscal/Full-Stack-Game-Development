You had updated your abstract commands in the previous section due to which you might have been getting errors in all your concrete command classes since there is an **Undo()** method which has not yet been implemented. 

![](https://tenor.com/view/nre-null-reference-object-reference-null-reference-exception-null-reference-not-set-to-an-instance-of-an-object-gif-9452472525844466198.gif)



To get rid of all these errors you must implement an undo functionality for each Unit Command. Lets start with the Attack Command.  

Its a simple unit action which is successful every time and damages the target unit by actor unit's power value.



So to reverse such a behavior, you will need to do exactly the opposite. That is, 

- To **Restore** the same amount of health of the target unit.
- Go back to the previous unit's turn. Here we will need to reset the Current Active Unit.



So lets turn this into code inside the Undo() method of `**AttackCommand**`:

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

        public override void Undo()
        {
              targetUnit.RestoreHealth(actorUnit.CurrentPower);
              actorUnit.Owner.ResetCurrentActiveUnit();
        }
    }
```



In the above code we are telling the active player to reset it's current active unit. But we haven't implemented the functionality to actually do so. Lets figure out how to do that.



The player controller has the current active unit's index and a list of all the units. You need to decrement the index of the current active unit and set that unit as active instead. 



But what if that unit is already dead? You can't set a dead unit as active. That would cause weird behavior in your game. Thus, you will need to check as well whether the unit you get after decrementing the index is alive or dead, if its dead, then keep decrementing the index.




<iframe src="https://www.loom.com/embed/27cf011e9c804d6f9beedc3342f36a1c" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





Create a method called `**ResetCurrentActiveUnit()**` inside you Player Controller and write the above logic inside it.

```javascript
public void ResetCurrentActiveUnit()
{
    // Reset the unit indicator (Arrow) for the currently active unit.
    units[activeUnitIndex].ResetUnitIndicator();
    
    // Move to the previous unit in the list.
    activeUnitIndex--;
    
    // Continue searching for a valid, living unit to make active.
    while (activeUnitIndex >= 0)
    {
        // Check if the unit at the current index is not alive (i.e., it's defeated).
        if (!units[activeUnitIndex].IsAlive())
        {
            // Move to the previous unit in the list.
            activeUnitIndex--;
        }
        else
        {
            // Activate the next living unit in the list and start its turn.
            units[activeUnitIndex].StartUnitTurn();
            break; // Exit the loop once an active unit is found.
        }
    }
}
```



With this simple logic you will be able to reset the turn to the previous alive unit in your party.

But there is still one bug in the above logic of undoing the Attack Action. Can you guess it? Read the Undo method again and think about an edge case.



![](https://tenor.com/view/kermit-kermit-the-frog-nervous-scared-peur-gif-5249824.gif)



**Swipe below to see the answer**

























Click here to find the answer- If you use attack command on a target unit, and that target unit dies. How are you going to restore the health of a dead unit. 
- To fix this bug, You will need to check inside whether the target unit is Dead or Alive, if it is alive you will simply restore its health.
- But if the target unit is dead, you will need to first revive it and then restore its health.



To fix this you can have a few extra checks in your code and implement the Undo command as follows:



```javascript
public override void Undo()
{
    if (willHitTarget)
    {
        if (!targetUnit.IsAlive())
            targetUnit.Revive();

        targetUnit.RestoreHealth(actorUnit.CurrentPower);
        actorUnit.Owner.ResetCurrentActiveUnit();
    }
}
```



Now you will also need to implement a **Revive()** functionality in your unit controller for this to work.



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_26_2023__13_36_22.jpg)



All you need to do to revive a unit is set it's state as alive and make sure that the Idle animation is playing instead of the Dead animation:

```javascript
public void Revive()
{
    SetAliveState(UnitAliveState.ALIVE);
    unitView.PlayAnimation(UnitAnimations.IDLE);
}
```



Take the same approach for implementing **Undo()** functionality in `**HealCommand.**` If the target is successfully hit by Heal Action then you will need to damage target unit by the same amount to reverse this Action:

```javascript
public override void Undo()
{
    if (willHitTarget)
    {
        targetUnit.TakeDamage(actorUnit.CurrentPower);
        actorUnit.Owner.ResetCurrentActiveUnit();
    }
}
```



Now go ahead and implement the **Undo()** functionality for all Unit Actions.



In the next section you will update your **Command Invoker** to use these newly implemented Undo() methods.
