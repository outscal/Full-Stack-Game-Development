For adding hitman in your game, you will simply create a `**TeleportingState**` and a `**HitmanController**`. 

You will now realize how easy it is to scale your project by adding new enemies and behavior if you follow good code architecture practices.

Are you ready? Lets start right away!



## 1) State Enhancements


---



The first thing you must do is to expand the state enum to embrace Hitman's latest trick – Teleporting.

```javascript
public enum States
{
    IDLE,
    ROTATING,
    SHOOTING,
    PATROLLING,
    CHASING,
    TELEPORTING
}
```



## 2) The Art of Teleportation


---



It's time to create a `**TeleportingState**` class where Hitman performs a vanishing act, reappearing randomly. It adds an intriguing twist, and transitions into the Chasing state.

```javascript
// Represents a teleporting state for an enemy of type T.
public class TeleportingState<T> : IState where T : EnemyController
{
    public EnemyController Owner { get; set; }
    private GenericStateMachine<T> stateMachine;

    public TeleportingState(GenericStateMachine<T> stateMachine) => this.stateMachine = stateMachine;

    public void OnStateEnter()
    {
        // Teleport the enemy to a random position.
        TeleportToRandomPosition();

        // Transition to the CHASING state after teleporting.
        stateMachine.ChangeState(States.CHASING);
    }

    public void Update() { }

    public void OnStateExit() { }
}
```



Now we must implement the `**TeleportToRandomPosition()**` method. We need to get a random position on our NavMesh to teleport our enemy at.

You can use the `**SamplePosition()**` method from NavMesh class of Unity:

```javascript
// Teleports the owner to a random NavMesh position within a specified radius.
private void TeleportToRandomPosition() => Owner.Agent.Warp(GetRandomNavMeshPoint());

// Generates a random NavMesh position within the teleporting radius.
private Vector3 GetRandomNavMeshPoint()
{
    // Calculate a random direction within the teleporting radius.
    Vector3 randomDirection = Random.insideUnitSphere * Owner.Data.TeleportingRadius + Owner.Position;
    NavMeshHit hit;
    
    // Try to find a valid NavMesh position within the radius, return spawn position if not found.
    if (NavMesh.SamplePosition(randomDirection, out hit, Owner.Data.TeleportingRadius, NavMesh.AllAreas))
        return hit.position;
    
    return Owner.Data.SpawnPosition;
}
```



## 3) Crafting Hitman's Arsenal


---



Hitman's state machine, a marvel of your code architecture, will be now created using the`GenericStateMachine`. All we need to do is, just define the states which it'll employ:

```javascript
public class HitmanStateMachine : GenericStateMachine<HitmanController>
{
    public HitmanStateMachine(HitmanController Owner) : base(Owner)
    {
        this.Owner = Owner;
        CreateStates();
        SetOwner();
    }

    private void CreateStates()
    {
        States.Add(StateMachine.States.IDLE, new IdleState<HitmanController>(this));
        States.Add(StateMachine.States.PATROLLING, new PatrollingState<HitmanController>(this));
        States.Add(StateMachine.States.CHASING, new ChasingState<HitmanController>(this));
        States.Add(StateMachine.States.SHOOTING, new ShootingState<HitmanController>(this));
        States.Add(StateMachine.States.TELEPORTING, new TeleportingState<HitmanController>(this));
    }
}
```

![](/Full-Stack-Game-Development/images/83fce5d9ceb7fd82.gif)



## 4) Hitman controller


---



The HitmanController takes center stage, orchestrating Hitman's moves. From state machine initialization to dynamic state transitions based on player actions.

```javascript
public class HitmanController : EnemyController
{
    private HitmanStateMachine stateMachine;

    public HitmanController(EnemyScriptableObject enemyScriptableObject) : base(enemyScriptableObject)
    {
        enemyView.SetController(this);
        CreateStateMachine();
        stateMachine.ChangeState(States.IDLE);
    }

    private void CreateStateMachine() => stateMachine = new HitmanStateMachine(this);

    public override void UpdateEnemy()
    {
        if (currentState == EnemyState.DEACTIVE)
            return;

        stateMachine.Update();
    }
}
```



You need to change the enemy state to Teleporting after hitman shoots. When the player enters its range it should chase the player and go to Idle state if player exits it's detectable range.

```javascript
public override void UpdateEnemy()
{
    if (currentState == EnemyState.DEACTIVE)
        return;

    stateMachine.Update();
}

// Initiates shooting and changes the state to TELEPORTING.
public override void Shoot()
{
    base.Shoot();
    stateMachine.ChangeState(States.TELEPORTING);
}

// Player enters range, change to CHASING state.
public override void PlayerEnteredRange(PlayerController targetToSet)
{
    base.PlayerEnteredRange(targetToSet);
    stateMachine.ChangeState(States.CHASING);
}

// Player exits range, change to IDLE state.
public override void PlayerExitedRange() => stateMachine.ChangeState(States.IDLE);
```



## 5) enlisting hitman in the ranks


---



You must enlist Hitman in our lineup of foes. To do that, go to EnemyService and update the enemy creation logic. Don't forget to summon the mysterious Hitman.  

```javascript
public class EnemyService
{
    ....
	
	    public EnemyController CreateEnemy(EnemyScriptableObject enemyScriptableObject)
    {
        EnemyController enemy;

        switch (enemyScriptableObject.Type)
        {
            case EnemyType.OnePunchMan:
                enemy = new OnePunchManController(enemyScriptableObject);
                break;
            case EnemyType.PatrolMan:
                enemy = new PatrolManController(enemyScriptableObject);
                break;
            case EnemyType.Hitman:
                enemy = new HitmanController(enemyScriptableObject);
                break;
            default:
                enemy = new EnemyController(enemyScriptableObject);
                break;
        }
    }

    ....

}
```



Hitman's teleporting antics add a thrilling dimension to our game. 

With your robust code architecture adding new states and enemies is a piece of cake



![](/Full-Stack-Game-Development/images/14d23f05ef04b74a.gif)
