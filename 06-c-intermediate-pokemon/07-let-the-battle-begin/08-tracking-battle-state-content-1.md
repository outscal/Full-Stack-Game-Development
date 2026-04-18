In the previous lessons,

you understood the battle loop and the health parameter.



Imagine being in the heat of a Pokémon battle.

Each decision, and move could be the difference between victory and defeat.



So, to demonstrate each move,

you need to keep track of everything happening in the battle.



But how does the game keep track of everything that happens in a battle?

Don't worry. You will learn it in this lesson.



# Battle State


---

What do you understand by the term 'state'?

'State' is nothing but the current condition of something.



So, the 'battle state' means the battle's current condition,

in simple words, I can explain it like,

what exactly is going on in the battle currently.



For a clear understanding, below are the critical aspects of the battle state

- Health Status: The current health of each Pokémon involved in the battle.
- Turn Management: Which Pokémon’s turn is it to attack?
- Battle Outcome: Whether the battle is ongoing, won, or lost.
- Additional State Elements: (Future considerations) Status effects, buffs/debuffs, etc.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/dbbb4a68548f1141.png)







# Implement battle state in the code


---

> **TODO:**
> ✅Create a header file with the name BattleState.hpp
> ✅Create a struct to encapsulate all the aspects of battle state
> ✅Make two pointers of Pokemon type, one for player and other one for wild
> ✅Make two boolean variable to store turn and if the battle is ongoing or finished



BattleState.hpp```cpp
// BattleState.hpp
#include "Pokemon.hpp"

struct BattleState {
    Pokemon *playerPokemon;  // Pointer to the player's Pokémon
    Pokemon *wildPokemon;    // Pointer to the wild Pokémon
    bool playerTurn;          // True if it's the player's turn, false otherwise
    bool battleOngoing;       // True if the battle is still ongoing
};
```



Notice that `playerPokemon` and `wildPokemon` have an asterisk(*****) before them?

But why?🤔

This is because these variables are not regular objects, they are ***Pointers!***

You'll understand pointers in the ***Pointers*** chapter. 

For now, you can just create them and move on.



Explanation

- `playerPokemon` and `wildPokemon`: Pointers to the Pokémon involved in the battle.
- `playerTurn`: Boolean to track whose turn it is.
- `battleOngoing`: Boolean to track whether the battle is still active.



Since you have created the battle state header file,

now, you need to use this in your code.



Do you remember the file that manages the whole battle?

Isn't it Battle Manager?



What are you waiting for? 

Let's go and integrate BattleState in BattleManager



> **TODO:**
> ✅Include BattleState.hpp in BattleManager header file
> ✅Initialize an object of BattleState type in the BattleManager header file
> ✅Use that variable to store current Pokemon in startBattle function in the source file of BattleManager
> ✅Set playerTurn and battleOngoing as true in the beggining





BattleManager.hpp```cpp
// BattleManager.hpp

#include "BattleState.hpp"
#include "Player.hpp"

class BattleManager {
public:
    void startBattle(Player &player, Pokemon &wildPokemon);
private:
    BattleState battleState;  // New BattleState object to track the battle

    void battle();
    void handleBattleOutcome();
    void updateBattleState(); // Method to update the battle state after each turn
};
```



startBattle()```cpp
void BattleManager::startBattle(Player &player, Pokemon &wildPokemon) {
    battleState.playerPokemon = &player.chosenPokemon;
    battleState.wildPokemon = &wildPokemon;
    battleState.playerTurn = true;  // Player starts first
    battleState.battleOngoing = true;

    std::cout << "A wild " << wildPokemon.name << " appeared!\\n";
    battle();
}
```





# Manage turns and Battle Progress


---

In the above section, you have initialised the **battle state**.

Now, it's time to implement the **Pokemon turns** in the battle.



Let's try to think about it step by step.

Player Pokemon and wild Pokemon are hitting each other turn by turn.



So, if the boolean variable `playerTurn` is true at some instance,

What do you think should happen next?



In this case, the player's Pokemon should first attack the wild Pokemon,

that will result in a decrease in the wild Pokemon's health.



Then you need to check if the wild Pokemon is still able to fight or,

he has been fainted.



If he has fainted, the battle will be over.



If the battle is continued, then wild Pokemon should get the turn, 

which means, you need to set `playerTurn` to false.



Similarly, every step will be followed again.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/30fb3d3cd19b5bf4.png)







`battle():` This loop alternates turns between the player and the wild Pokémon, updating the battle state after each turn.



battle()```cpp
void BattleManager::battle() {
    while (battleState.battleOngoing) {
        if (battleState.playerTurn) {
            // Player's turn to attack
            battleState.playerPokemon->attack(*battleState.wildPokemon);
        } else {
            // Wild Pokémon's turn to attack
            battleState.wildPokemon->attack(*battleState.playerPokemon);
        }

        // Update the battle state after the turn
        updateBattleState();

        // Switch turns
        battleState.playerTurn = !battleState.playerTurn;

        Utility::waitForEnter();
    }

    handleBattleOutcome();
}
```





`updateBattleState():` This method checks if either Pokémon has fainted and updates the battleOngoing flag accordingly.



updateBattleState()```cpp
void BattleManager::updateBattleState() {
    if (battleState.playerPokemon->isFainted()) {
        battleState.battleOngoing = false;
    } else if (battleState.wildPokemon->isFainted()) {
        battleState.battleOngoing = false;
    }
}
```





# Handling the Battle Outcome


---

> **TODO:**
> ✅Create handleBattleOutcome() function
> ✅Add if-else statement in it
> ✅Print the congratulatory statement if wild Pokemon looses
> ✅Print that player's Pokemon has lost the game if wild Pokemon wins





`handleBattleOutcome():` This method checks the final state of the battle and displays the appropriate outcome message.



handleBattleOutcome()```javascript
void BattleManager::handleBattleOutcome() {
    if (battleState.playerPokemon->isFainted()) {
        std::cout << battleState.playerPokemon->name << " has fainted! You lose the battle.\\n";
    } else {
        std::cout << "You defeated the wild " << battleState.wildPokemon->name << "!\\n";
    }
}
```
