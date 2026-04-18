In this lesson, you'll understand what a battle loop is!



# What is a Battle Loop?


---

The battle loop is the flow of the battle.

What the hell is the flow of the battle?!

![  ](/Full-Stack-Game-Development/images/5104b048d693428b.webp)



Let's understand the **"Flow of the Battle!" **using our game *Midnight Pizza Fight*!



# Flow of the Battle


---

Flow of the battle controls the battle between *Dough Master* and *Crust Bandit* step by step.



![ ](/Full-Stack-Game-Development/images/20513fc8a7e29b9c.png)

***Flow of Battle Loop***



A separate function will handle this flow: `ProcessBattleLoop()`

> **TODO**
> **✅ **In the `Game` class, create `public void ProcessBattleLoop()`



**Note: **You'll change the access modifier of the `ProcessBattleLoop()`** **to `private` in the next chapter. It's currently `public` to test the Battle Loop.



Battle Loop for the *Midnight Pizza Fight *can be divided into two major parts:

1. **Show Battle Options**
2. **Process the Player's Input** based on the option selected.

Both these steps will keep on running until one of the characters dies!



# Show Battle Options


---



In this section, you need to show the options that the player can choose from.
You must make sure that the options are shown in a presentable way.

This is the first step in the battle loop, so the `ShowBattleOptions()` will be called in the `ProcessBattleLoop()` function.

**Expected Output:**



```text
==================================================
             🍕 PIZZA BATTLE OPTIONS 🍕             
==================================================
  Choose your action:
    [A] Attack the Crust Bandit 🥊
    [H] Gulp an Espresso Shot ☕
==================================================
  Your choice:  
```



> **TODO**
> **✅**In `Game` class create `private void ShowBattleOptions()`
> ✅In `ShowBattleOptions()` function, display the Attack and heal options.
> ✅In `ProcessBattleLoop()` function call the `ShowBattleOption()` function.



Click here to see the solution.

`**Main.cs**`** **`**Game class**`



```csharp
public void ProcessBattleLoop()
 {
          ShowBattleOptions();
 }
```

```csharp
private void ShowBattleOptions()
    {
        Console.WriteLine("\n==================================================");
        Console.WriteLine("             🍕 PIZZA BATTLE OPTIONS 🍕             ");
        Console.WriteLine("==================================================");
        Console.WriteLine("  Choose your action:");
        Console.WriteLine("    [A] Attack the Crust Bandit 🥊");
        Console.WriteLine("    [H] Gulp an Espresso Shot ☕");
        Console.WriteLine("==================================================");
        Console.Write("  Your choice: ");
    }
```





Now, you need to process the player's input.



# Process Player's Battle Input


---

`ProcessBattleInput()` will be a separate function, as it'll handle so many things(refer to the flow diagram of Battle Loop)



> **TODO**
> **✅**In `Game` class create an empty `private void ProcessBattleInput()` function
> ✅In `ProcessBattleLoop()` function call the `ProcessBattleInput()` function.



Click here to see the solution.

`**Main.cs**`** **`**Game class**`

```csharp
public void ProcessBattleLoop()
 {
          ShowBattleOptions();
          ProcessBattleInput();
 }
```



```csharp
private void ProcessBattleInput()
{

}
```





That being said, let's implement the rest of the processes individually!

The first step in the process battle input is to get the player's input!



## **Get Player Input**


---

Firstly, you need to get the player's input.

How do you get the Player's input?🤔

The `Console.ReadLine()`  function can be used to get the player's input.



> **PROTIP💡: **`**Console.ReadLine()**`
> Implementation of the `Console.ReadLine()` function:

> **Reads** an entire line of text from the input stream.

> **Returns** the input as a `string`.

> **Useful for** capturing multi-character input, such as words, sentences, or any text input, until the user presses the `Enter` key.



> **PROTIP💡: Input Stream**

> Refers to the flow of data from the user.



Then, this input will be stored in a variable `string input` and returned.



> **PROTIP💡: String Methods**
> To avoid checking both lowercase and uppercase letters you can use the `ToUpper()` string method!
> There are more string methods like `ToLower()`, `ToString()`, and more to work with strings.



