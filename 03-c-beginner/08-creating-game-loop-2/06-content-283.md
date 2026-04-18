So...

Now you are all done with ***C# Beginner***



Click here to see the complete code.

```csharp
using System;

class Player
{
    private int health = 100;
    private int attackDamage = 20;
    private int healingCapacity = 15;
    private int maxHealth = 100;

    public int Health
    {
        get { return health; }

        private set 
        {
            // If the value provided is negative, store zero instead
            if (value < 0)
                health = 0;
            else if(value > maxHealth)
            {
                health = maxHealth;
            }

            else
            {
                health = value; // Otherwise, store the provided value
            }

        }
    }

    
    public Player()
    {
        SpawnPlayer();
        DisplayPlayerStats();
    }


    private int generateRandomNumberInRange(int min, int max)
    {
        Random rand = new Random();
        int randomNumber = rand.Next(min, max + 1);
        return randomNumber;
    }

    public int CalculateTotalDamage()
    {
        int additionalDamage = generateRandomNumberInRange(5, 15);
        int totalDamage = attackDamage + additionalDamage;

        return totalDamage;
    }

    public int CalculateTotalHeal()
    {
        int additionalHeal = generateRandomNumberInRange(10, 20);
        int totalHeal = healingCapacity + additionalHeal;

        return totalHeal;
    }

    public void TakeDamage(int damageRecieved) => Health -= damageRecieved;


    public void Heal(int healAmount) => Health += healAmount;

    private void SpawnPlayer()
    {
        Console.WriteLine("\n==================================================");
        Console.WriteLine("   🍕 DOUGH MASTER: GUARDIAN OF THE GOLDEN CRUST 🍕   ");
        Console.WriteLine("==================================================\n");
        Console.WriteLine("\nDough Master: That scoundrel won't escape with my creation!\n");
    }

    public void DisplayPlayerStats()
    {
        Console.WriteLine("\n---------------------------------------------------");
        Console.WriteLine("              DOUGH MASTER'S STATS                ");
        Console.WriteLine("---------------------------------------------------");
        Console.WriteLine("Health: " + Health + "/" + maxHealth);
        Console.WriteLine("Dough Slapper: " + attackDamage);
        Console.WriteLine("Espresso Shot ☕: " + healingCapacity);
        Console.WriteLine("Dough Slapper Boost 🌪️: 5 to 15");
        Console.WriteLine("Espresso Shot Boost ☕: 10 to 20");
    }

    public void ShowAttackDamage(int totalDamage)
    {
        Console.WriteLine("             🍕 PIZZA BATTLE 🍕                   ");
        Console.WriteLine("============================================");
        Console.WriteLine("Dough Master's attack dealt " + totalDamage + " damage! 🥊");
        Console.WriteLine("--------------------------------------------");
    }

    public void ShowHeal(int healAmount)
    {
        if (Health >= maxHealth)
        {
            Console.WriteLine("             🍕 PIZZA BATTLE 🍕                   ");
            Console.WriteLine("============================================");
            Console.WriteLine("     Dough Master is bursting with energy! 🚀    ");
            Console.WriteLine("--------------------------------------------");
        }
        else
        {
            Console.WriteLine("             🍕 PIZZA BATTLE 🍕                   ");
            Console.WriteLine("============================================");
            Console.WriteLine("Dough Master's heal restored " + healAmount + " hp! ☕");
            Console.WriteLine("--------------------------------------------");
        }
    }
}

class Enemy
{
    private int health = 150;
    private int attackDamage = 15;
    private int maxHealth = 150;

    
    public int Health
    {
        set 
        {
            // If the value provided is negative, store zero instead
            if (value <= 0)
                health = 0;
            else if(value > maxHealth)
                health = maxHealth;
            else
                health = value; // Otherwise, store the provided value
        }
        get { return health; }
    }
    
    public Enemy()
    {
        SpawnEnemy();
        DisplayEnemyStats();
    }

    private int generateRandomNumberInRange(int min, int max)
    {
        Random rand = new Random();

        int randomNumber = rand.Next(min, max + 1);
        return randomNumber;
    }


    private void SpawnEnemy()
    {
        Console.WriteLine("\n==================================================");
        Console.WriteLine("   🦹 CRUST BANDIT: NEMESIS OF ITALIAN CUISINE 🦹  ");
        Console.WriteLine("==================================================\n");
        Console.WriteLine("\nCrust Bandit: \"This delectable pizza is mine now!");
        Console.WriteLine("You'll never catch me, flour face!\"\n");
    }

    public void DisplayEnemyStats()
    {
        Console.WriteLine("\n--------------------------------------------------");
        Console.WriteLine("            CRUST BANDIT'S STATS                ");
        Console.WriteLine("--------------------------------------------------");
        Console.WriteLine("Health: " + Health + "/" + maxHealth);
        Console.WriteLine("Sneaky Jab 💪: " + attackDamage);
        Console.WriteLine("Dirty Trick Bonus 🪄: 3 to 12");
    }

    public void ShowAttackDamage(int totalDamage)
    {
        Console.WriteLine("Crust Bandit's sneak attack dealt " + totalDamage + " damage! 💥");
        Console.WriteLine("============================================");
    }

    public int CalculateTotalDamage()
    {
        int additionalDamage = generateRandomNumberInRange(3, 12);
        int totalDamage = attackDamage + additionalDamage;

        return totalDamage;
    }

    public void TakeDamage(int damageRecieved) => Health -= damageRecieved;
}

class Game
{
    bool isGameExited;
    Player player;
    Enemy enemy;

    public void GameLoop()
    {
        while (!isGameExited)
        {
            DisplayGameStory();
            StartMenu();
            if (!isGameExited)
                RestartMenu();
        }
    }
    private void DisplayGameStory()
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

    private void StartMenu()
    {
        Console.WriteLine("==================================================");
        Console.WriteLine("     Press S to Get Your Masterpiece BACK...     ");
        Console.WriteLine("     Press any other key to exit the game   ");
        Console.WriteLine("==================================================");

        ProcessStartMenuInput();
    }

    private void RestartMenu()
    {
        Console.WriteLine("\n==================================================");
        Console.WriteLine("     Press R to Restart...     ");
        Console.WriteLine("     Press any other key to exit the game   ");
        Console.WriteLine("==================================================");

        ProcessRestartMenuInput();
    }

    private string GetInput()
    {
        string input = Console.ReadLine();
        return input.ToUpper();
    }

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

    private void SpawnCharacters()
    {
        //Initialize Player and Enemy objects
        player = new();
        enemy = new();
    }

    private void ProcessBattleLoop()
    {
        do
        {
            ShowBattleOptions();
            ProcessBattleInput();

        } while (AreCharactersAlive());
    }

    private bool AreCharactersAlive() => player.Health > 0 && enemy.Health > 0;

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

    private void PlayerAttack()
    {
        int totalDamage = player.CalculateTotalDamage();
        enemy.TakeDamage(totalDamage);
        player.ShowAttackDamage(totalDamage);
        
    }

    private void EnemyAttack()
    {
        int totalDamage = enemy.CalculateTotalDamage();
        player.TakeDamage(totalDamage);
        enemy.ShowAttackDamage(totalDamage);
        
    }

    private void PlayerHeal()
    {
        int totalHeal = player.CalculateTotalHeal();
        player.Heal(totalHeal);
        player.ShowHeal(totalHeal);
        
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


    private void ExitGame()
    {
        Console.Clear();
        Console.WriteLine("Thanks for playing Midnight Pizza Fight!😄");
        isGameExited = true;
    }

    private void InvalidInput() => Console.WriteLine("Invalid Input! , please give valid input");


    private void DisplayCharacterStats()
    {
        player.DisplayPlayerStats();
        enemy.DisplayEnemyStats();
    }
}

class Program
{
    public static void Main()
    {
        Game game = new Game();
        game.GameLoop();
    }
}
```





This project was supposed to prepare you for what's coming ahead... Unity!

Keep the little game dev inside you excited!

So far this was fun

And it'll be fun ahead too!



![Ready To Game Dev](/Full-Stack-Game-Development/images/93e3db34751fbb03.png)
