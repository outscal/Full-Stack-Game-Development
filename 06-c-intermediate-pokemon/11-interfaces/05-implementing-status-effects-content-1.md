In the last lesson, you’ve created the interface for status effects.

It’s time to make the battles more exciting by adding real effects! 



***Are you ready to bring these effects to life? ***



There are many status effects in the Pokémon game, like Paralyzed, Burn, and Poison.



I will guide you in implementing the Paralyzed effect in your game code.
After that, you will implement the other status effects on your own.



But before implementing the Paralyzed effect, let’s first understand what the Paralyzed effect is in the real Pokémon game.




---



When a Pokémon gets paralyzed, it may not be able to move for a few turns. 
There is also a chance that the paralysis will stop it from attacking completely.


You had to make this effect feel realistic and unpredictable, just like in the Pokémon games. 



**Let’s think together: **

*How should the Paralyzed effect be implemented?*
*What functionality or methods are needed to make this work?*



The first thing You thought about was, how to apply the effect. 
You wanted the player to know that their Pokémon is paralyzed.



So You should print a message like: “**Your Pokémon is paralyzed! It may not be able to move!**”

You can randomly choose a duration between 1 and 3 turns.


To handle this, you can create a method `applyEffect()`.




Since paralysis can wear off after a few turns.

You need to track how long the Pokémon stays paralyzed.
Should it last for a specific number of turns? 
If yes, we need a variable to track the remaining turns .



You can create a variable `turnsLeft` to keep track of the number of turns remaining before the effect wears off.





You also needed a way for the game to display the effect’s name during the battle. 
To handle this , you can create a method  `getEffectName()`. 





Third, you have to decide what happens at the end of each turn. 

***Will the Pokémon be able to move? ***



Paralysis should make it harder for the Pokémon to act.
So you gave it a **25% chance of stopping the Pokémon** from attacking. 



But the effect doesn’t last forever.
So you also check if the effect has worn off.



If all the turns affected by the **paralysis are over, remove the paralysis** effect entirely.



If paralysis effect is **still active**, **reduce** the duration of the paralysis **effect by one turn**.
but don’t remove it until all turns have been used.



To handle this, You can create a Method `turnEndEffect().`



Finally, when the paralysis wears off, You can remove the effect. 

Once the effect is gone, we print a message to let the player know.



You can use `clearEffect()`  method to handle this. 





Before Implementation, First Create a header file of `ParalyzedEffect.hpp` in `StatusEffects`folder that contains all these interface methods.

Which you have to implement in the `ParalyzedEffect.cpp` later.



> TODOs : 
> ✅ Create a header file named **ParalyzedEffect.hpp**.
> ✅ In the header file, ensure the class **ParalyzedEffect** inherits from **IStatusEffect** using public inheritance.
> ✅ Declare a private member variable `int turnsLeft` to track how many turns the paralysis will last.
> ✅ Declare the public methods that override the functions in **IStatusEffect**:

> `applyEffect(Pokemon* target)`

> `getEffectName()`

> `turnEndEffect(Pokemon* target)`

> `clearEffect(Pokemon* target)`:



**ParalyzedEffect.hpp**```cpp
#pragma once
#include "IStatusEffect.hpp"

namespace N_Pokemon
{
    namespace N_StatusEffects
    {
        class ParalyzedEffect : public IStatusEffect
        {
        private:
            int turnsLeft; // Track the remaining turns for the effect
        public:
            void applyEffect(Pokemon* target) override;
            std::string getEffectName() override;
            bool turnEndEffect(Pokemon* target) override;
            void clearEffect(Pokemon* target) override;
        };
    }
}
```



And now You have Implemented all the Methods of Paralyzed effect.


---




# Creating the `ParalyzedEffect`


---

Now, You will Implement all of these Method, for giving life to `ParalyzedEffect` in a game.



Lets' Implement `applyEffect()` Function.

First, Print a Information that your pokemon is paralyzed and it may not able to move.

and also sets paralyzed effect will last  between 1 and 3 turns by using rand() Method.



> **TODOs **:
>  ✅ Implement the `applyEffect()` Method in `ParalyzedEffect.cpp` class.
>  ✅ Pass a pointer to Pokemon Object `target` as a parameter of `applyEffect()` class.



This method sets the duration of the paralysis and informs the player that the effect has been applied.



applyEffect() - Click Here```cpp
void ParalyzedEffect::applyEffect(Pokemon* target){
            std::cout << target->name << " is paralyzed! It may not be able to move!\n";

            // Effect lasts between 1 and 3 turns randomly
            turnsLeft = rand() % 3 + 1;
}
```



Now, This is the way to display the Effect name that applied on the pokemon.



