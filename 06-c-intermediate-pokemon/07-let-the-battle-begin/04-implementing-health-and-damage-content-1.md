As you continue your journey to build your Pokémon game,

Let’s take a moment to reflect on what you've learned so far. 

In the last material, you learned the concepts of Health Points (HP) and damage. 



These are the backbone of any battle system. 

Now, it’s time to dig deeper and refine these ideas. 



You’ll focus on managing health and damage better, making your game feel more realistic and engaging.

From this lesson, your Pokémon will be ready to carry their battle scars and victories with them.

Making each encounter more meaningful.



# Implementing Health Management in the Game Context


---



In the world of Pokémon, a battle doesn’t just reset when it’s over. 

If your Pokémon takes damage in one battle, that damage stays with them. 

They don’t just magically heal when the battle ends. 



This persistent health system is a key feature that adds depth to the game. 

It means that every hit your Pokémon takes matters, and you'll need to think strategically about when to fight and when to rest.



![img](//outscal.github.io/Full-Stack-Game-Development/images/9a822ef8bba2c2f1.png)







To implement this in your game.

You’ll need to update  your `Pokemon` class. 



You want your Pokémon’s health to carry over from one battle to the next.

But you also need a way to heal them, just like how Trainers visit a PokéCenter in the Pokémon games.



Here’s how you can do that. 

You’ll add a new method called `heal()`  that restores the Pokémon’s health to its maximum value. 

This way, when your Pokémon is hurt, you can bring it back to full strength when you visit the PokéCenter.



Imagine your Pokémon took a heavy hit in a tough battle. 

You head to the PokéCenter, and after some much-needed rest.

your Pokémon is fully healed, ready to take on the next challenge. 



This simple addition makes your game world more alive and gives your decisions more weight.



> **TODO: **
> ✅ Introduce the `heal()` method in the `Pokemon.hpp` header file.
> ✅ Implement the `heal()` method in the `Pokemon.cpp` class
> ✅ Set `health` is equal to `maxHealth.`



Pokemon.hpp - Click Here

```cpp

class Pokemon {
public:
    string name;
    PokemonType type;
    int health; // Current HP
    int maxHealth; // Max HP

    Pokemon(std::string p_name, PokemonType p_type, int p_maxHealth)
        : name(p_name), type(p_type), maxHealth(p_maxHealth), health(p_maxHealth) {}

    void takeDamage(int damage);
    bool isFainted() const;
    void heal(); // Method to restore HP to max
};





```



Pokemon.cpp - Click Here```cpp
void Pokemon::heal() {
    health = maxHealth; // Restore health to full
}
```





With this code, your Pokémon’s health is now persistent, and they can be healed when needed. 

This small change adds a new layer of strategy to your game. 

Do you risk another battle with a weakened Pokémon, or do you play it safe and head to the PokéCenter?





# Damage Calculation


---



Now that you’ve refined how health works. let’s take a closer look at damage. 

In the previous material, you kept things simple by making every attack do the same amount of damage. 



But in a real Pokémon battle, different Pokémon have different strengths. 

Some Pokémon hit harder than others, and you want to reflect that in our game.



To do this, you’ll introduce a new attribute called `attackPower`. 

This will allow us to vary the amount of damage each Pokémon can deal. 



A Pokémon with higher `attackPower` will do more damage, making them a tougher opponent in battle.

Imagine your Pokémon has a powerful move that can deal a significant blow to its opponent. 

This move is represented by a higher `attackPower`. 



Now, when your Pokémon attacks.

It can do more damage, making each hit feel more impactful 

and adding excitement to the battle.



> **TODO: **
> ✅ Add the `attackPower` attribute to the `Pokemon` class.
> ✅ Implement the `attack()` method using `attackPower` for damage calculation



Solution - Click Here

`Pokemon.h`

```cpp

class Pokemon {
public:
    int attackPower; // New attribute for attack power

    Pokemon(std::string p_name, PokemonType p_type, int p_maxHealth, int p_attackPower);
        
    void attack(Pokemon &target);
};
```



`Pokemon.cpp`

```cpp
 Pokemon(std::string p_name, PokemonType p_type, int p_maxHealth, int p_attackPower)
        : name(p_name), type(p_type), maxHealth(p_maxHealth), health(p_maxHealth), attackPower(p_attackPower) {}
 
 void Pokemon::attack(Pokemon &target) {
        int damage = attackPower; // Use attack power for damage calculation
        std::cout << name << " attacks " << target.name << " for " << damage << " damage!\n";
        target.takeDamage(damage);
    }
```





With this new attribute, battles become more varied and exciting. 

Each Pokémon brings its own strengths into the fight, making each encounter unique. 

This is just the beginning of creating a battle system that feels dynamic and engaging.





# Integrating Health and Damage into the Game Loop


---



Now that you’ve improved health and damage, it’s time to see how they work in the game. 

The game loop is where everything happens. 



After each battle, your Pokémon’s health should reflect the damage it took. 

If it’s hurt, you might want to visit the PokéCenter to heal it before the next battle.



Let’s update the game loop to include this healing process. 

When your Pokémon is hurt, you can go to the PokéCenter to heal it. 

This adds a new level of strategy to the game. 



You’ll need to think about when to keep fighting and when to take a break to heal.



**Example Code :**

```cpp
	void Game::gameLoop(Player &player) {
	    ...
	    case 2: {
	        cout << "You head to the PokeCenter.\\n";
	        player.chosenPokemon.heal(); // Heal the player's Pokémon
	        cout << player.chosenPokemon.name << "'s health is fully restored!\\n";
	        break;
	    }
	    ...
	}
```



With this update, your game feels more complete. 

Now, you have to manage your Pokémon’s health carefully, which makes the game more engaging.



and the Expected output when you go to the PokeCenter will be :

```plaintext
player pokemon's health is fully stored.
```



You’ve made big improvements to your game’s battle system. 

By making health and damage work better, your game now feels more real and fun. 

Your Pokémon will now keep their health after battles, making each fight more important.



Next, you’ll put it all together by coding the full battle loop. 

This is where your Pokémon will fight wild Pokémon in real-time. 

It’s a big step toward creating a fully working battle system.



**Get ready**—your Pokémon battles are about to come to life!
