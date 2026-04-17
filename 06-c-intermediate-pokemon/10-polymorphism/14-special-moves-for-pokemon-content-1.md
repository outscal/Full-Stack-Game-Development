So, how are you feeling now?



You have done so much in your code till now.

Are you Excited and Happy? 🥳



In the last lesson,

you created the functionality of multiple moves.



There is a vector that has all the moves that a Pokemon can have.

You can insert as many moves as you want for any particular Pokemon,

without changing the code much.



That is the Power of writing the code in a structured way. 😎





Now, this lesson is also going to be very exciting.

You will implement some special moves for the Pokemon.



Till now, all the moves have a similar format.

Player is supposed to select a particular move,

then you will execute it,

and then the health of the opponent decreases.



But now, in this lesson,

moves will have some more functionalities.



Curious to know? 

Hold on tight with me!!!





# Special Moves


---

What do ordinary moves do,

they just do some damage to the opponent.



Special moves will also damage the opponent,

but there is some unique logic in them.



You remember the Thunder Bolt special move in real Pokemon Game?

You will include that kind of special moves in your game.



There will be a special move in your game where,

the possibility of hitting the target is 80%.

That means the move may get missed, too.



*You can even make your own custom special moves.*



Now, let's see how you can implement special moves in your game.





# Coding Time


---

Before moving to the special moves,

there is a little issue with your code.



Look at `BattleManager.cpp` file,

for now, it is directly calling `attack` function.

```cpp
battleState.playerPokemon->attack(battleState.wildPokemon);
```



But this is wrong,

first, the Player should see the list of Pokemon,

then he would select one of them,

then the attack should be called.



`attack` should only be kept just to give damage to the opponent.



So, you need to change your code a little bit.

`BattleManager.cpp` should look like

```cpp
battleState.playerPokemon->selectAndUseMove(battleState.wildPokemon);
```



And re-define the `attack` function in `Pokemon.cpp`.

```cpp
void Pokemon::attack(Move selectedMove, Pokemon* target) { target->takeDamage(selectedMove.power); }
```





Now that you have declared the attack function,

now it's time to call it from `useMove()`



```cpp
// useMove

void Pokemon::useMove(Move selectedMove, Pokemon* target){
    cout << name << " used " << selectedMove.name << "!\n";
    
    attack(selectedMove, target);		// Calling attack() from here
    
    N_Utility::Utility::waitForEnter();

    cout << "...\n"; 
    N_Utility::Utility::waitForEnter();
    
    if (target->isFainted())
      cout << target->name << " fainted!\n";
    else
      cout << target->name << " has " << target->health << " HP left.\n";
}
```







Now, let's move to the special moves.



Let's start with **Balbasaur Pokemon**.

It will have a special move named **VINE WHIP**

If this move is selected, 

then the Pokemon will definitely hit the opponent once.



After hitting once, there will be a possibility to hit once again.

The probability of hitting once again will be 50%.



And the damage of this move will be 25 units.



`attack` function of Balbasaur will look like.

```cpp
Bulbasaur::Bulbasaur()
    : Pokemon("Bulbasaur", PokemonType::GRASS, 110, {
        Move("VINE WHIP", 25),
        Move("TACKLE", 10)
}) {}

..........

void Bulbasaur::attack(Move selectedMove, Pokemon* target){
    Pokemon::attack(selectedMove, target);

    if(selectedMove.name == "VINE WHIP"){
        // Chance for a second hit (50% chance)
        int secondHitChance = rand() % 2;
        
        if (secondHitChance == 1){
            Pokemon::attack(selectedMove, target);
            std::cout << name << " hits again with a second " << selectedMove.name << "!\n";
        }
        else
            std::cout << target->name << " dodged the second hit!\n";
    }
}
```



> 💡**PROTIP:**
> Any number divided by 2 always gives the reminder as 0 or 1. Hence, the value of `secondHitChance` will either be 0 or 1!



Now, it's your job to implement special moves for all the Pokemon.

I will give the details of each special move for each Pokemon,

and you will implement them.



I will also provide the code at the end, 

so don't worry if you get stuck somewhere.





## Caterpie


---

Special Move - STICKY WEB

Damage - 10

Description - Reduce the damage power of the opponent by 5 units permanently





## Charmander


---

Special Move - BLAZING CHARGE

Damage - 70

Description - Charmander will itself have a recoil damage of 10 units





## Pidgey


---

Special Move - GUST

Damage - 15

Description - 20% probability that it blows away the enemy in the wind, ending the battle





## Pikachu


---

Special Move - THUNDER BOLT

Damage - 80

Description - 20% chances are there that the hit will get missed





## Squirtle


---

Special Move - RAPID SPIN

Damage - 5

Description - This will attack the opponent multiple times, anywhere from around 2-5 times





## Zubat


---

Special Move - LEECH LIFE

Damage - 10

Description - Will increase the health of Zubat by 60% of the damage dealt







# Codes


---



Caterpie```cpp
void Caterpie::attack(Move selectedMove, Pokemon* target){
    Pokemon::attack(selectedMove, target);
    
    if(selectedMove.name == "STICKY WEB")
    {
        // Reduce the target's next attack damage (for simplicity, reducing by a fixed value)
        int reducedDamage = 5;
        target->reduceAttackPower(reducedDamage);
        std::cout << target->name << "'s next attack will be reduced by " << reducedDamage << " damage!\n";
    }
}
```



Charmander```cpp
void Charmander::attack(Move selectedMove, Pokemon* target){
    Pokemon::attack(selectedMove, target);

    if(selectedMove.name == "BLAZING CHARGE")
    {
        // Recoil effect: Charmander takes recoil damage
        this->takeDamage(10); // Fixed recoil damage
        std::cout << name << " takes 10 recoil damage from the Blazing Charge!\n";
        N_Utility::Utility::waitForEnter();
    }
}
```



Pidgey```cpp
void Pidgey::attack(Move selectedMove, Pokemon* target){
    Pokemon::attack(selectedMove, target);

    if(selectedMove.name == "GUST")
    {
        // 20% chance to blow the opponent away
        if (rand() % 100 < 20)
        { 
            std::cout <<"... and blew the opponent away!\n";
            N_Battle::BattleManager::stopBattle();
            N_Utility::Utility::waitForEnter();
        }
    }
}
```



Pikachu```cpp
void Pikachu::attack(Move selectedMove, Pokemon* target){
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
            
}
```



Squirtle```cpp
void Squirtle::attack(Move selectedMove, Pokemon* target){
    Pokemon::attack(selectedMove, target);
    
    if(selectedMove.name == "RAPID SPIN")
    {
        // Random number of hits between 2 and 5
        int hits = (rand() % 4) + 2;

        // Split damage across hits
        for (int i = 0; i < hits; ++i) {
            Pokemon::attack(selectedMove, target);
        }
        
        std::cout << "... and hit " << hits << " times!\\n";
    }
}
```



Zubat```cpp
void Zubat::attack(Move selectedMove, Pokemon* target){
    // Call the base class method from child class.
    Pokemon::attack(selectedMove, target);

    if(selectedMove.name == "LEECH LIFE")
    {
        // Restore 50% of the damage dealt
        this->health += selectedMove.power * 0.5; 

        // Ensure health does not exceed maxHealth
        if (this->health > this->maxHealth)
            this->health = this->maxHealth;

        std::cout << "... and regained health!\n";
    }
}
```
