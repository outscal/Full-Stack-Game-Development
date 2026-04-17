In this lesson, you'll spawn the player character in the game!

To spawn the character, you need to create an object of the `Player` class.



# Objects in C#


---



> **💡PRO TIP: Object of class** 
> An object in programming is a specific instance of a class. It's like using a blueprint (the class) to create a real-world item (the object). Each object is equipped with its own set of data based on the structure defined in the class but can have its own unique values.



**SAMPLE CODE to Create an Object** 

```csharp
Player player = new Player();
```

From the above example, let's fetch the syntax of creating a new object in C#.

**SAMPLE CODE for Syntax for Creating an Object of any Class**

```csharp
 ClassName objectName = new ClassName();
```



But what is this `**new**` keyword?



> **PRO TIP** 💡: `new` keyword in C#
> 
> - Allocates the required amount of memory for the object.
> - It calls the constructor of the class to initialize the object.
> - It returns a reference to the newly created object.



**NOTE: **`new` isn’t a C# specific keyword. C++ also has the `new` keyword. You will learn about them in the*** C++ Intermediate Module*** in detail.



But what if you create an object without using the `**new**` keyword?



## INITIALIZATION vs Declaration


---



**SAMPLE CODE** 

```csharp
Player player = new Player(); 	//Creation and Initialization
Player playerSecond; //Declaration
```



**Initialization:** 

The first line is initialization!

Once you use the `**new**` keyword while creating a variable, a new object is created in the memory. It occupies certain space in the memory.



**Declaration:** 

The second line is declaration!

Without using the `**new**` keyword, no memory is allocated. 
So, basically, only an empty variable with a `**null**` value is created.

There is no value in `playerSecond`. 

You can assign an already existing object to it for use `**new**` keyword to create a new object, for example:

**SAMPLE CODE** 

```csharp
Player player = new Player();
Player playerSecond;				

playerSecond = player;
```

OR

**SAMPLE CODE** 

```csharp
Player player = new Player();
Player playerSecond;				

playerSecond = new Player();
```



You now understand objects in C#.

Now, to spawn the player character, all you have to do is create `Player` class's object inside `Main()` 



> **TODO: **`**Main()**`  
> ✅ Create a variable `Player player` at the end of `Main()`



Click here to see the solution.

```csharp
static void Main() 
{
        //...some other code
    
		    Player player = new Player(); //Creating and Spawning the Player Character
}
```





Now, when you run the code, you can see that the player spawns!

It's time to challenge the Dough Master!⚔️

How do we do that?!🤔

Yes, you're right about creating an Enemy!💪
