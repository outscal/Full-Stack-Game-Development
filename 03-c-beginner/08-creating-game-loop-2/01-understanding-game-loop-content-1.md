You might think that the game is working now!

What is a game loop?! Why do we need a game loop now?



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/09_03_2024__07_11_32.gif)



Don't worry. All your questions will be answered in this lesson!!



# What is a Game Loop?


---

The game loop controls the execution of different elements of the game. 

For Example: Spawning Characters, Showing different menus, Running Battle Loop and more!



In the current code,  the Story, Spawning of Characters and the battle loop are shown at once on the console.

Also, when the game win/ lose message is displayed, there's no option to restart the game.

The game loop will basically separate the **Story**, **Start Logic **and **Restart Logic**, making the game more structured and readable.



Let's set up the game loop, and then we'll understand it in detail!



# Setting Up Game Loop


---

How can you implement the game loop without a game loop function!🤷



> **TODO**
> **✅**In `Game` class create `public void GameLoop()` function.



Okay, so now that you have created the `GameLoop()` function, you can remove everything from the `Main()` function except for the object of the `Game` class. And call the `GameLoop()` function using the object of the `Game` class.

Yeah, I know `GameLoop()` function is empty! But not for long!😉



> **TODO**
> **✅**In `Main()` function remove `DisplayGameStory()` , `SpawnCharacters()` and `ProcessBattleLoop()` functions.
> **✅**In `Main()` function call the `game.GameLoop()` function.



Click here to see the solution.

`**main.cs**`** **`**Program class**`

```csharp
class Program
{
    public static void Main()
    {
        Game game = new Game();
        game.GameLoop();
    }
}
```





> **PROTIP💡: **`**private**` functions
> It's always a good practise to keep the functions `private` if they are not used outside the class.



> **TODO**
> **✅**In `Game` class make the `DisplayGameStory()` , `SpawnCharacters()` and `ProcessBattleLoop()` functions `private`.



The setup for Game Loop is ready!

Let's complete the game!! 💪



# Understanding Game Loop


---

![Game Loop Flow Diagram](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/09_05_2024__10_57_08.png)

**Flow diagram for Game Loop**

The flow of the Game Loop can be divided into three parts:

- Displaying Story
- Start Menu
- Restart Menu

Let's break down each of these parts to implement the game loop properly.



# Implementing Game Loop


---

Let's start with the story!



## Displaying Story


---

This part is as simple as its name!

You need to display the only story on the console. That's it!!

You have already created a function to display the story. 

So there's nothing new in this part, except calling it from the `GameLoop()` function and not `Main()` function.



> **TODO**
> **✅**In `GameLoop()` function call `DisplayGameStory()` function.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
public void GameLoop()
{
     DisplayGameStory();
}
```





1st part done! 😌

Next? **Start Menu**!



## Start Menu


---

Now, instead of directly spawning the characters and starting the battle loop, there can be a Start Menu.

This way, the player can read the story and then decide whether to start the game or not.

Expected Start Menu:



```text
==================================================
     Press S to Get Your Masterpiece BACK...     
     Press any other key to exit the game   
==================================================
```



Then, you need to process the start menu input.



> **TODO**
> **✅**In `Game` class create `private void StartMenu()` and  `private void ProcessStartMenuInput()` functions.
> ✅In `StartMenu()` print the start menu and call the `ProcessStartMenuInput()`



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
private void StartMenu()
{
        Console.WriteLine("==================================================");
        Console.WriteLine("     Press S to Get Your Masterpiece BACK...     ");
        Console.WriteLine("     Press any other key to exit the game   ");
        Console.WriteLine("==================================================");

        ProcessStartMenuInput();
 }
 
 private void ProcessStartMenuInput() {}
```





**Processing Start Menu Input**

The player can choose to start the game by giving "**S**" as input or any other input to exit the game.



**How to Start the Game?**

If** **player gives **"S" input**, then the console will be cleared to show a fresh screen.

Characters will spawn and then the Battle Loop will start! ⚔️



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/09_03_2024__10_41_13.png)

**Characters are spawned and battle loop starts**



> **TODO:**
> In `ProcessStartMenuInput()` :

> ✅Get player's input in `string startGame` using `GetInput()`
> ✅Clear the console, call `SpawnCharacters()` and `ProcessBattleLoop()` if `startGame` is **"S"**



Click here to see the solution.

```csharp
private void ProcessStartMenuInput()
    {
        string startGame = GetInput();

        if (startGame == "S")
        {
            Console.Clear();
            SpawnCharacters();
            ProcessBattleLoop();
        }
  }
```





For any input other than **"S"**, the console will be cleared and the game will exit.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/09_03_2024__10_48_05.png)

**Exit Game**



> **TODO**
> **✅**In `Game` class** **create an empty function `private void ExitGame()`
> **✅**Call `ExitGame()` for any other input.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
private void ProcessStartMenuInput()
    {
        string startGame = GetInput();

        if (startGame == "S")
        {
            Console.Clear();
            SpawnCharacters();
            ProcessBattleLoop();
        }
        else
        {
            ExitGame();
        }
    }
   
   private void ExitGame()
   {
              
   } 
