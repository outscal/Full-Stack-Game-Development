You have created all concrete states required for Patrol Man and refactored the code of State Machine to make it more flexible. 

Now use this more flexible and modular architecture to create a State Machine for Patrol Man. 



# Patrol Man's state machine


---

## 1) State Initialization



`PatrolManStateMachine` will be implementing the `IStateMachine` interface. This is very similar to how we created State Machine for One Punch Man.

We will first initialize all the states required for Patrol Man and set their owner, just like we did before for One Punch Man's state machine.

```javascript
public class PatrolManStateMachine : IStateMachine
{
    private PatrolManController Owner;
    private IState currentState;
    protected Dictionary<States, IState> States = new Dictionary<States, IState>();

    public PatrolManStateMachine(PatrolManController Owner)
    {
        this.Owner = Owner;
        CreateStates();
        SetOwner();
    }

    private void CreateStates()
    {
        States.Add(StateMachine.States.IDLE, new IdleState(this));
        States.Add(StateMachine.States.PATROLLING, new PatrollingState(this));
        States.Add(StateMachine.States.CHASING, new ChasingState(this));
        States.Add(StateMachine.States.SHOOTING, new ShootingState(this));
    }

    private void SetOwner()
    {
        foreach (IState state in States.Values)
        {
            state.Owner = Owner;
        }
    }
}
```

Add the state transition logic as well in the above state machine.




---

## 2) Creating **PatrolMan Controller**

The Owner for the above state machine (`PatrolManController`) needs to be implemented so lets get it done. 

`PatrolManController` will inherit from EnemyController and create a State Machine in its constructor.

```javascript
// Controller for a patrolling enemy character.
public class PatrolManController : EnemyController
{
    private PatrolManStateMachine stateMachine;

    // Constructor initializes the controller and sets the initial state to IDLE.
    public PatrolManController(EnemyScriptableObject enemyScriptableObject) : base(enemyScriptableObject)
    {
        enemyView.SetController(this);
        CreateStateMachine();
        stateMachine.ChangeState(States.IDLE);
    }
}
```



Now lets define the method for creating a State Machine for Patrol Man and update this state machine as well if the enemy is active.

```javascript
// Creates a PatrolManStateMachine.
private void CreateStateMachine() => stateMachine = new PatrolManStateMachine(this);

// Override to update the enemy's state machine.
public override void UpdateEnemy()
{
    if (currentState == EnemyState.DEACTIVE)
        return;

    stateMachine.Update();
}
```



Finally, lets add logic for when player enters or exits from the enemy range.

```javascript
// Called when a player enters this enemy's detection range.
public override void PlayerEnteredRange(PlayerController targetToSet)
{
    base.PlayerEnteredRange(targetToSet);
    stateMachine.ChangeState(States.CHASING);
}

// Called when a player exits this enemy's detection range.
public override void PlayerExitedRange() => stateMachine.ChangeState(States.IDLE);
```



# Level Setup


---



Now that we have created our new Enemy lets set him up in a new Level in Unity.



1. In Projects Tab, go to the following path -> `*Assets/Resources/Levels*` You will find a bunch of Level Scriptable Objects already set up for you. You can use these or create your own Level Designs with your own kind of enemies very easily.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_11_56.png)



1. Right-Click in Project tab and select `*Create/ScriptableObjects/LevelScriptableObject*`

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_12_51.png)



1. You can configure the level according to your preference or use the preconfigured scriptable objects. 

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_13_26.png)



1. Just like Level Scriptable Object, you can create an Enemy Scriptable Object as well. Some preconfigured examples are already there in the project.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_14_05.png)



1. Click on the GameService GameObject in the Hierarchy of your Unity Editor

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_14_42.png)



1. Drag and Drop your Level 2 Scriptable Object under the List of Level Scriptable Objects in GameService

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_15_16.png)
