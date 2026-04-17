Since you have now created a Generic State Machine you will no longer be needing an IStateMachine interface. 

So delete that script form your project.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_46_25.jpg)



Your project must be showing a lot of errors in Unity after you deleted your state machine interface. Don't worry, we will refactor all our states and state machines and resolve all these errors quickly.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__13_47_27.jpg)



- First, you need to refactor all the states you created earlier. You had references of `**IStateMachine**` earlier which we simply need to replace with `**GenericStateMachine<T>**`.
- You will also need to change the class declaration of states to specify what '`**T**`' is.

```javascript
public class ShootingState<T> : IState where T : EnemyController
{
    private GenericStateMachine<T> stateMachine;

    ...

    public ShootingState(GenericStateMachine<T> stateMachine) => this.stateMachine = stateMachine;
	
	    ...
}
```



Similarly you can refactor all the other states as well.

Now take a look at `**OnePunchManStateMachine**`. Since we are not using `**IStateMachine**` anymore, this class will inherit from `**GenericStateMachine<T>**` instead.

```javascript
public class OnePunchManStateMachine : GenericStateMachine<OnePunchManController>
{
    
}
```



Create a constructor for this class and add the states that this state machine is going to use.

```javascript
public class OnePunchManStateMachine : GenericStateMachine<OnePunchManController>
{
    public OnePunchManStateMachine(OnePunchManController Owner) : base(Owner)
    {
        this.Owner = Owner;
        CreateStates();
        SetOwner();
    }
    
    private void CreateStates()
    {
        States.Add(StateMachine.States.IDLE, new IdleState<OnePunchManController>(this));
        States.Add(StateMachine.States.ROTATING, new RotatingState<OnePunchManController>(this));
        States.Add(StateMachine.States.SHOOTING, new ShootingState<OnePunchManController>(this));
    }
}
```



**That's all we need to do when creating any state machine from now on! The generic state machine takes care of the rest of the logic.**



![](https://tenor.com/view/yes-thats-all-over-done-bye-gif-2359658865930065513.gif)
