The time has come to bring your Pokémon battles to life!

You’ve worked hard, figuring out how to manage health, calculate damage, and make turn-based fights.

Now, let’s combine everything and see it in action!



By the end of this lesson, you'll have a fully working battle loop in your game.

Your Pokémon will be able to fight wild Pokémon, exchange attacks, and come out as either the winner or the loser.



This is where everything starts to feel real. 

You’ll be creating something that resembles the true heart of Pokémon battles.



Now, You already understand the importance of Soc, Separation of concern.

You have to create a battle loop that contains different functionality.

Like starting the battle between Pokemon and handling the battle outcome.



Let’s make a new class to handle all the battle stuff in one place and keep things organised.

Keep the name of class is **BattleManager**.



This class will be in charge of handling all the parts of the battle. 

It will manage the health, damage, and turns of both the player's Pokémon and the wild Pokémon. 



# High-Level Overview of the Battle Loop


---



The **BattleManager** will act as a guide.

Controlling the battle from start to finish.

Making sure everything happens in the right order.



Now, Let's Focus on how Battle will work -



Start the Battle

The player encounters a wild Pokémon. 

At this point, the **BattleManager** steps in and starts the battle. 

It gets things ready, showing your Pokémon and the wild Pokémon you’ll battle.



Turns

Once the battle begins, the **BattleManager** takes control of the turns. 

Your Pokémon and the wild Pokémon will take turns attacking each other. 

The player makes a move, and then the wild Pokémon responds. 







Health Check

After each turn, the **BattleManager** will check if either Pokémon has fainted. 

It keeps an eye on both the player’s Pokémon and the wild Pokémon’s health. 



If a Pokémon’s health drops to zero, the battle starts moving toward its conclusion.



End of Battle

If the wild Pokémon faints, the player wins the battle. 



But if the player’s Pokémon faints, the game ends.

And it’s time to return to the PokéCenter to heal.



The battle loop, controlled by the BattleManager, works like a turn-based game. 

Each step is connected, ensuring the battle moves smoothly from beginning to end.





# Implementing the BattleManager Class


---



Now, it’s time to introduce the **BattleManager** class. 

Think of this class as the brain behind the battle. 



It’s responsible for handling everything that happens during a battle,
from when it starts to when it ends.



The **BattleManager** is important because it keeps everything related to the battle organized. 

Instead of having battle logic scattered all over your code.

You will have one class that manages the entire flow. 





# Declaring `BattleManager` Class


---



It will manage to start the battle, actual battle between pokemon and outcome of battle.



> **TODOs**

> ✅ create `BattleManager.hpp` header class.

> ✅Declare `startBattle `Method and Pass Player object `player `& pokemon object `wildPokemon` as Parameter.

> ✅Declare `battle` Method and Pass Pokemon object `playerPokemon `& pokemon object `wildPokemon` as Parameter.

> ✅Declare `HandleBattleOutcome` Method and Pass Pokemon object `playerPokemon `& `bool` parameter.





 BattleManager.hpp -  Solution```cpp
// BattleManager.hpp

#include "Pokemon.hpp"
#include "Player.hpp"

class BattleManager {
public:
    void startBattle(Player &player, Pokemon &wildPokemon);
private:
    void battle(Pokemon &playerPokemon, Pokemon &wildPokemon);
    void handleBattleOutcome(Player &player, bool playerWon);
};

```



Explanation of the BattleManager Methods :)



startBattle(Player &player, Pokemon &wildPokemon)

This is the method that kicks off the battle.

 When the player encounters a wild Pokémon, this function is called, and the battle begins.



battle(Pokemon &playerPokemon, Pokemon &wildPokemon)

This method is where the actual battle happens. 

It controls the turns, making sure both the player’s Pokémon and the wild Pokémon take their attacks in order. 

The battle keeps going until one of the Pokémon faints.



handleBattleOutcome(Player &player, bool playerWon)

Once the battle is over, this method is called to figure out what happens next. 

If the player’s Pokémon wins, the player is rewarded. 

If the player loses, the game can react appropriately, like sending them back to the PokéCenter to heal.





# Implementing the Battle Loop with BattleManager


---



Let's implement the BattleManager class and its methods.

Which will encapsulate the battle logic.



**1. Starting the Battle**

           The **BattleManager** will start the battle when the player encounters a wild Pokémon. 

                     The battle begins with a message and then jumps into the core battle logic.



> **TODO: **
> ✅ Implement `startBattle `Method in `BattleManager` class.

> ✅ print the statement for wild pokemon appeared given below.

> ✅call the `battle` Method for start battle and pass argument player `chosenPokemon` and `wildPokemon`.





startBattle Method - Solution```cpp
void BattleManager::startBattle(Player &player, Pokemon &wildPokemon) {
            std::cout << "A wild " << wildPokemon.name << " appeared!\n";
                battle(player.chosenPokemon, wildPokemon);
}     
```



**2.  Creating the **`**Battle **`**Method**

                    You have already created the actual battle loop, where both Pokémon take turns attacking until one faints. 

                    The player’s Pokémon attacks first. If the wild Pokémon is still standing, it attacks back. 

                    The loop continues until one Pokémon faints. After the battle, the outcome is processed.

                    

 The **BattleManager** will manage these turns and handle what happens during and after the battle.