```





The last part was the restart menu. But before you jump into the restart menu, you must understand why tracking whether the player exits the game is important.



## Is Game Exited?


---

The game loop will keep on running until the player exits the game.

How will you know if the player has exited the game?🤔

You can use a `bool isGameExited`, and when the player exits the game, set it to true. False otherwise.

Using `isGameExited` as a condition, you can use the `while` loop to run the game loop until `isGameExited` is set to true.



But when should you set it to true?🤔

`ExitGame()` ? Yeah, it makes sense! 

Also, in the `ExitGame()` function, you must clear the console and show a message.



**Expected Exit Game Message:**

```text
Thanks for playing Midnight Pizza Fight!😄
```



> **TODO**
> **✅**In `Game` class** **create `bool isGameExited`
> **✅**In `ExitGame()` function, clear the console, show the message on the console and set `isGameExited` to true.
> 
> In the `GameLoop()` function:

> ✅Create a `while(!isGameExited)` loop
> ✅Call the `DisplayGameStory()` and `StartMenu()` in the `while` loop.



Click here to see the solution.

`**Main.cs**`** **`**Game class**`

```csharp
class Game
{
    bool isGameExited = false;
    Player player;
    Enemy enemy;

    public void GameLoop()
    {
        while (!isGameExited)
        {
            DisplayGameStory();
            StartMenu();
        }
    }
    
     //rest of the code
     
 		private void ExitGame()
     {
             Console.Clear();
             Console.WriteLine("Thanks for playing Midnight Pizza Fight!😄");
             isGameExited = true;
     }
}    
```





Now, let's jump into the final part!😌

**Restart Menu**!



## Restart Menu


---

Now, suppose that the player has started the game, battle loop is completed and the player ends up on either game win or game lose screen.

Currently, the `Main()` function ends as the battle loop ends. There's no option for the player to restart the game.



**Processing Restart Menu Input**

You need to show a restart menu when the game ends.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/09_03_2024__11_05_21.png)

**Restart Menu**



After showing the restart menu, the player's restart menu input will be processed.



> **TODO**
> **✅**In `Game` class create `private void RestartMenu()` and  `private void ProcessRestartMenuInput()` functions.
> ✅In `RestartMenu()` print the restart menu and call the `ProcessRestartMenuInput()`
> ✅In `GameLoop()` function call the `RestartMenu()` function after the `StartMenu()` function.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
private void RestartMenu()
    {
        Console.WriteLine("\n==================================================");
        Console.WriteLine("     Press R to Restart...     ");
        Console.WriteLine("     Press any other key to exit the game   ");
        Console.WriteLine("==================================================");

        ProcessRestartMenuInput();
    }
    
    public void GameLoop()
        {
                while (!isGameExited)
                {
	                DisplayGameStory();
	                StartMenu();
	                RestartMenu();
                }
        }
```





**How to Restart the Game?**

If player gives **"R" **input, then the game starts from the story part again!

For any input other than **"R"** exit the game.



> **TODO**
> In `ProcessRestartMenuInput()` :

> ✅Get player's input in `string restartGame` using `GetInput()`
> ✅Set `isGameExited` to false  if  `restartGame` is **"R"**
> **✅**Call `ExitGame()` otherwise.



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
private void ProcessRestartMenuInput()
    {
        string restartGame = GetInput();
        
        if (restartGame == "R")
        {
            isGameExited = false;
        }
        else
        {
            ExitGame();
        }
    }
```





Restart Menu is also now ready!

There's still a small problem, though. Can you figure it out?!🤔



**Hint: **Try playing** **the game and exit in the start menu.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/10_04_2024__06_32_51.png)



## Completing the Game Loop!


---

Were you able to figure out the problem using the hint?

No? 🥲

Don't worry 😌 I'll explain the problem.

Let's look at the `GameLoop()` function to understand the problem.



```csharp
public void GameLoop()
{
	while (!isGameExited)
	{
		DisplayGameStory();
		StartMenu();
		RestartMenu();
	}
}
```



When the `StartMenu()` is executed, the `while` loop has already started executing.

So when the player exits the game in the `StartMenu()`, `isGameExited` is set to true, and then `RestartGame()` is executed.

Now, why is `RestartGame()` executing if the condition of the while loop does not match? 
Shouldn't the while loop break as soon as the condition is violated?! 🤔

Well, the answer is NO! Once the while loop has started its execution, the condition will be checked only after the code in the while block has completed its execution.



Due to this, the player will have to exit the game twice!

You can do it if you want to annoy the player 🥲

Or you can add a check for `isGameExited` before calling the `RestartMenu()` function.



> **TODO**
> **✅**In `GameLoop()` function If the game is not exited, call the `RestartMenu()` function
> ✅Play the game, notice how organised it looks😌



Click here to see the solution.

`**main.cs**`** **`**Game class**`

```csharp
public void GameLoop()
{
	while (!isGameExited)
	{
		DisplayGameStory();
		StartMenu();
		if(!isGameExited)
			RestartMenu();
	}
}
```





You have completed your first C# game!👏

Congratulations!!🥳
