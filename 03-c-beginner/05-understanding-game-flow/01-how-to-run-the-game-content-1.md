How should this game flow? What should be the steps?

For example:

What are the steps to start an ***EA Sports FC 24 (PS: FIFA 24)*** game?

1. Start Splash Screen
2. Game Connects to the EA Server
3. Player has to *Press Any Key To Start* 
4. Start Menu: Player Selects Mode (Let's say Kick Off)
5. Player Selects Team
6. Player does any Team Management
7. Game Starts


[Watch video](https://www.loom.com/embed/85049d3b5841471884c781b1963b3205)



***Starting Kick-Off Match in FIFA 24***



Now, this looks like it has many steps, and this is just for a basic *Kick-Off* match.

Can you imagine if this FIFA was being made in C++, how would the `main()` look?!

Try to think💭 a little!

If you were writing the code for this game-loop in `main()`, how it would look like!

Did you think?



Well, now think how it would look for all the FIFA Modes!

Here is the basic Game Loop to start a game in FIFA

```text
1. Start Splash Screen
2. Connect to EA Server
3. Prompt "Press Any Key To Start"
4. Display Start Menu
5. Player selects mode
   - If Kick Off:
     - Player selects team
     - Player performs team management
     - Game starts
   - If Career Mode:
     - Choose Manager or Player Career
     - Set up career details (team, manager/player customization)
     - Begin career (transfer market, team selection, etc.)
   - If Ultimate Team:
     - Introduction to Ultimate Team if first time
     - Access to Ultimate Team hub
     - Manage team, transfer market, squad building challenges
     - Play matches (squad battles, weekend league, etc.)
   - If Pro Clubs:
     - Create or join a club
     - Customize player appearance and position
     - Play matches with club
   - If Volta Football:
     - Customize avatar
     - Choose match type (3v3, 5v5, etc.)
     - Play street football matches
6. Game loop continues based on selected mode
7. Exit game when player decides to quit

```





Now can you image how the `main()` would look?!



See, always remember:

The code should be modular!

Easy to read!

Easy to modify!



Now, how will you achieve this handling of the game-loop for a complex game like FIFA?

Well, how about you create a `**Game**` class?!



A `**Game**` class that can handle the entire game-loop!

You don't have to put all this burden on `main()`!



## Understanding Game Class


---



To understand what this `Game` class should do, you have to understand what all things happen in this game!




[Watch video](https://www.loom.com/embed/760b75558d0543bf8c1c1e31de6fca4f)



***MPF Gameplay Video***

Let's start listing down...

You ready?

Go!

1. Game Begins
2. Game's story is displayed
3. Characters are Spawned
4. Battle Begins
5. Battle Ends
6. Game Ends
7. All this while, Player is constantly giving inputs
8. There are different Menus
9. Stats for ***Dough Master*** and ***Crust Bandit*** are displayed on multiple occasions

We can discuss this in even more detail, but for now, this gives a good enough picture



Let's begin!



> **TODO: class **`**Game**`** **
> ✅ Create an empty `Game` class



## Displaying the Story


---



Let's begin with moving the story logic to `Game` class



> **TODO: class **`**Game**`** **
> ✅ Create a `public void DisplayGameStory()` 
> Inside it:
> ✅ Clear the console using: `Console.Clear()` 
> ✅ Write the code to display the entire lore



> **TODO: class **`**Program**` 
> Inside `Main()`:
> ✅ Clear the story printed.
> ✅ Create object of `Game` class using the `new` keyword: `game` 
> ✅ Call `game.DisplayGameStory()` before creation of player and enemy objects.



Click here to see the class Game and class Program.

`**class Game**`

```csharp
class Game
{
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



`**class Program**`

```csharp
class Program
{
    public static void Main()
    {
        Game game = new Game();
        game.DisplayGameStory();
        Player player = new Player();
        Enemy enemy = new Enemy();
    }
}
```







You have displayed the story. It's time to spawn the characters!

In the next lesson, you'll spawn the characters by creating the objects of their respective classes!

**See you there!👋🏻**
