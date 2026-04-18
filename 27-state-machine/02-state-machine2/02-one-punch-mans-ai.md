Lets assume that our enemy at any given point of time is either **Idle** or **Rotating**. To implement this behavior, we will create two booleans inside the `OnePunchManController` class.



```javascript
private bool isIdle;
private bool isRotating;

private float idleTimer;
private float targetRotation;
private PlayerController target;

// Constructor for OnePunchManController, initializes variables and sets the view.
public OnePunchManController(EnemyScriptableObject enemyScriptableObject) : base(enemyScriptableObject)
{
    enemyView.SetController(this);
    InitializeVariables();
}

// Private method to initialize variables to their default values.
private void InitializeVariables()
{
    // Set the enemy to be in an idle state initially.
    isIdle = true;

    // Set rotating state to false initially.
    isRotating = false;

    // Initialize the idle timer with the value from the scriptable object.
    idleTimer = enemyScriptableObject.IdleTime;
}
```



We have 2 booleans here, `**isIdle**` and `**isRotating**`, indicating the enemy behavior at any particular time. Initially we are setting the enemy to be in Idle State and setting `isRotating` to false. Inside the update method, we will first check which boolean is true and accordingly apply some logic.



```javascript
// Override of the base class method for updating the enemy's behavior.
public override void UpdateEnemy()
{
    // Check if the enemy is in a deactivated state, and if so, return without further processing.
    if (!isActive)
        return;

    // If the enemy is in an idle state, decrement the idle timer.
    if(isIdle)
    {
        idleTimer -= Time.deltaTime;

        // Check if the idle timer has elapsed, indicating the end of the idle state.
        if(idleTimer <= 0)
        {
            isIdle = false;
            isRotating = true;

            // Calculate the target rotation to face the opposite direction (180 degrees).
            targetRotation = (Rotation.eulerAngles.y + 180) % 360;
        }
    }

    // If the enemy is rotating, set its rotation and check if the rotation is complete.
    if(isRotating)
    {
        SetRotation(CalculateRotation());

        // Check if the rotation is complete.
        if(IsRotationComplete())
        {
            isIdle = true;
            isRotating = false;
            ResetTimer();
        }
    }
}
```



The code may look a bit unclean right now but it does what needs to be done, right?

Well then, lets add the third behavior of One Punch Man, **Shooting**. We will refactor the above script by adding another boolean indicating the shooting state.



```javascript
private bool isIdle;
private bool isRotating;
// Adding another boolean to indicate if player is shooting
private bool isShooting;

private float idleTimer;
private float targetRotation;
private PlayerController target;

...
...

private void InitializeVariables()
{
    isIdle = true;
    isRotating = false;
    
    // Set Shooting state to false initially.
    isShooting = false;

    idleTimer = enemyScriptableObject.IdleTime;
}
```



Now lets use this new boolean inside the `update()` method of our enemy script to implement the actual shooting behavior. 



```javascript
public override void UpdateEnemy()
{
    if (!isActive)
        return;

    if(isIdle)
    {
        idleTimer -= Time.deltaTime;
        if(idleTimer <= 0)
        {
            isIdle = false;
            isRotating = true;
            targetRotation = (Rotation.eulerAngles.y + 180) % 360;
        }
    }

    if(isRotating)
    {
        SetRotation(CalculateRotation());
        if(IsRotationComplete())
        {
            isIdle = true;
            isRotating = false;
            ResetTimer();
        }
    }
		
		if(isShooting) 
    {
        // Calculate the desired rotation to face the player.
				Quaternion desiredRotation = CalculateRotationTowardsPlayer();
    
				// Set the enemy's rotation towards the player.
				SetRotation(RotateTowards(desiredRotation));
    
				// Check if the enemy is facing the player.
				if (IsFacingPlayer(desiredRotation))
				{
	    			// Decrement the shoot timer.
	    			shootTimer -= Time.deltaTime;
        		
	    			// Check if it's time to shoot based on the rate of fire.
	    			if (shootTimer <= 0)
	    			{
								// Reset the shoot timer and initiate the shooting behavior.
								shootTimer = enemyScriptableObject.RateOfFire;
								Shoot();
	    			}
				}
    }
}
```



![undefined](//outscal.github.io/Full-Stack-Game-Development/images/692cdf2a20610e80.gif)



Its getting more and more difficult to read doesn’t it? Well lets hold on for a little longer. 

The enemy should go into shooting state when the player enters its range of detection and go back to rotating state when player gets out of enemy’s detection zone:



```javascript
public override void PlayerEnteredRange(PlayerController targetToSet)
{
    base.PlayerEnteredRange(targetToSet);
    isShooting = true;
    target = targetToSet;
    shootTimer = 0;
}

public override void PlayerExitedRange() 
{
    isShooting = false;
}
```



Now inside this spaghetti code, lies a **bug**, can you notice it? take 2 minutes and try to figure out what's wrong.



> Hint: Booleans

![](//outscal.github.io/Full-Stack-Game-Development/images/932f70ecc58d1473.png)













If you haven’t noticed yet, there will be a situation where multiple booleans of your enemy will be active at a given time, for example, `isShooting` and `isIdle` can be both true at a given time which is going to cause some weird behavior in your game. To rectify this, we will need to check and set all the enemy state booleans each time we transition to a new state, and refactor our code to look something like this:



```javascript
public override void UpdateEnemy()
{
    if (!isActive)
        return;

    if(isIdle && !isRotating && !isShooting)
    {
        idleTimer -= Time.deltaTime;
        if(idleTimer <= 0)
        {
            isIdle = false;
            isRotating = true;
            targetRotation = (Rotation.eulerAngles.y + 180) % 360;
        }
    }

    if(!isIdle && isRotating && !isShooting)
    {
        SetRotation(CalculateRotation());
        if(IsRotationComplete())
        {
            isIdle = true;
            isRotating = false;
            ResetTimer();
        }
    }

    if(!isIdle && !isRotating && isShooting)
    {
        Quaternion desiredRotation = CalculateRotationTowardsPlayer();
        SetRotation(RotateTowards(desiredRotation));
        
        if(IsFacingPlayer(desiredRotation))
        {
            shootTimer -= Time.deltaTime;
            if (shootTimer <= 0)
            {
                shootTimer = enemyScriptableObject.RateOfFire;
                Shoot();
            }
        }
    }
}

public override void PlayerEnteredRange(PlayerController targetToSet)
{
    base.PlayerEnteredRange(targetToSet);
    isIdle = false;
    isRotating = false;
    isShooting = true;
    target = targetToSet;
    shootTimer = 0;
}

public override void PlayerExitedRange() 
{
    isIdle = true;
    isRotating = false;
    isShooting = false;
}
```



**Something is clearly wrong with our approach!** 

The code we have now is not very readable, manageable and its even more harder to build something upon it.

Consider if you get new requirements of implementing 3 more unique behaviors for this enemy, at this rate, it will collapse into a heap of bugs before we’re done with it.

![](//outscal.github.io/Full-Stack-Game-Development/images/5d14227e8e7d4dfe.png)





One of the biggest drawback of using booleans is it **reduces readability**, it gets harder and harder to understand what's going in the code as more behavior for enemies keep getting added. 

If you are working in a team, it will be even more difficult to make any kind of progress with this approach.



![undefined](//outscal.github.io/Full-Stack-Game-Development/images/894ee4648b214931.png)



In the next section. we will learn a design pattern called **State Pattern **using which we will make our code architecture a lot better.

we will learn about **State Machine** and how it can be easily used to handle state management of an entity in our game.
