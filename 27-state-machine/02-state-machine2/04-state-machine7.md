As discussed in the previous section, the problem with One Punch Man's code is that with each new behavior to be added, the update method keeps getting more and more twisted and tangled with all these booleans being used.



We can fix this by using **State Pattern** but what exactly is State Pattern?



The basic idea behind State Pattern is to separate each "**Behavior**" of an entity into different '"**States**". 

For example, our Enemy, One Punch Man has 3 different behaviors which are:

- Idle
- Rotating
- Shooting

![](/Full-Stack-Game-Development/images/0617cd570aa9c3ca.png)



Currently, the logic for each behavior is written inside the `Update()` method of `OnePunchManController`.

According to State Pattern, all these 3 behaviors should be separated into 3 different classes and should be independent of each other.

These different classes are called "**States**" and they will contain logic for their respective behavior.



Whenever the state of an enemy changes during the game, its behavior will also change.

But `OnePunchManController` itself will not contain logic for any behavior, it will just keep track of the current state and communicate with its **state machine** to use one of the states.



## Here's how we are going to do it:

- First, we’re going to define a state interface (`**IState**`) which will be used to represent all enemy state in our game.

- Then we’re going to implement a State class for every state of the enemy. These classes will be responsible for the behavior of the enemy when it is in the corresponding state.

- Finally, we’re going to get rid of all of our conditional code and instead delegate to the state class to do the work for us.



So lets fix up our `OnePunchManController` by making 3 state classes for it. But first we will need to make an `IState` interface which these classes will implement.

```javascript
// Define an interface for enemy states.
public interface IState
{
    // Reference to the owner (e.g., the enemy character) that holds this state.
    public OnePunchManController Owner { get; set; }

    // Called when the owner enters this state.
    public void OnStateEnter();

    // Called during each game update cycle to update the state's behavior.
    public void Update();

    // Called when the owner exits this state.
    public void OnStateExit();
}
```

That's basically what a state is all about, we just need to define what happens when:

- An enemy enters a state
- An enemy is currently in a state
- An enemy Exits the current state.



The next step is to create concrete states for our enemy by implementing this interface. Here is an example below for Idle State:

```javascript
// Define a state where the character is idle.
public class IdleState : IState
{
    public OnePunchManController Owner { get; set; }

    public void OnStateEnter() { }

    public void Update() { }

    public void OnStateExit() { }
}
```



Just like that, go ahead and create `**RotatingState.cs**` and `**ShootingState.cs**`  as well



Before we start implementing the methods in these state classes, we need to figure out when and how will our enemy transition from one state to another. Lets take a look at the updated diagram form before:

![](/Full-Stack-Game-Development/images/5a8ab5d76a07a9fa.png)



These arrows which have been added in the above diagram are called state transitions. They define the conditions under which our enemy will switch its internal state. The whole diagram itself is called a **Finite State Machine**.



Looks a bit similar doesn't it? 

That's right, this is exactly the kind of diagram you saw earlier for our old friend Mario. 

Here is a reminder below:

![](/Full-Stack-Game-Development/images/5cb5f4668bfd0686.png)



> State Machines are responsible for managing and controlling the transitions between different states of an object.



So now that we have the bigger picture, lets convert the state diagram above into actual code. 

We will first define an enum for various Enemy States that One Punch Man can have:



```javascript
public enum OnePunchManStates
{
    IDLE,
    ROTATING,
    SHOOTING
}
```



Now lets create our **State Machine!**

![](/Full-Stack-Game-Development/images/a6dcb2e2ba2b34a8.gif)



Inside our `**OnePunchManStateMachine**`, we will create an instance of each state class and map it with an enum value from above. 

We will also need to know who is the owner of this state machine and pass the owner reference down to each individual state object as well. 

![](/Full-Stack-Game-Development/images/7c6b3a39ab7815d9.png)



```javascript
public class OnePunchManStateMachine
{
    // Reference to the owner of the state machine
    private OnePunchManController Owner;
    
    // Dictionary to store available states, mapped to enum values
    protected Dictionary<OnePunchManStates, IState> States = new Dictionary<OnePunchManStates, IState>();

    public OnePunchManStateMachine(OnePunchManController Owner)
    {
        this.Owner = Owner;
        CreateStates();
        SetOwner();
    }

    // Create and initialize the states
    private void CreateStates()
    {
        States.Add(OnePunchManStates.IDLE, new IdleState(this));
        States.Add(OnePunchManStates.ROTATING, new RotatingState(this));
        States.Add(OnePunchManStates.SHOOTING, new ShootingState(this));
    }
    
    // Set the owner for each state
    private void SetOwner()
    {
        foreach (IState state in States.Values)
        {
            state.Owner = Owner;
        }
    }
}
```



You will need to make a reference for the **current state** of enemy inside our state machine. 

You will also need to **update enemy's current state** so the corresponding behavior can be executed. 

To do that, you will can add the following lines of code in your State Machine:

```javascript
// Reference to the current state
private IState currentState;

// Update the current state (if it exists)
public void Update() => currentState?.Update();
```



Now you almost have your State Machine completed, the only thing to add is transitioning logic in it. 

For this, create a method called `ChangeState()`. 

Whenever this method will be called, your enemy will transition into a new state:

