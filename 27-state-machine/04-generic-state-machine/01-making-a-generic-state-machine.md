Both state machines you created earlier are very similar to each other and share a lot of repeating code. 

The basic functionality of state machine still remains the same irrespective of who the owner is, that is, to update the current state, set owners for each state & handle state transition logic.

According to the current logic implemented, for each enemy that we create we will have to rewrite this same logic each time we implement a state machine.



> Go ahead and check out the following branch before moving forward: [***Generic-State-Machine***](https://github.com/outscal/AGD_StateMachine/tree/Generic-State-Machine-Setup)***-Setup***





# Introducing Generic State Machines


---



We will need to fix this issue by converting `IStateMachine` into a more generalized super class. But in doing so we encounter another issue.



Our States and State Machine needs to know which kind of enemy do they belong to. So you will need to convert your `IStateMachine` interface into a Generic Super Class for State Machine.



Our goal in this section is to create a Generic Super Class which when inherited by a sub class, that sub class will start behaving like a State Machine. \

Only thing the sub class needs to do is to specify which states  can it's owner acquire.



Lets start with some basic generic class syntax:

```javascript
// Generic state machine for an enemy of type T.
public class GenericStateMachine<T> where T : EnemyController
{
    protected T Owner;

    // Constructor sets the owner.
    public GenericStateMachine(T Owner) => this.Owner = Owner;
}
```

Notice that the access modifiers of properties have been updated accordingly.



Now add the current state reference + the logic to update your state machine and change its current state to a given new state

```javascript
protected IState currentState;

public void Update() => currentState?.Update();

protected void ChangeState(IState newState)
{
    currentState?.OnStateExit();
    currentState = newState;
    currentState?.OnStateEnter();
}

public void ChangeState(States newState) => ChangeState(States[newState]);
```



Finally, Create a map of State Types & State implementations and write logic for setting owner of states.

```javascript
protected Dictionary<States, IState> States = new Dictionary<States, IState>();

protected void SetOwner()
{
    foreach (IState state in States.Values)
    {
        state.Owner = Owner;
    }
}
```



Now our Generic State Machine is Complete! Here is how it looks like:

```javascript
public class GenericStateMachine<T> where T : EnemyController
{
    protected T Owner;
    protected IState currentState;
    protected Dictionary<States, IState> States = new Dictionary<States, IState>();

    public GenericStateMachine(T Owner) => this.Owner = Owner;

    public void Update() => currentState?.Update();

    protected void ChangeState(IState newState)
    {
        currentState?.OnStateExit();
        currentState = newState;
        currentState?.OnStateEnter();
    }

    public void ChangeState(States newState) => ChangeState(States[newState]);

    protected void SetOwner()
    {
        foreach (IState state in States.Values)
        {
            state.Owner = Owner;
        }
    }
}
```



Now any enemy state machine can inherit from this superclass and define its states. No need to rewrite repeating code.

You have just created a powerful and reusable tool, simplifying state management in game development. 



In the next section, we'll refactor our existing State Machines to utilize this new Generic State Machine.
