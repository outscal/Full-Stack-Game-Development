In previous content you created a class called `**ParalyzedEffect**` which implemented the interface `**IStatusEffect**`.



But apart from just **Paralyze**, there can be multiple kinds of status effects in your game.

How are you going to store each different types and maintain a list of them in your code?



think .. think.. think ...



Answer![c++](https://media1.tenor.com/m/onTlUVMtWy4AAAAC/rickroll-rick.gif)



The Answer (Real One)

Yes, you thought correctly.
You should use an **Enum** for different types of Status Effects.







This will allow you to store different status effects in one place, making it easier to reference them throughout the code.



> **TODOs :**
> ✅ Create a new header file named `**StatusEffectType.hpp**` inside the `**StatusEffects**` folder.
> ✅ Add a header guard or use `#pragma once` to prevent multiple inclusions of the header file.
> ✅ Inside the file, declare a namespace named `**N_Pokemon**` to keep the code organized.
> ✅ Inside `N_Pokemon`, create a nested namespace called `**N_StatusEffects**` to group status effect-related code.
> ✅ Define an `**enum class**` named `**StatusEffectType**` inside the `N_StatusEffects` namespace.
> ✅ Inside the `StatusEffectType` enum, add the following status effects as members:

> **       PARALYZED, SLEEPING, BURNED, POISONED**
> ✅ Close the namespaces `N_StatusEffects` and `N_Pokemon` to properly encapsulate the code.





StatusEffectType.hpp```cpp
#pragma once

namespace N_Pokemon
{
    namespace N_StatusEffects
    {
        enum class StatusEffectType
        {
            PARALYZED,
            SLEEPING,
            BURNED,
            POISONED
        };
    }
}
```




---



Now let's get back to our main concern. 

At the end of your previous material, although you created `**ParalyzedEffect**`, you were not able to use it.

Why were you not able to use it?

Because you have not yet integrated it with your battle loop.

But then the question arises, how should you exactly integrate it in your battle loop?



Let's think about it logically,

This is how your battle loop looks currently:

```cpp
void BattleManager::battle()
  {
    while (battleState.battleOngoing)
    {
      if (battleState.playerTurn)
        battleState.playerPokemon->selectAndUseMove(battleState.wildPokemon);
      else
        battleState.wildPokemon->selectAndUseMove(battleState.playerPokemon);

      updateBattleState();
      battleState.playerTurn = !battleState.playerTurn;
      Utility::waitForEnter();
    }
    handleBattleOutcome();
  }
```



Now where does status effects fit in the above code exactly?

Let's think about how can status effects actually influence the battle loop:

1. In each turn, the applied status effect (if any) must be inflicted on pokemons
2. Some of the status effects like paralyze or sleep may restrict the pokemon to move, skipping its chance from the battle loop.



Given the above 2 scenarios,

Lets consider there is a function inside `**Pokemon**` class which tells us if that Pokemon is able to move this turn or not.

Lets call this method `**canAttack()**`

This function whenever called, can check if there is any applied status effect on this pokemon and return a bool value, indicating whether it can move this turn or not.



So considering such a function exists, you can call it in your battle loop, before actually performing a Pokemon's move

Then your updated Battle Loop Code will look like this:

```cpp
void BattleManager::battle()
  {
    while (battleState.battleOngoing)
    {
      if (battleState.playerTurn && battleState.playerPokemon->canAttack())
        battleState.playerPokemon->selectAndUseMove(battleState.wildPokemon);
      else if (battleState.wildPokemon->canAttack())
        battleState.wildPokemon->selectAndUseMove(battleState.playerPokemon);

      updateBattleState();
      battleState.playerTurn = !battleState.playerTurn;
      Utility::waitForEnter();
    }
    handleBattleOutcome();
  }
```




---



Now obviously your code is going to throw error since you have neither declared or defined a function called `**canAttack()**` inside Pokemon class!

So let's go ahead and make a few changes in your Pokemon class.



But apart from the `**canMove()**` method, is there anything else that you need to update inside Pokemon Class?

Also, How are you going to implement this method exactly?



Let's answer the second question first!

To implement `**canMove()**` function, you need to check first if a status effect has been applied to your Pokemon!

How will you check that?

I think you should create a property in Pokemon class to hold that data.

By that, I mean having a variable called `**appliedEffect**` declared inside the Pokemon class.

Can you guess what will be the type of this variable ?????????







Yes, you are correct! Its going to be a *pointer* of type `**IStatusEffect**` 



> **TODOs **: `Pokemon.hpp`
> ✅ Add a new member variable `IStatusEffect* appliedEffect` to track the current status effect applied to the Pokémon.
> ✅ Declare the function **canAttack()** that will check if the Pokémon can attack based on the status effect.




Now, coming back to the first question, are there some other things that you need to declare in the Pokemon class ???

Answer me this, How is the value of `**appliedEffect**` going to be updated?

You must create another, no no no, actually you need to create 2 other functions, one to apply a status effect and one to clear any previously applied status effect.



> **TODOs **: `Pokemon.hpp`
> ✅ Declare the function **applyEffect(StatusEffectType effectToApply)** to apply the appropriate status effect to the Pokémon.
> ✅ Declare the function **clearEffect()** to clear any status effect currently applied to the Pokémon.




But now I have another question 😂 

If a status effect is already applied, should you be able to override it and apply a new status effect?

Well, it is a design choice to be fair, but for our game, if a status effect has already been applied, new one will not be applied.

Just to keep it simple.



But then again you need something to check if you can actually apply a status effect to a Pokemon or not.



> **TODOs **: `Pokemon.hpp`
> ✅ Declare the function **canApplyEffect()** that checks if a new status effect can be applied (i.e., if no effect is currently applied).





Now your `**Pokemon.hpp**` should look like this:



Solution (Pokemon.hpp)

```cpp
#pragma once
#include <string>
#include <vector>
#include "Move.hpp"
#include "StatusEffects/IStatusEffect.hpp"
#include "StatusEffects/StatusEffectType.hpp"

using namespace std;
using namespace N_Pokemon::N_StatusEffects;

namespace N_Pokemon {

    struct Move;
    enum class PokemonType;
    
    class Pokemon {
    public:
        std::string name;
        PokemonType type;
        int health; 
        int maxHealth; 
        vector<Move> moves; // Store the list of moves
        IStatusEffect* appliedEffect;
    
        Pokemon(); 
        Pokemon(std::string p_name, PokemonType p_type, int p_health, vector<Move>);
        Pokemon(Pokemon* other);
    
        bool isFainted() const;
        void heal();
        virtual void attack(Move selectedMove, Pokemon* target);
        void takeDamage(int damage);
        void selectAndUseMove(Pokemon* target);
        void reduceAttackPower(int reduced_damage);
        bool canAttack();
        bool canApplyEffect();
        void applyEffect(StatusEffectType effectToApply);
        void clearEffect();

    protected:
        // Base implementation for selecting and using a move
        void printAvailableMoves();
        int selectMove();
        void useMove(Move selectedMove, Pokemon* target);
    };
}
```






---



You have declared so many new methods in `**Pokemon.hpp**`, so its time now that you define the logic inside them.

Let's go one by one:



1. `canAttack()` 

This function should check whether the Pokemon can still attack.

This function should first check if there is any active status effect (`appliedEffect != null`). 

If there isn’t, the Pokémon can attack normally.

If there is an applied effect, 

It should inflict the turn end effect for the applied effect. 

And it should return true or false based on whether that effect prevents the Pokémon from attacking or not.



2. `canApplyEffect()`

This function should check if a new status effect can be applied to the Pokémon.

 It should return `true` only if the Pokémon is not currently under any status effect (i.e., `appliedEffect == nullptr`).



3.  `clearEffect()`

This function should clear the current status effect by setting `appliedEffect` to `nullptr`. 

Once the effect is cleared, the Pokémon can act normally again.



4.`applyEffect(StatusEffectType effectToApply)`

This function should apply the given status effect to the Pokémon. 

It should check which type of status effect needs to be applied, like **PARALYZED**, and assigns the appropriate effect to `**appliedEffect**`.





So, Seems pretty straightforward, right?

Then get to work now:


> **TODOs **: Pokemon.cpp
> ✅ Initialize the `appliedEffect` member variable to `nullptr` in the constructor to indicate no status effect at the start.
> ✅ Implement the **canAttack()** method to check if the Pokémon can attack:

> Return `true` if no status effect is applied (i.e., `appliedEffect == nullptr`).

> If an effect is applied, call `turnEndEffect()` from the current effect to determine whether the Pokémon can attack.
> ✅ Implement the **canApplyEffect()** method to check if a new status effect can be applied:

> Return `true` if no status effect is currently applied (i.e., `appliedEffect == nullptr`).
> ✅ Implement the **applyEffect(StatusEffectType effectToApply)** method to assign a status effect to the Pokémon:

> Use a switch statement to check the effect type (e.g., **PARALYZED**) and apply the corresponding effect using the appropriate class.

> Call the `applyEffect()` method on the new effect.
> ✅ Implement the **clearEffect()** method to remove the current status effect by setting `appliedEffect` to `nullptr`.





Solution (Pokemon.cpp)

```cpp
#include <iostream>
#include "../../include/Pokemon/Pokemon.hpp"
#include "../../include/Pokemon/PokemonType.hpp"
#include "../../include/Pokemon/StatusEffects/ParalyzedEffect.hpp"
#include "../../include/Utility/Utility.hpp"
using namespace std;

namespace N_Pokemon {

  // Default constructor
  Pokemon::Pokemon() {
    name = "Unknown";
    type = PokemonType::NORMAL;
    health = 50;
    maxHealth = 50;
  }
  
  // Parameterized constructor
  Pokemon::Pokemon(string p_name, PokemonType p_type, int p_health, vector<Move> p_moves) {
    name = p_name;
    type = p_type;
    maxHealth = p_health;
    health = p_health;
    moves = p_moves;
    appliedEffect = nullptr;
  }
  
  // Copy constructor
  Pokemon::Pokemon(Pokemon* other) {
    name = other->name;
    type = other->type;
    health = other->health;
    maxHealth = other->maxHealth;
    moves = other->moves;
  }
  
  // Reduce HP by the damage amount
  void Pokemon::takeDamage(int damage) {
    health -= damage;
    if (health < 0) {
      health = 0;
    }
  }

  void Pokemon::selectAndUseMove(Pokemon* target)
  {
    printAvailableMoves();

    int choice = selectMove();
    Move selectedMove = moves[choice-1];
    
    useMove(selectedMove, target);
  }

  void Pokemon::reduceAttackPower(int reduced_damage)
  {
    for(int i=0; i<moves.size(); i++)
    {
      moves[i].power -= reduced_damage;
      if(moves[i].power < 0)
        moves[i].power = 0;
    }
  }

  bool Pokemon::canAttack()
  {
    if(appliedEffect == nullptr)
      return true;
    else
      return appliedEffect->turnEndEffect(this);
  }

  bool Pokemon::canApplyEffect() { return appliedEffect == nullptr; }

  void Pokemon::applyEffect(StatusEffectType effectToApply)
  {
    switch (effectToApply)
    {
    case StatusEffectType::PARALYZED:
      appliedEffect = new ParalyzedEffect();
      appliedEffect->applyEffect(this);
      break;
    default:
      appliedEffect = nullptr;
    }
  }

  void Pokemon::clearEffect() { appliedEffect = nullptr; }

  void Pokemon::printAvailableMoves()
  {
    cout << name << "'s available moves:\n";

    // List out all moves for the player to choose from
    for (size_t i = 0; i < moves.size(); ++i) {
      cout << i + 1 << ": " << moves[i].name << " (Power: " << moves[i].power << ")\n";
    }
  }

  int Pokemon::selectMove()
  {
    // Ask the player to select a move
    int choice;
    cout << "Choose a move: ";
    cin >> choice;

    // Validate the choice
    while (choice < 1 || choice > static_cast<int>(moves.size())) {
      cout << "Invalid choice. Try again: ";
      cin >> choice;
    }

    return choice;
  }

  void Pokemon::useMove(Move selectedMove, Pokemon* target)
  {
    cout << name << " used " << selectedMove.name << "!\n";
    attack(selectedMove, target);
    
    N_Utility::Utility::waitForEnter();

    cout << "...\n"; 
    N_Utility::Utility::waitForEnter();
    
    if (target->isFainted())
      cout << target->name << " fainted!\n";
    else
      cout << target->name << " has " << target->health << " HP left.\n";
  }

  void Pokemon::attack(Move selectedMove, Pokemon* target) { target->takeDamage(selectedMove.power); }

  // Check if the Pokemon has fainted
  bool Pokemon::isFainted() const { return health <= 0; }
  
  // Restore health to full
  void Pokemon::heal() { health = maxHealth; }
} // namespace N_Pokemon
```






---



Now, there is just one last cherry on the top left!



To actually apply the Paralyze Effect 😂 ... through a move like **Thundershock**.



You needed to add logic to actually apply the **PARALYZED** status when Pikachu uses this move.



Pikachu.cpp```cpp
#include "../../../include/Pokemon/Pokemons/Pikachu.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include "../../../include/Pokemon/Move.hpp"
#include <iostream>
namespace N_Pokemon {
    namespace N_Pokemons {
      
        using namespace std;
        Pikachu::Pikachu()
                : Pokemon("Pikachu", PokemonType::ELECTRIC, 100, {
                    Move("THUNDER SHOCK", 20),
                    Move("QUICK ATTACK", 10),
                    Move("THUNDER BOLT", 80)
                }) {}

        void Pikachu::attack(Move selectedMove, Pokemon* target)
        {

            if(selectedMove.name == "THUNDER BOLT")
            {
                // 80% chance to hit
                if (rand() % 100 < 80)
                { 
                    Pokemon::attack(selectedMove, target);
                    std::cout << "... and it hit successfully!\n";
                }
                else
                    std::cout << "... but it missed!\n";
            }
            else
                Pokemon::attack(selectedMove, target);
```

            if(selectedMove.name == "THUNDER SHOCK")

            {

                if(target->canApplyEffect())

                    target->applyEffect(StatusEffectType::PARALYZED);

            }

        }

  }

}



Now, when Pikachu uses **Thunder Shock**, it checks if the target Pokémon can have a status effect applied, and if so, it paralyzes the target.



You’ve done it! 

Now, status effects like **Paralysis** are fully working in your game. 



Pokémon battles are more fun and challenging.
As these effects can stop attacks and change the way the game plays out.



Your hard work has made your game more exciting and closer to real Pokémon battles. 
Keep going—there's more to explore!



**Great Job🎉!**
