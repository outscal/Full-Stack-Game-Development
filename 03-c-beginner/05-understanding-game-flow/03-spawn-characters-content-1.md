In this lesson, you'll spawn the *Dough Master* and the *Crust Bandit* in the game.

Wait? Didn't you do that already?!🤨

Yes, you're right! But was that the right place to spawn characters?🤔

Not really, let's see why so.



# Spawn Characters


---

After the game's story is displayed, the *Dough Master* and Crust Bandit will spawn.



Okay, but where do you create the objects of player and enemy?

Think 🤔

*Hint: *Spawning the characters is a part of the game's flow.



Click here to see the Hint.Did you think?😏Okay, here's the Hint!The objects of the characters should be created in the `Game` class!



**Note: **Creation of the objects of the `Player` and `Enemy` class can be done in a single function, i.e., `public void SpawnCharaters()`

**Note: **`SpawnCharacters()` is a `public` function, as you'll need to call it in the `Main()` function. This is a bad approach, and we'll fix it in the Final Chapter!



> **TODO: class **`**Program**` 
> ✅Clear the objects of `Player` and `Enemy` classes.
> 
> In the `Game` class:
> ✅Create `public void SpawnCharacters()`
> ✅In `SpawnCharacters()` create objects of the `Player` and `Enemy` class.
> ✅In the `Main()` function call the `SpawnCharacters()` function after `DisplayGameStory()`.



**Expected Output**

![ ](//outscal.github.io/Full-Stack-Game-Development/images/cb8ea87eb39bf420.png)



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
class Game { 
	Player player; 
	Enemy enemy; 
	public void SpawnCharacters() 
	{ 
	//Initialize Player and Enemy object 
	player = new Player(); 
	enemy = new Enemy(); 
	}
public void DisplayGameStory()
	{
				Console.Clear();
        Console.WriteLine("\n==================================================");
        Console.WriteLine("            🍕 MIDNIGHT PIZZA FIGHT 🍕           ");
        Console.WriteLine("==================================================");
        Console.WriteLine("\nIn a bustling pizzeria on a busy Friday night...");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("You, the Dough Master, created your magnum opus -");
        Console.WriteLine("the perfect pizza🤌  Suddenly, a sneaky Crust Bandit");
        Console.WriteLine("snatches your masterpiece!");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("\nFueled by passion for your craft, you give chase...");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("Through winding alleys and crowded streets, you");
        Console.WriteLine("pursue the pizza pilferer. Finally, the thief is");
        Console.WriteLine("cornered in a dead-end alley. It's time to recover");
        Console.WriteLine("your stolen slice!");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("                      FIGHT!                      \n");
	}
}
```



`**main.cs**` `**Program class**`

```csharp
class Program { 
	public static void Main() 
	{ 
		Game game = new Game(); 
		game.DisplayGameStory(); 
		game.SpawnCharacters(); 
	} 
}
```





You have successfully spawned the *Dough Master* and *Crust Bandit* in the game! 🥳

Currently, they are just saying their respective dialogues. We want them to have a *Battle *to save the *Dough Master's Masterpiece* 🤌

In the next chapter, let's create some abilities for them to initiate the *Battle *⚔️
