Imagine playing a game and wishing you could relive that incredible moment when you pulled off a jaw-dropping move or solved a challenging puzzle. Game replays let players go back in time, allowing them to watch and analyze their gameplay.



When you score an awesome goal in FIFA and are able to watch the replay of that goal from different angles and relive the glory, When you watch replay of a game of Clash Royale to strategize and learn where you can improve your gameplay, how do you think this replay functionality is implemented?



![](/Full-Stack-Game-Development/images/cdf19dda1742a2f1.gif)



![](/Full-Stack-Game-Development/images/e15ba768bf523a04.gif)



The Command Pattern, with its ability to store and execute actions, can make this magic happen.



When you want to replay a game, you simply execute these stored commands in the exact same order. If the conditions that they are executed in are similar to previous time, it will replicate the exact gameplay experience. It's like watching a movie of your game session. Soon you yourself are going to direct such a movie. 



You've already got the building blocks, and now it's time to assemble them into another amazing game mechanic.


---



To implement this feature you will need to create a `**ReplayService**`. 

Why you need another service for implementing this feature?

According to the communication flow you implemented earlier, the **Input Service** creates commands and passes it for processing in the game service. But in the **Replay Mode** you wont need to select an input, you already have a list of commands that you want to execute. It contains relevant data like which unit should perform what kind of action on which target.



During replay mode, your Input Service will not be required to function. Instead the **Replay Service** will pass the next command to be processed by the **Game Service**. The responsibility of Replay Service will be to maintain its state and when it is in active state, it will store the list of all commands in a **replay stack** and pass commands one-by-one to the Game Service in the correct order to be processed. While in **Replay Mode**, the **Input Service** will be set as Inactive.

![](/Full-Stack-Game-Development/images/9f20ad4c79dad7fe.png)



So let's jump into it right away, Create a folder called **Replay** in the Scripts folder and create a new script called **Replay Service** in it.

![](/Full-Stack-Game-Development/images/efb592c94d201873.png)



Open this script and translate all the above logic into code:

```javascript
// A class responsible for managing and controlling the replay of recorded commands.
public class ReplayService
{
    // A stack to store recorded commands for replay.
    private Stack<ICommand> replayCommandStack;

    // Property to get or set the current replay state.
    public ReplayState ReplayState { get; private set; }

    // Constructor for the ReplayService. Initializes the replay state as "DEACTIVE."
    public ReplayService() => SetReplayState(ReplayState.DEACTIVE);

    /// Set the replay state to the specified state.
    public void SetReplayState(ReplayState stateToSet) => ReplayState = stateToSet;

    // Set the command stack for replay, providing a collection of commands to replay.
    public void SetCommandStack(Stack<ICommand> commandsToSet) => replayCommandStack = new Stack<ICommand>(commandsToSet);

    // Execute the next recorded command in the stack if there are commands left to replay.
    public void ExecuteNext()
    {
        if (replayCommandStack.Count > 0)
            GameService.Instance.ProcessUnitCommand(replayCommandStack.Pop());
    }
}
```



We have created a functionality to execute the next command but this method will be invoked at the correct time by another component. That correct time is when the previous command has been executed. 



Create an instance of this new Service in `**GameService.cs**`:

```javascript
public class GameService : GenericMonoSingleton<GameService>
{
	.....
	public ReplayService ReplayService { get; private set; }
	
	.....
	
	private void Start() 
	{
			....
			ReplayService = new ReplayService();
	}
}
```



In the next section you will be using this Replay Service in your game to replay the whole battle like a movie.