> **TODOs**:
> ✅ Implement the `getEffectName()` Method in `ParalyzedEffect.cpp` class.





getEffectName() - Click Here```cpp
string ParalyzedEffect::getEffectName() {
    return "Paralyzed";
}
```



Now, at the end of each turn, check the status of the Paralyzed effect.
If the number of turns for the Paralyzed effect has finished, clear the Paralyzed effect.
If the effect is still active, decrease the remaining turns by 1.



Also, generate a random number between 0 and 3 to check if the Pokémon is paralyzed or not.
If the generated number is 0, return `false`, indicating the Pokémon can't act.
Otherwise, it can act normally, and return `true`.



> TODOs :
> ✅ Implement the `turnEndEffect()` method in the **ParalyzedEffect** class.
> ✅ Check if `turnsLeft` is less than or equal to 0. If so, call `clearEffect()` to remove the paralysis and return `true` (indicating the Pokémon can move).
> ✅ Decrease the value of `turnsLeft` by 1 at the end of each turn.
> ✅ Generate a random number between 0 and 3 using `rand() % 4`.
> ✅ If the generated number is 0, print a message saying the Pokémon is paralyzed and return `false` (indicating it cannot act).
> ✅ If the generated number is not 0, print a message saying the Pokémon can move and return `true` (indicating it can act normally).





turnEndEffect() - Click Here```cpp
  bool ParalyzedEffect::turnEndEffect(Pokemon* target){
            if (turnsLeft <= 0) {
                clearEffect(target);
                return true; // Can move as the effect is cleared
            }
            turnsLeft--;

            // Generates a number between 0 and 3
            int paralysis_chance = rand() % 4; 

            // 25% chance that the Pokémon cannot move due to paralysis
            if (paralysis_chance == 0)
            {
                std::cout << target->name << " is paralyzed! It can't move!\n";
                return false; // Pokémon cannot act this turn
            }

            // Otherwise, it can act normally
            std::cout << target->name << " shakes off the paralysis momentarily and can move!\n";
            return true; // Pokémon can act this turn
}
```



If the number of turns for which the Pokémon is paralyzed has finished, clear the Paralyzed effect.



> TODOs :
> ✅ Implement the `clearEffect()` method in the **ParalyzedEffect** class.
> ✅ In the `clearEffect()` method, print a message saying the target Pokémon is no longer paralyzed, including the Pokémon's name.
> ✅ Call the `clearEffect()` method on the **target** Pokémon to remove the paralysis effect from the Pokémon.





clearEffect() - Click Here```cpp
void ParalyzedEffect::clearEffect(Pokemon* target) {
            std::cout << target->name << " is no longer paralyzed!\n";
            target->clearEffect();
    
}
```



And now You Implemented all the Method of Paralyzed effect.



Let's Look at the Final Code:



ParalyzedEffect.cpp```cpp
#include "../../../include/Pokemon/StatusEffects/ParalyzedEffect.hpp"
#include "../../../include/Pokemon/Pokemon.hpp"
#include "../../../include/Pokemon/StatusEffects/StatusEffectType.hpp"
#include <iostream>

namespace N_Pokemon
{
    namespace N_StatusEffects
    {
        void ParalyzedEffect::applyEffect(Pokemon* target)
        {
            std::cout << target->name << " is paralyzed! It may not be able to move!\n";

            // Effect lasts between 1 and 3 turns randomly
            turnsLeft = rand() % 3 + 1;
        }

        std::string ParalyzedEffect::getEffectName()
        {
            return "Paralyzed";
        }

        // Determines whether the Pokémon can act at the end of the turn
        // Returns false if the paralysis prevents the Pokémon from moving
        bool ParalyzedEffect::turnEndEffect(Pokemon* target)
        {
            if (turnsLeft <= 0) {
                clearEffect(target);
                return true; // Can move as the effect is cleared
            }
            turnsLeft--;

            // Generates a number between 0 and 3
            int paralysis_chance = rand() % 4; 

            // 25% chance that the Pokémon cannot move due to paralysis
            if (paralysis_chance == 0)
            {
                std::cout << target->name << " is paralyzed! It can't move!\n";
                return false; // Pokémon cannot act this turn
            }

            // Otherwise, it can act normally
            std::cout << target->name << " shakes off the paralysis momentarily and can move!\n";
            return true; // Pokémon can act this turn
        }

        void ParalyzedEffect::clearEffect(Pokemon* target)
        {
            std::cout << target->name << " is no longer paralyzed!\n";
            target->clearEffect();
        }
    }
}
```




---



In the next lesson, you’ll take these status effects.

And fully integrate them into the battle system.


Making them an active part of your Pokémon’s strategy. 

Get ready to see how these effects can change the course of a fight!



**Great Job!🎉**
