## Finalizers (Destructor) in C#


---

In C#, Destructors are called ***Finalizers***.

***Finalizers*** are directly called by C#'s Garbage Collector, and therefore, you have no control on when they'll be called.

They are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.



> 💡**PRO TIP: Garbage Collection in C#**
> Garbage collection in C# automatically manages memory by deallocating objects that are no longer needed, preventing memory leaks. The garbage collector automatically detects when objects in memory are no longer being used by the application and deallocates their memory, making it available for other objects.


Although C# automatically handles garbage collections, Finalizers can be used to clean up unmanaged resources like Windows, files, network connections, etc.



**SAMPLE CODE for Finalizer**

```csharp
public class Player
{
    //...some code

    // Finalizer
    ~Player()
    {
        // Cleanup code here
        Console.WriteLine("Player finalizer called, cleaning up resources.");
    }
}
```



In the next chapter, you'll understand why we need a separate `Game` class.
