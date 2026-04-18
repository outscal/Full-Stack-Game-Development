> Before we begin this Chapter, please checkout the following branch: [***State-Machine-Setup***](https://github.com/outscal/AGD_StateMachine/tree/State-Machine-Setup)



Once you have cloned this repository and checked out the branch above, open this project in Unity and press the play button to check out how the game currently looks like.




<iframe src="https://www.loom.com/embed/f8dcb416b50e43fd82eb2e9afca58898" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





Once you hit the play button you will see a level selection screen with only Level 1 on it. You will be creating many more levels as you progress through the course but right now click the Level 1 Button to check out what happens.



The level will be loaded with your player somewhere at the bottom of the game window with some enemies scattered on the screen.

The objective of the game is simple, eliminate all enemies and try to stay alive.

You can use WASD keys to move your player and use SPACE key to slash the throats of your enemies.



Now take some time and study how these enemies are behaving. 

It looks like they can **rotate** from time to time and stay **idle** for a few seconds. For now it sounds simple, right? 

But once the player is inside their range, they are able to detect the player and **shoot** at it. 



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/11_06_2023__10_10_04.png)



If your player gets close enough to any of these enemies, that enemy will turn **RED, **indicating that you kill that enemy.



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/11_06_2023__10_10_37.png)



Now that you understand the behavior of these enemies lets try to figure out how we can translate this behavior in code.

First we will see how enemies are getting spawned, so lets open and take a closer look at `EnemyService.cs` 

Once we select a Level from the Level selection menu, the `SpawnEnemies()` method in `EnemyService` is called.



> **Please Note: **This Project uses Design Patterns like **Service Locator** and **MVC**. If you are not familiar with these concepts we recommend you to check out related courses here ***(link to other courses)***



```javascript
// This is the constructor for the EnemyService class.
public EnemyService()
{
    // Initialize the variables required for this service.
    InitializeVariables();
    
    // Subscribe to events when the level is selected.
    SubscribeToEvents();
}

// This method initializes the activeEnemies list.
private void InitializeVariables() => activeEnemies = new List<EnemyController>();

// This method subscribes to the event triggered when a level is selected.
private void SubscribeToEvents() => GameService.Instance.EventService.OnLevelSelected.AddListener(SpawnEnemies);
```



Inside `SpawnEnemies()` method, we fetch the enemy data for the selected level and create **enemy controllers** using that data. 

Each object of `EnemyController` represents an enemy in the game. New `EnemyControllers` being created are added to `activeEnemies` List.



```javascript
// This method is responsible for spawning enemies when a level is selected.
public void SpawnEnemies(int levelId)
{
    // Get the list of enemy data for the selected level.
    List<EnemyScriptableObject> enemyDataForLevel = LevelService.GetEnemyDataForLevel(levelId);
    
    // Iterate through each enemy data for this level.
    foreach(EnemyScriptableObject enemySO in enemyDataForLevel)
    {
        // Create an EnemyController using the enemy data and add it to the activeEnemies list.
        EnemyController enemy = CreateEnemy(enemySO);
        activeEnemies.Add(enemy);
    }

    // Update the count of active enemies.
    SetEnemyCount();

    // Unsubscribe from the event to prevent multiple spawns for the same level.
    UnsubscribeToEvents();
}
```



You must have noticed, we have an `EnemyController` in the above script, which is a generic class for all enemies. The type of enemy which we have in level 1 is called “***One Punch Man***”. In *line number 12* in the above code snippet we are calling a function to create an enemy, but which type of enemy is being created here exactly?

Lets see what is happening inside `CreateEnemy()` method:



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__08_23_44.png)



```javascript
// This method creates an instance of an enemy based on the provided EnemyScriptableObject.
public EnemyController CreateEnemy(EnemyScriptableObject enemyScriptableObject)
{
    EnemyController enemy;

    // Determine the type of enemy based on the EnemyScriptableObject.
    switch (enemyScriptableObject.Type)
    {
        // If it's of type OnePunchMan, create a OnePunchManController instance.
        case EnemyType.OnePunchMan:
            enemy = new OnePunchManController(enemyScriptableObject);
            break;
        // For other types, create a generic EnemyController instance.
        default:
            enemy = new EnemyController(enemyScriptableObject);
            break;
    }

    // Return the created enemy instance.
    return enemy;
}
```



Now that you have seen the spawning logic for enemies, In the next section we will try to figure out how the observed behavior of `OnePunchManController` can be implemented in our code.