```javascript
// Change the current state to a new state
protected void ChangeState(IState newState)
{
    currentState?.OnStateExit(); // Exit the current state (if it exists)
    currentState = newState; // Set the new state
    currentState?.OnStateEnter(); // Enter the new state
}

// Change the current state to a new state by providing a state enum
public void ChangeState(OnePunchManStates newState) => ChangeState(States[newState]);
```



**Congratulations!** You have now created your very first State Machine! This is how it looks like now:



```javascript
public class OnePunchManStateMachine
{
    private OnePunchManController Owner;
    private IState currentState;
    protected Dictionary<OnePunchManStates, IState> States = new Dictionary<OnePunchManStates, IState>();

    public OnePunchManStateMachine(OnePunchManController Owner)
    {
        this.Owner = Owner;
        CreateStates();
        SetOwner();
    }

    private void CreateStates()
    {
        States.Add(OnePunchManStates.IDLE, new IdleState(this));
        States.Add(OnePunchManStates.ROTATING, new RotatingState(this));
        States.Add(OnePunchManStates.SHOOTING, new ShootingState(this));
    }

    private void SetOwner()
    {
        foreach (IState state in States.Values)
        {
            state.Owner = Owner;
        }
    }
    
    public void Update() => currentState?.Update();
    
    protected void ChangeState(IState newState)
    {
        currentState?.OnStateExit();
        currentState = newState;
        currentState?.OnStateEnter();
    }

    public void ChangeState(OnePunchManStates newState) => ChangeState(States[newState]);
}
```



> **Please Note:** We strongly recommend you to create your own state machine from scratch instead of copying and pasting the code given here.



Now lets implement those concrete states and soon enough you will have a working State Machine in your project!



In Idle state our enemy is supposed to wait for a certain amount of time and then transition to rotating state once that timer is over. 

So lets implement this behavior in `IdleState` class:

```javascript
// Define a state where the character is idle.
public class IdleState : IState
{
    public OnePunchManController Owner { get; set; }
    private OnePunchManStateMachine stateMachine;
    private float timer;

    public IdleState(OnePunchManStateMachine stateMachine) => this.stateMachine = stateMachine;

    public void OnStateEnter() => ResetTimer();

    public void Update()
    {
        timer -= Time.deltaTime;
        if (timer <= 0)
            stateMachine.ChangeState(OnePunchManStates.ROTATING);
    }

    public void OnStateExit() => timer = 0;

    private void ResetTimer() => timer = Owner.Data.IdleTime;
}
```



Quite similarly, we will implement Rotating State as well in which our player is going to rotate until the target rotation is reached and once it has, we will transition back to Idle State: 

```javascript
// Define a state where the character is rotating.
public class RotatingState : IState
{
    public OnePunchManController Owner { get; set; }
    private OnePunchManStateMachine stateMachine;
    private float targetRotation;

    public RotatingState(OnePunchManStateMachine stateMachine) => this.stateMachine = stateMachine;

    public void OnStateEnter() => targetRotation = (Owner.Rotation.eulerAngles.y + 180) % 360;

    public void Update()
    {
        // Calculate and set the character's rotation based on the target rotation.
        Owner.SetRotation(CalculateRotation());
        if (IsRotationComplete())
            stateMachine.ChangeState(OnePunchManStates.IDLE);
    }

    public void OnStateExit() => targetRotation = 0;

    private Vector3 CalculateRotation() => Vector3.up * Mathf.MoveTowardsAngle(Owner.Rotation.eulerAngles.y, targetRotation, Owner.Data.RotationSpeed * Time.deltaTime);

    private bool IsRotationComplete() => Mathf.Abs(Mathf.Abs(Owner.Rotation.eulerAngles.y) - Mathf.Abs(targetRotation)) < Owner.Data.RotationThreshold;
}
```



While implementing these 2 states you must have noticed how easy it is to add more states in this architecture, since all the classes are different for each state, the code is decoupled and more modular. 



Now go ahead and implement the third and final State which is **Shooting State **by yourself.


---



Do you remember that horrific Update method inside OnePunchManController?



Once you have implemented logic for the Shooting State, Lets revisit our `OnePunchManController` and refactor that spaghetti bowl code you had earlier. 

First of all, lets get rid of all those booleans. 

Also you will need to create a State Machine inside the constructor of `OnePunchManController` and set its initial state as idle.

```javascript
 public class OnePunchManController : EnemyController
 {
     private OnePunchManStateMachine stateMachine;
     
         public OnePunchManController(EnemyScriptableObject enemyScriptableObject) : base(enemyScriptableObject)
             {
                     enemyView.SetController(this);
                     CreateStateMachine();
                     stateMachine.ChangeState(OnePunchManStates.IDLE);
             }
                                         
             private void CreateStateMachine() => stateMachine = new OnePunchManStateMachine(this);
}
```



**Clean and simple! **



Now that our enemy has a state machine of its own, you will also need to update it. 

```javascript
 public override void UpdateEnemy()
{
    if (currentState == EnemyState.DEACTIVE)
        return;

    stateMachine.Update();
}

public override void PlayerEnteredRange(PlayerController targetToSet)
{
    base.PlayerEnteredRange(targetToSet);
    stateMachine.ChangeState(OnePunchManStates.SHOOTING);
}

public override void PlayerExitedRange() => stateMachine.ChangeState(OnePunchManStates.IDLE);
```



**And that's all !!! **



All that spaghetti code has now been reduced to clean and simple 10 lines of code. even a 10 year old could read and understand this class now.



![](/Full-Stack-Game-Development/images/5c92c569b972992b.gif)