> **TODO: **
> ✅ Implement `Battle `Method of `BattleManager` class.



> **NOTE **:  You have already created that `battle` Method in Previous lessons. you can just copy paste it here.



battle Method - Solution```cpp
void BattleManager::battle(Pokemon &playerPokemon, Pokemon &wildPokemon) {
    while (!playerPokemon.isFainted() && !wildPokemon.isFainted()) {
        // Player attacks first
        playerPokemon.attack(wildPokemon);

        // Check if wild Pokémon fainted
        if (!wildPokemon.isFainted()) {
            // Wild Pokémon attacks back
            wildPokemon.attack(playerPokemon);
        }

        // Pause to show the result of each turn
        Utility::waitForEnter();
    }

    // Determine and display the outcome of the battle
    handleBattleOutcome(playerPokemon, playerPokemon.isFainted());
}

```

**3.** **Handling the Battle Outcome**

**                    **Finally, let’s define what happens after the battle. 

                    If the player’s Pokémon wins, the game congratulates them. 

                    If it loses, the player is prompted to heal at the PokéCenter.



Now, it's time to make changes in a code.

> **TODO: **
> ✅ Implement `handleBattleOutcome `Method of `BattleManager` class.

> ✅ Put if-else statement and set condition is `playerWon`.

> ✅ Print `playerWon` true or false print the following statement given below respectively .





if -else statements

```cpp
[player.chosenPokemon.nam ]  is victorious! Keep an eye on your Pokémon's health.
Oh no!    [player.chosenPokemon.name]   fainted! You need to visit the PokeCenter.
```



handleBattleOutcome Method - Solution

```cpp
void BattleManager::handleBattleOutcome(Player &player, bool playerWon) {
    if (playerWon) {
        std::cout << player.chosenPokemon.name << " is victorious! Keep an eye on your Pokémon's health.\n";
    } else {
        std::cout << "Oh no! " << player.chosenPokemon.name << " fainted! You need to visit the PokeCenter.\n";
        Utility::waitForEnter();
        std::cout << "Game Over.\n";
    }
}

```



This method determines if the player won or lost and displays the appropriate message. 

If the player loses, it suggests visiting the PokéCenter for healing.



# Integrating the BattleManager into the Game Loop


---



Now, let’s update your **gameLoop** method to integrate the **BattleManager** class, which will handle the wild Pokémon battles.





BattleManager Integration

- A `BattleManager battleManager`, instance is created at the start of the `gameLoop` to handle wild Pokémon battles,
  When the player chooses to battle a wild Pokémon (`case 1`).
- The game now generates a random wild Pokémon using the `WildEncounterManager` 
  And passes both the player's Pokémon and the wild Pokémon to the `BattleManager`. 
  The battle is then handled by `battleManager.startBattle(player, wildPokemon);`.



Visiting the PokéCenter

In `case 2`, the player can visit the PokéCenter to heal their Pokémon. 

`player.chosenPokemon.heal()` function is used to fully restore the Pokémon's health.







Quitting the Game

The quitting process (`case 5`) is unchanged in logic.
But it still gives the player a humorous warning from Professor Oak before they are allowed to quit.



If the player chooses "yes" (`'y'`), the game loop stops by setting `keepPlaying` to `false`





It's time to make changes in a code :



> **TODO: **
>   ✅ Update `gameLoop `Method of `Game` class

> ✅ Update `Case 1` of switch case handling battle.

> ✅ Create an instance encounterManager of WildEncounterManager  in `case 1`.

> ✅ Create an random wildPokemon throurgh `getRandomPokemonFromGrass` in `case 1.`

> ✅ Call the `startBattle` Method of `BattleManager`  and pass the parameter Player object `player` & `wildPokemon` object in `case 1`.

> ✅ Call the `player.chosenPokemon.heal()` in the case 2.







gameLoop - Code```cpp
void Game::gameLoop(Player &player) {
    BattleManager battleManager;
    bool keepPlaying = true;

    while (keepPlaying) {
        Utility::clearConsole();
        std::cout << "\\nWhat would you like to do next, " << player.name << "?\\n";
        std::cout << "1. Battle Wild Pokémon\\n";
        std::cout << "2. Visit PokeCenter\\n";
        std::cout << "3. Challenge Gyms\\n";
        std::cout << "4. Enter Pokémon League\\n";
        std::cout << "5. Quit\\n";
        std::cout << "Enter your choice: ";
        int choice;
        std::cin >> choice;

        Utility::clearInputBuffer();

        switch (choice) {
            case 1: {
                WildEncounterManager encounterManager;
                Pokemon wildPokemon = encounterManager.getRandomPokemonFromGrass(forestGrass);
                battleManager.startBattle(player, wildPokemon);
                break;
            }
            case 2: {
                std::cout << "You head to the PokeCenter.\\n";
                player.chosenPokemon.heal(); // Heal the player's Pokémon
                std::cout << player.chosenPokemon.name << "'s health is fully restored!\\n";
                break;
            }
            case 5: {
                keepPlaying = false;
                break;
            }
            default: {
                std::cout << "That's not a valid choice. Try again!\\n";
                break;
            }
        }

        Utility::waitForEnter();
    }

    std::cout << "Goodbye, " << player.name << "! Thanks for playing!\\n";
}

```





**Great Job🎉!**
