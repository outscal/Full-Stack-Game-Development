So, to create the player character, you need a class!



> **💡PRO TIP: Class in Programming** 
> A class in programming can be thought of as a way to define a new type of data structure that contains both data and functions to operate on that data. It's like creating a custom toolkit for handling specific types of information and operations related to it.
> Class acts like a blueprint to create objects.



Classes on a fundamental programming level are the same in both C++ and C#!



# Creating the Player Class


---



> **TODO: **`**class Player**`
> ✅ Create an empty **Player** class



**Click here to see the **`Player`** class**

```csharp
class Player
{

}
```





Now, you need to add elements to the player class.


# Adding Elements to Player Class


---

A class in C# can have lots of elements. We'll cover the basic ones!



## **Fields**


---

Variables within a class that hold data. Usually, private and accessed via properties.

Let's create variables for the player character!

What will be the variables for the player character?🤔

As discussed earlier, the *Dough Master *will have limited health, attack, and healing abilities.

You need to create variables for these abilities. 



> **TODO:**
> **✅**Create `private int health` and set its value to **100**.
> ✅Create `private int maxHealth` and set its value to **100**.
> ✅Create `private int attackDamage` and set its value to **20**.
> ✅Create `private int healingCapacity` and set its value to **15**.



You might have noticed that all the variables are integers! What about the other data types?!

Don't worry. You'll learn about them at the end of this chapter.

Now, let's move to the next element of a class: **Methods**!



## **Methods**


---



> **💡PRO TIP: Methods**
> Methods are a fundamental concept of programming. Methods in C# are blocks of code that perform specific tasks. Methods help organize code, promote reusability, and make programs more manageable.



Here's how a method is written in C#:



![ ](/Full-Stack-Game-Development/images/cf06e37a9ac7fcae.png)



