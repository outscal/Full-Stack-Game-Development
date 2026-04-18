As you already know that an **Abstract Command** is a template for any command which can be used to encapsulate some method calls. It usually includes an `**Execute**` method.



Its time to create our own Abstract Command Interface.

Create a Folder and namespace inside your script folder called "Commands". Inside that Folder create another Folder called Abstract Commands:

![](/Full-Stack-Game-Development/images/18e993d9ade6c8e1.png)



Create an interface named `**ICommand**`** **this will be your most abstract command with just an **Execute() **method declared in it:

```javascript
public interface ICommand
{
    // This method defines the contract for executing a command.
    void Execute();
}
```



You can have commands of various types as well in a game. For example, you can have commands which represent Unit Actions and you can also have commands which represent Player Input and likewise. 

So you can create separate abstract commands for different types of commands. Create another abstract class Called `**UnitCommand**` inheriting form `**ICommand**`

```javascript
/// <summary>
/// An abstract class representing a unit-related command.
/// </summary>
public abstract class UnitCommand : ICommand
{
    // Fields to store information related to the command.
    public int ActorUnitID;
    public int TargetUnitID;
    public int ActorPlayerID;
    public int TargetPlayerID;

    // References to the actor and target units, accessible by subclasses.
    protected UnitController actorUnit;
    protected UnitController targetUnit;

    /// <summary>
    /// Abstract method to execute the unit command. Must be implemented by concrete subclasses.
    /// </summary>
    public abstract void Execute();

    /// <summary>
    /// Abstract method to determine whether the command will successfully hit its target.
    /// Must be implemented by concrete subclasses.
    /// </summary>
    public abstract bool WillHitTarget();
}
```



Here we are storing the Unit and Player IDs in the Unit Command's instance so that in case we need execute this command again in the future, we know which units were involved.



Now what you have is basically an empty Order Book according to our restaurant analogy. What you still need is a Command Invoker.

In the next section you will see how you can create a Command Invoker and with command registry for storing already executed commands.
