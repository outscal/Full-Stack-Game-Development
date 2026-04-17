As discussed in the previous section,  **Command Invoker** is responsible for invoking and managing commands, which includes: 

- Maintaining a command registry.
- Registering each command before executing it. 
- Executing a command whenever required. (Either immediately or sometime later)



Inside your Command folder, create a script called `**CommandInvoker.cs**`

You will need to maintain the commands in a sequence so storing them in a **Stack **will be useful. Create a Stack of `**ICommands**`** **called commandRegistry in this class.

Next, Create a public method called `**ExecuteCommand()**` which takes `**ICommand**`** **as an argument and invokes it by calling its `Execute()` method. 

Similarly Create another method called `**RegisterCommand()**` which takes `**ICommand**` as an argument and stores it at the top of the stack.

```javascript
/// <summary>
/// A class responsible for invoking and managing commands.
/// </summary>
public class CommandInvoker
{
    // A stack to keep track of executed commands.
    private Stack<ICommand> commandRegistry = new Stack<ICommand>();

    /// <summary>
    /// Process a command, which involves both executing it and registering it.
    /// </summary>
    /// <param name="commandToProcess">The command to be processed.</param>
    public void ProcessCommand(ICommand commandToProcess)
    {
        ExecuteCommand(commandToProcess);
        RegisterCommand(commandToProcess);
    }

    /// <summary>
    /// Execute a command, invoking its associated action.
    /// </summary>
    /// <param name="commandToExecute">The command to be executed.</param>
    public void ExecuteCommand(ICommand commandToExecute) => commandToExecute.Execute();

    /// <summary>
    /// Register a command by adding it to the command registry stack.
    /// </summary>
    /// <param name="commandToRegister">The command to be registered.</param>
    public void RegisterCommand(ICommand commandToRegister) => commandRegistry.Push(commandToRegister);
}
```



** **Right now you have created Abstract Commands and a Command Invoker for invoking and managing commands. But right now they are not being used by any Units in the game. The Communication between Units and Actions is still the same as before. 



In the Next Chapter you will learn how to create **Concrete Commands **for specific actions and use the command invoker for executing those commands.