1. **Access Modifier**: Determines the visibility of the function (e.g., public, private).
2. **Return Type**: Specifies the data type the function returns (or void if it doesn't return anything).
3. **Name**: A unique identifier for the function.
4. **Parameters**: Input values that the function can work with (optional).
5. **Body**: The actual code that performs the task.



Now that you know how to write a method in C#, let's create a method to **Spawn** the player!

What do we mean by "**Spawning**" the Player Character?🤔

Well, spawning means bringing something into the game's world.

In the case of this game, spawning the player simply means creating the Player's object.



But you also need to inform the Player that Player Character has spawned!

You can do this by printing a message!



**PLAYER CHARACTER SPAWNING MESSAGE**:

```text
==================================================
           🍕 DOUGH MASTER: GUARDIAN OF THE GOLDEN CRUST 🍕   
==================================================

Dough Master: That scoundrel won't escape with my creation!
```



When should this message be displayed?

Well, of course, when the `Player` class's object is created.

So, basically, when the object of the `Player` class is created, this message can be displayed in the `constructor`.



However, writing so much code in the constructor is not the correct approach. Because the code can be better organised.

Since this is "**Spawning** **of the Player Character**", you can create a separate **function** for this!



> **TODO: **`**class Player**`  
> ✅ Create a method, `private void SpawnPlayer()` 
> ✅ Inside it, display the above message for spawning the player.



Click here to see the current `Player` class

```csharp
class Player
{
//variables
private int health = 100;
private int attackDamage = 20;
private int healingCapacity = 15;
private int maxHealth = 100;

//Function
private void SpawnPlayer()
{
Console.WriteLine("\\n==================================================");
Console.WriteLine(" 🍕 DOUGH MASTER: GUARDIAN OF THE GOLDEN CRUST 🍕 ");
Console.WriteLine("==================================================\\n");
Console.WriteLine("\\nDough Master: That scoundrel won't escape with my creation!\\n");
}
}
```







## **Constructors**


---

Special methods that are called when an object is instantiated. They are used to initialise an object's fields.

Now, you need to call the `SpawnPlayer()` method in the `Player` class's constructor so that the message is printed on the console whenever an object of the player class is created.



> **TODO: **

> ✅ Create `Player` class's `constructor` 
> ✅ Inside the `constructor`, call `SpawnPlayer()`



Click here to see the current `Player` class

```csharp
class Player
{
		//variables
		private int health = 100;
    private int attackDamage = 20;
    private int healingCapacity = 15;
    private int maxHealth = 100;
   
   //Default Constructor
	 public Player()
	 {
		 SpawnPlayer()
	 }
	 
	 //Function
	 private void SpawnPlayer()
	 {
		 Console.WriteLine("\\n==================================================");
     Console.WriteLine("   🍕 DOUGH MASTER: GUARDIAN OF THE GOLDEN CRUST 🍕   ");
     Console.WriteLine("==================================================\\n");
     Console.WriteLine("\\nDough Master: That scoundrel won't escape with my creation!\\n");
	 }
}
```





> **PROTIP💡: *****Parameterized and Copy Constructors***
> Both these types of are constructors are same as C++. You'll learn the Copy Constructor in ***C++ inetmediate*** module



Now, you know about these elements of a class: **Fields**, **Methods,** and **Constructors.**

These elements in C# classes are very similar to C++ classes.

Now, let's see what is different in C# classes as compared to the C++ classes!



Two things that are different from C++ Classes

1. **Properties**
2. **No Destructor**



Let's see what is going on...



## **Properties**


---

Properties are a mix of Fields and Methods.

Let's understand properties by turning the Player's health variable into a property!

But why do we need it as a property?🤔

Don't worry. You'll understand it in the ***Battle Mechanics*** chapter!

Now, let's understand how to create a property!



Properties have **Getters** ('`get'`) and **Setters** ('`set'`)

`**get**`**: **It returns the value of the private field. It's a method that helps you read the data.

```csharp
public int Health
{
				//GETTER
				get 
				{
					return health; 
				}
}
```



`**set**`**:** It is used to assign a new value to the private field. It can include validation or other logic to ensure the data being set is correct or to perform actions when the data changes.



```csharp
public int Health
{
				//GETTER

				//SETTER
        private set 
        {
            // If the value provided is negative, store zero instead
            if (value < 0)
                health = 0;
            // if the value exceeds maximum health
            else if(value > maxHealth)
            {
                health = maxHealth;
            }
						//set the provided value if both the conditions are false
            else
            {
                health = value;
            }
        }
}
```



**SAMPLE CODE for using Properties** 

```csharp
//Assume that the player is Player class's object
player.Health = 100; 														// Setting the player's health
int currentHealth = player.Health;		// Getting the health of the player(can be useful if any other class want to access the health)
```



Notice how there is Logic inside the setter!

Now, whenever you want to set the health value, you can use the property instead of repeatedly writing the same logic!

Here are some more advantages of properties.



**ADVANTAGES OF PROPERTIES**

1. Fields remain private
2. You can create logic for both getting and setting the values
3. You get the control to make getters and setters to be public or private



> **TODO: **

> ✅In `Player` class implement the `public int Health` property for the health variable.



Click here to see the solution.

```csharp
class Player
{
		//variables
		private int health = 100;
    private int attackDamage = 20;
    private int healingCapacity = 15;
    private int maxHealth = 100;
   
   public int Health
	{
				//GETTER
				get 
				{
					return health; 
				}
				//SETTER
        private set 
        {
            // If the value provided is negative, store zero instead
            if (value < 0)
                health = 0;
            // if the value exceeds maximum health
            else if(value > maxHealth)
            {
                health = maxHealth;
            }
						//set the provided value if both the conditions are false
            else
            {
                health = value;
            }
        }
	}
   
   //Default Constructor
	 public Player()
	 {
		 SpawnPlayer()
	 }
	 
	 //Function
	 private void SpawnPlayer()
	 {
		 Console.WriteLine("\\n==================================================");
     Console.WriteLine("   🍕 DOUGH MASTER: GUARDIAN OF THE GOLDEN CRUST 🍕   ");
     Console.WriteLine("==================================================\\n");
     Console.WriteLine("\\nDough Master: That scoundrel won't escape with my creation!\\n");
	 }
}
```





## Access Modifiers


---

***Access Modifiers*** are no different than C++

Well, the syntax is slightly different.

 

**SAMPLE CODE** 

```csharp
public class Player
{
	private int health = 100;
	public int Health 
	{ 
			//code 
	}
} 
```



`**private:**` Only code declared in the same `class` can access this member.

`**public:**` This can be accessed from any class or method in your code as long as it includes a reference to where `the parent` class is defined.



At the end of the chapter, we'll see how destructor in C# differs from C++!

Now that you have created the player character, it's time to spawn the *Dough Master* in the game world!💪