> **🧠MORE BRAINS: Sring Methods**
>  [https://learn.microsoft.com/en-us/dotnet/api/system.string?view=net-8.0](https://learn.microsoft.com/en-us/dotnet/api/system.string?view=net-8.0)



Now, to get the input, you will create a function `GetInput()` .

Then, you can use `Console.ReadLine()` to get the player's input and turn the input into upper case using `ToUpper` and then return the input.

In the `ProcessBatlleInput()` function, you can call the `GetInput()` function and store the returned input in a local variable.

Now you have the player's input and can clear the console to show the Battle⚔️ in a clear console.



> **TODO**
> **✅**In `Game` class create `private string GetInput()`
> ✅In the `GetInput()` function get the player's input in a local variable `string input`, convert it to uppercase and return the `input` variable.
> ✅In the `ProcessBattleInput()` store the input returned by `GetInput()` in a local variable `playerChoice`
> ✅Clear the console.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
private void ProcessBattleInput()
    {
        string playerChoice = GetInput();
        Console.Clear();
    }
```



```csharp
private string GetInput()
    {
        string input = Console.ReadLine();
        return input.ToUpper();
    }
```





You have the input. Now what?🤔

You need to check if the player has given "**A**", "**H**", or some invalid input.



## Checking the Input


---



How to check the Input? If-Else If? Yeah, but you have already used it in C++ beginner🥱

Let's use switch-case statements! 

Basically, there will be three cases: "**A**", "**H**" or **Invalid Input**.

Here's how the **switch-case** statements for these cases will work:



```csharp
switch (playerChoice)
{
    case "A":
        // Code block for value1
        break;
    case "H":
        // Code block for value2
        break;
    ...
    default:
        // Default code block if no case matches
        break;
}
```



If the `playerChoice` is **A**, then the code block in `case "A"` will execute.
If `playerChoice` is **H,** then the code block for `case "H"` will execute, 
otherwise, the code block for the default case executes!



> **TODO**
> **✅**In `ProcessBattleInput()` function, create `switch` statement for the `playerChoice`
> ✅In the `switch` block create three cases, "**A**", "**H**" and **default**.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
public void ProcessBattleInput()
    {
        string playerChoice = GetInput();
        Console.Clear();
        
        switch (playerChoice)
        {
            case "A":
                break;
                
            case "H":
                break;

            default:
                break;
        }
    }
```





Now, it's time to use the combat functionalities you created in the Player and the Enemy classes!💪

Let the Battle Begin!!⚔️



## Player's Turn


---

So, it's the player's turn now!

The player can drop a *Dough Slapper *to the *Crust Bandit* 🥊!

Or Heal himself by gulping an *Expresso Shot *☕!



`PlayerAttack()` and `PlayerHeal()` will be separate functions. Remember SRP?!



> **TODO**
> **✅**In the `Game` class** **create the  `private void PlayerAttack()` and `private void PlayerHeal()` functions.



**Player Attack**

Firstly, you need to call the `CalculateTotalDamage()` function of the `Player` class and store it in a local variable `int totalDamage`

Then, *Crust Bandit's* health will be reduced by `totalDamage` using the `TakeDamage(totalDamage)` function of the Enemy class.

Lastly, the damage will be shown on the console using the `ShowAttackDamage(totalDamage)` function of the `Player` class.



**Player Heal**

Similar to Attack, `totalHeal` will store the heal amount returned by `Player` class's `CalculateTotalHeal()`

Then, the `Heal(totalHeal)` function adds the `*totalHeal*`* *to the *Dough Master's* health.

Lastly, the total heal will be shown on the console using the `ShowHeal(totalHeal)` function of the `Player` class.



> **TODO**
> In the  `PlayerAttack()` function:

> ✅Call the `player.CalculateTotalDamage()` and store its value in `int totalDamage`
> ✅Call the `enemy.TakeDamage(totalDamage)`
> ✅Call the `player.ShowAttackDamage(totalDamage)`

> In the  `PlayerHeal()` function:

> ✅Call the `player.CalculateTotalHeal()` and store its value in int `totalHeal`
> ✅Call the `player.Heal(totalHeal)`
> ✅Call the `player.ShowHeal(totalHeal)`



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
private void PlayerAttack()
    {
        int totalDamage = player.CalculateTotalDamage();
        enemy.TakeDamage(totalDamage);
        player.ShowAttackDamage(totalDamage);
    }
    
private void PlayerHeal()
    {
        int totalHeal = player.CalculateTotalHeal();
        player.Heal(totalHeal);
        player.ShowHeal(totalHeal);
    }
```





The `PlayerAttack()` & `PlayerHeal()` functions are now ready!

Now, you need to call them in the switch statements in their respective cases.



> **TODO**

> ✅In `ProcessBattleInput()` function in the `case "A":` call the `PlayerAttack()` function.
> ✅In `ProcessBattleInput()` function in the `case "H":` call the `PlayerHeal()` function.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
public void ProcessBattleInput()
    {
        string playerChoice = GetInput();
        Console.Clear();
        
        switch (playerChoice)
        {
            case "A":
            //Player's Turn
            PlayerAttack();
            
                break;
                
            case "H":
            //Player's Turn
            PlayerHeal();
            
                break;

            default:
                break;
        }
    }
```





The player's turn is now complete.

It's *Crust Bandit's* turn to drop a *Sneaky Jab💪* to the *Dough Master*! 



## Enemy's Turn


---

The enemy's turn is similar to the player's turn.

The *Crust Bandit* only can attack the *Dough Master*.



> **TODO**
> **✅**In the `Game` class** **create the  `private void EnemyAttack()`  function.



**Enemy Attack**

You need to call the `CalculateTotalDamage()` function of the `Enemy` class and store it in a local variable `int totalDamage`

Then, *Dough Master's* health will be reduced by `totalDamage` using the `TakeDamage()` function of the `Player` class.

Lastly, the damage will be shown on the console using the `ShowAttackDamage(totalDamage)` function of the `Enemy` class.



> **TODO**
> In the  `EnemyAttack()` function:

> ✅Call the `enemy.CalculateTotalDamage()` and store its value in `int totalDamage`
> ✅Call the `player.TakeDamage(totalDamage)`
> ✅Call the `enemy.ShowAttackDamage(totalDamage)`



Click here to see the solution.

`**Main.cs**`** **`**Game class**`

```csharp
private void EnemyAttack()
    {
            int totalDamage = enemy.CalculateTotalDamage();
            player.TakeDamage(totalDamage);
            enemy.ShowAttackDamage(totalDamage);
    }
```





Now, you need to call the `EnemyAttack()` function in the switch statement.

In both the attack and heal cases, the Crust Bandit can only attack.



> **TODO**

> In `ProcessBattleInput()` function in the `switch-case`'s  `case "A":` and `case "H":`

> ✅Call the `EnemyAttack()` function after Player Attacks and Heals



Click here to see the solution.

`**Main.cs**`** **`**Game class**`

```csharp
public void ProcessBattleInput()
    {
        string playerChoice = GetInput();
        Console.Clear();
        
        switch (playerChoice)
        {
            case "A":
            //Player's Turn
            PlayerAttack();
            //Enemy's Turn
            EnemyAttack();
                break;
                
            case "H":
            //Player's Turn
            PlayerHeal();
            //Enemy's Turn
            EnemyAttack();
                break;

            default:
                break;
        }
    }
```





Tired? Don't Worry 😌

Grab a cup of coffee  ☕, and take a break for a few minutes. Then, let's complete the Battle Loop! 💪



## Display Character Stats


---

You have already created functions in the `Player` and the `Enemy` class to display their stats.

`player.DisplayPlayerStats()` and `enemy.DisplayEnemyStats()` will be called in a separate function `DisplayCharacterStats()`

This way, if you want to display the stats of both characters in the future, you can call the `DisplayCharacterStats()` function.



> **TODO**
> **✅**In the `Game` class** **create the  `private void DisplayCharacterStats()`  function.
> 
> In the `DisplayCharacterStats()` function:

> ✅Call the `player.displayPlayerStats()` function.
> ✅Call the `enemy.displayEnemyStats()` function.

> In `ProcessBattleInput()` function in the `switch-case`'s  `case "A":` and `case "H":`

> ✅Call the `DisplayCharacterStats()` function.



Click here to see thee solution.

`**Main.cs**`** **`**Game class**`

```csharp
public void ProcessBattleInput()
    {
        string playerChoice = GetInput();
        Console.Clear();
        
        switch (playerChoice)
        {
            case "A":
            //Player's Turn
            PlayerAttack();
            //Enemy's Turn
            EnemyAttack();
            
            DisplayCharacterStats();
                break;
                
            case "H":
            //Player's Turn
            PlayerHeal();
            //Enemy's Turn
            EnemyAttack();
            
            DisplayCharacterStats();
                break;

            default:
                break;
        }
    }
```



```csharp
private void DisplayCharacterStats()
    {
        player.DisplayPlayerStats();
        enemy.DisplayEnemyStats();
    }
```





## Check Game Over


---

Lastly, you need to check the game over condition.



> **TODO**
> **✅**In the `Game` class** **create the  `private bool CheckGameOver()`  function.



Game over can be two different cases,

- If the enemy's health touches 0, the player wins the game!🏆
- If the player's health touches 0, the player loses the game!💀



> **TODO**
> **✅**In the `Game` class** **create the  `private void ShowGameWin()`  and `private void ShowGameLose()` functions.



**Show Game Win**

The `ShowGameWin()` function will clear the console and then display the game win message.



```text
==================================================
           🎉 PIZZA JUSTICE SERVED! 🎉              
==================================================
The Dough Master has defeated the Crust Bandit!
--------------------------------------------------
The perfect pizza has been reclaimed 🍕           
The honor of Italian cuisine is restored!         
--------------------------------------------------
    Bon appétit, and thanks for playing! 👨‍🍳        
==================================================
```



**Show Game Lose**

The `ShowGameLose()` function will clear the console and then display the game lose message.



```text
==================================================
              😭 PIZZA TRAGEDY! 😭                
==================================================
The Dough Master has been outmaneuvered!           
--------------------------------------------------
The Crust Bandit escapes with your masterpiece 🏃‍♂️
Your pizzeria's reputation is in shambles 📉     
--------------------------------------------------
        Thanks for your valiant effort! 🎖️         
   Perhaps it's time to switch to calzones... 🥟   
==================================================
```



> **TODO**
> **✅**In the `private void ShowGameWin()`  function clear the console and print the game win message.
> ✅In the `private void ShowGameLose()` function clear the console and print the game lose message.
> 
> In the `CheckGameOver()` function:

> ✅If  `enemy.Health` reaches  0, call the `ShowGameWin()` Function.
> ✅If `player.Health` reaches 0, call the `ShowGameLose()` Function.

> 

> In `ProcessBattleInput()` function inside `switch-case`'s `case "A":` and `case "H":`

> ✅Call the `CheckGameOver()` function.



**Note: **`CheckGameOver()` will be called whenever either of the characters' health reaches 0. The switch statement will break.



So, can the health of either of the characters reach 0 if the player or the enemy attacks?🤔

Yes! So, you need to check the game over after both of these functionalities.

But, can the health of the either of the character reach 0 if the player heals?🤨

No, right?! Remember, this is right after the player has healed!



Click here to see the solution.

`main.cs` `Game class`

```csharp
private void ProcessBattleInput()
	    {
        string playerChoice = GetInput();
        Console.Clear();

        switch (playerChoice)
        {
            case "A":
                //Player's Turn
                PlayerAttack();
                
                if (CheckGameOver())
                    break;
                //Enemy's Turn
                EnemyAttack();

                if (CheckGameOver())
                    break;

                DisplayCharacterStats();
                break;

            case "H":
                //Player's Turn
                PlayerHeal();
                //Enemy's Turn
                EnemyAttack();

                if (CheckGameOver())
                    break; 

                DisplayCharacterStats();
                break;

            default:
                break;
        }
    }

    private bool CheckGameOver()
    {
        if (enemy.Health <= 0)
        {
            ShowGameWin();
            return true;
        }
        if (player.Health <= 0)
        {
            ShowGameLose();
            return true;
        }
        return false;
    }
    
    private void ShowGameWin()
    {
        Console.Clear();
        Console.WriteLine("\n==================================================");
        Console.WriteLine("           🎉 PIZZA JUSTICE SERVED! 🎉              ");
        Console.WriteLine("==================================================");
        Console.WriteLine("The Dough Master has defeated the Crust Bandit!");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("The perfect pizza has been reclaimed 🍕           ");
        Console.WriteLine("The honor of Italian cuisine is restored!         ");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("    Bon appétit, and thanks for playing! 👨‍🍳        ");
        Console.WriteLine("==================================================");
    }

    private void ShowGameLose()
    {
        Console.Clear();
        Console.WriteLine("\n==================================================");
        Console.WriteLine("              😭 PIZZA TRAGEDY! 😭                ");
        Console.WriteLine("==================================================");
        Console.WriteLine("The Dough Master has been outmaneuvered!           ");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("The Crust Bandit escapes with your masterpiece 🏃‍♂️");
        Console.WriteLine("Your pizzeria's reputation is in shambles 📉     ");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("        Thanks for your valiant effort! 🎖️         ");
        Console.WriteLine("   Perhaps it's time to switch to calzones... 🥟   ");
        Console.WriteLine("==================================================");
    }
```





## Invalid Input


---

Invalid input will be the default case, as any input other than "**A**" or "**H**" is invalid.

What should you do if the player gives an invalid input?🤔

Easy! Just print a message that the input is invalid and break out of the switch statement!

**Expected Output:**



```text
Invalid Input! , please give a valid input
```



> **TODO**
> **✅**In the `Game` class** **create the  `private void InvalidInput()`  function.
> ✅In the `InvalidInput()` function print the message for invalid input.
> ✅In the `ProcessBattleInput()` in the `switch` block call the `InvalidInput()` function in the `default` case.



Click here to see the solution.

`**Main.cs**`** **`**Game class**`

```cpp
    private void ProcessBattleInput()
    {
        string playerChoice = GetInput();
        Console.Clear();

        switch (playerChoice)
        {
            case "A":
                //Player's Turn
                PlayerAttack();
                if (CheckGameOver())
                    break;
                //Enemy's Turn
                EnemyAttack();

                if (CheckGameOver())
                    break;

                DisplayCharacterStats();
                break;

            case "H":
                //Player's Turn
                PlayerHeal();
                //Enemy's Turn
                EnemyAttack();

                if (CheckGameOver())
                    break; 

                DisplayCharacterStats();

                break;

            default:
                InvalidInput();
                break;
        }
    }
```

```csharp
private void InvalidInput() => Console.WriteLine("Invalid Input! , please give a valid input");
```





The flow for the battle is almost ready!

You need to repeat these steps until one of the characters dies!



# Are Characters Alive?


---

You'll implement the battle loop again if both the characters are alive.

Otherwise, the battle loop will end!

How do you repeat the steps?🤔

Loops!!



> **💡PRO TIP: Loops**

> Loops are fundamental concepts in programming used to execute a block of code repeatedly.



Here, you are checking a condition to repeat a process. Hence, you need a `while` or a `do-while` loop.

In this case, `do-while`  loop makes more sense, as battle options will be shown and processed at least once before checking the characters' status. 



**Note**: You'll learn about other loops at the end of the chapter.



> **TODO**
> **✅**In the `Game` class** **create the  `private bool AreCharactersAlive()`  function.
> ✅In the `AreCharactersAlive()` function check if the health of the player and enemy is greater than 0.
> ✅In the `ProcessBattleLoop()`  `while` `AreCharactersAlive()` returns true `do` `ShowBattleOptions()` `ProcessBattleInput()`



> **PROTIP💡: Conditional Operators**

> Conditional operators allow you to combine multiple conditions.

> **&& (AND)**: Returns true if both conditions are true.

> **|| (OR)**: Returns true if at least one condition is true.

> **! (NOT)**: Reverses the result of a condition.



**Note**: You'll need the **&&(AND)** for `AreCharactersAlive()` method.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
public void ProcessBattleLoop()
    {
        do
        {
            ShowBattleOptions();
            ProcessBattleInput();
        } while (AreCharactersAlive());
    }
    
    private bool AreCharactersAlive() => player.Health > 0 && enemy.Health > 0;
```





Battle Loop is now Ready!!! 🥳 Finally!😌

It's time to test the battle loop you created! 🎮



> **TODO**
> **✅**Call the `ProcessBattleLoop()` function of the `Game` class in the `Main()` function
> ✅Play the game!🎮



Click here to see the solution.

`**main.cs**`** **`**Program class**`

```csharp
class Program 
{ 
	public static void Main() 
	{ 
		Game game = new Game(); 
		game.DisplayGameStory(); 
		game.SpawnCharacters();
		game.ProcessBattleLoop();
	} 
}
```







You can see the game works!!

In the next lessons, you'll learn about taking input and loops in C# in detail!

See you there!👋
