State Machines are a powerful tool for controlling enemy behavior. 

In this section we'll explore how to make our State Machines more versatile and flexible and utilize this while adding more enemies and behaviors in our project.

To expand our state machine for `PatrolMan`, we'll begin by adding two new states: **Patrolling** and **Chasing**.



Do you remember that Enum you created earlier called `**OnePunchManStates**`**? **

Update that enum to make it *more ****generalized***. Rename it to **"States" **and add these 2 new States:

```javascript
public enum States
{
    IDLE,
    ROTATING,
    SHOOTING,
    PATROLLING,
    CHASING
}
```



Now you’re going to put the behavior of each state into a separate class. 

That way, you will be localizing the behavior and making things a lot easier to change and understand your code. 

Start with **Patrolling State**, which implements the `IState` interface:

```javascript
public class PatrollingState : IState
{
    public OnePunchManController Owner { get; set; }
    private OnePunchManStateMachine stateMachine;

    public PatrollingState(OnePunchManStateMachine stateMachine) => this.stateMachine = stateMachine;

    public void OnStateEnter() {  }

    public void Update() { }

    public void OnStateExit()  {  }
}
```



Before we begin implementing methods in the above class, can you look at it again and tell us what's wrong with it?

**Hint:**

![](/Full-Stack-Game-Development/images/7443e4195ebca829.jpg)



Click here to see what is wrong in the above scriptWe have a reference of `**OnePunchManController**`** **and `**OnePunchManStateMachine**`** **in our Patrolling State. 

Even our `**IState**`** **interface holds a reference of `**OnePunchManController**`. 

But our states should be more flexible, they should be applicable to multiple enemy types, not just `**OnePunchMan**`.

Also, What if another enemy in the future also needs to use this Patrol State in it's state machine?  

We want to implement States in such a way that a they can be used by Multiple types of enemies. 



To achieve that we need to revisit a foundational programming principle in object oriented way of programming:



> **Program to an interface, not an implementation.**



You will need to create an interface `IStateMachine` to represent each State Machine and each implementation of a State Machine will implement this interface.

Similarly, You will need to use the base class `EnemyController` in `IState` to hold the reference of an enemy. This will decouple it from any specific enemy types.

Please note that “**Program to an interface**” really means “**Program to a supertype.**”

So our State interface will look like this:

```javascript
public interface IState
{
    public EnemyController Owner { get; set; }
    public void OnStateEnter();
    public void Update();
    public void OnStateExit();
}
```

and our updated implementation of `PatrolState` will look like this:

```javascript
public class PatrollingState : IState
{
    public EnemyController Owner { get; set; }
    private IStateMachine stateMachine;

    public PatrollingState(IStateMachine stateMachine) => this.stateMachine = stateMachine;

    public void OnStateEnter() { }

    public void Update() { }

    public void OnStateExit() {  }
}
```



But we have not created an interface called `IStateMachine` yet. 

So lets quickly create a simple interface to generalize and represent any State Machine in our project.

```javascript
public interface IStateMachine
{
    public void ChangeState(States newState);
}
```



That's all for now, we may refactor this interface later to make it more *generic,* but for now this is sufficient for our requirement.



Now that we have a generic `IStateMachine` interface, we can update its references in other **state classes** and `**OnePunchManStateMachine**` accordingly. 

So go ahead and quickly refactor these classes in your project.



Once you are done refactoring the code for previous states, Let's continue implementing our new Patrolling State.

The behavior of this state is quite simple, our enemy will have a set of patrol points assigned to it on which it will iterate one by one. 

![](/Full-Stack-Game-Development/images/24c6f9fa7371302f.png)



We will keep track of the current waypoint index to determine the position where our enemy needs to go next. 

Once our Enemy enters the patrolling state it will get a destination that it needs to move towards:

```javascript
// Initialize the current patrolling index to -1 to start from the first waypoint.
private int currentPatrollingIndex = -1;

// Store the destination for the enemy's patrolling behavior.
private Vector3 destination;

public void OnStateEnter()
{
    SetNextWaypointIndex();
    destination = GetDestination();
}

private void SetNextWaypointIndex()
{
    // Check if the currentPatrollingIndex has reached the end of the waypoint list.
    if (currentPatrollingIndex == Owner.Data.PatrollingPoints.Count - 1)
        // If it has, reset it to 0 to start patrolling from the first waypoint.
        currentPatrollingIndex = 0;
    else
        // Otherwise, increment the index to move to the next waypoint.
        currentPatrollingIndex++;
}

// Helper method to get the destination position for the current waypoint.
private Vector3 GetDestination() => Owner.Data.PatrollingPoints[currentPatrollingIndex];
```



We will be using Unity's NavMesh for moving our enemy in the Level. 

> Note that this project is made in a 3D environment to utilize Unity's NavMesh for pathfinding. 
> You can use different assets for this game if you like and make changes to camera to easily convert this into a 3D Game



```javascript
public void OnStateEnter()
{
    SetNextWaypointIndex();
    destination = GetDestination();
    MoveTowardsDestination();
}

// This method is responsible for moving the character towards its destination.
private void MoveTowardsDestination()
{
    // Set the 'isStopped' property of the character's navigation agent to false.
    // This ensures that the agent is actively navigating towards the destination.
    Owner.Agent.isStopped = false;

    // Set the destination for the character's navigation agent.
    Owner.Agent.SetDestination(destination);
}
```



This will make your enemy to reach towards the destination position but there is one missing piece left. 

You need to update your enemy to **Idle State** when it reaches the destination. 

Lets modify the `Update()` method in `PatrollingState` to check for this condition

```javascript
public void Update()
{
    if(ReachedDestination())
        stateMachine.ChangeState(States.IDLE);
}

private bool ReachedDestination() => Owner.Agent.remainingDistance <= Owner.Agent.stoppingDistance;
```



So this how your complete `**PatrollingState**` class looks like:

```javascript
public class PatrollingState : IState
{
    public EnemyController Owner { get; set; }
    private IStateMachine stateMachine;
    private int currentPatrollingIndex = -1;
    private Vector3 destination;

    public PatrollingState(IStateMachine stateMachine) => this.stateMachine = stateMachine;

    public void OnStateEnter()
    {
        SetNextWaypointIndex();
        destination = GetDestination();
        MoveTowardsDestination();
    }

    public void Update()
    {
        if(ReachedDestination())
            stateMachine.ChangeState(States.IDLE);
    }

    public void OnStateExit() { }

    private void SetNextWaypointIndex()
    {
        if (currentPatrollingIndex == Owner.Data.PatrollingPoints.Count-1)
            currentPatrollingIndex = 0;
        else
            currentPatrollingIndex++;
    }

    private Vector3 GetDestination() => Owner.Data.PatrollingPoints[currentPatrollingIndex];

    private void MoveTowardsDestination()
    {
        Owner.Agent.isStopped = false;
        Owner.Agent.SetDestination(destination);
    }

    private bool ReachedDestination() => Owner.Agent.remainingDistance <= Owner.Agent.stoppingDistance;
}
```



**You have made your states more flexible!** 
They can now be used by multiple type of enemies and you can easily add a new state like **Patrolling State**. 

Go ahead and try implementing Chasing State for Patrol Man as well.
