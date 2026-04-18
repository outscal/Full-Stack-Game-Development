In the previous lesson you have understood the basic flow of a battle loop. 



If you have seen the actual pokemon TV series, then you know that

In the Pokémon world, battles are where the true bond between Trainer and Pokémon shines. 



![Image result for gif of Ash going into the jungle with pikachu](/Full-Stack-Game-Development/images/64bba59298731102.gif)



So, understanding the basics of these battles is key to becoming a great Trainer.



From the earlier chapters You know that to create battles in your game you need to implement some mechanisms. 

Those were health points (HP), damage calculation, and turn-based combat.



In this lesson you will learn how to implement these mechanisms. 



These mechanics form the backbone of any battle system and if you master them then it will be easier for you to code when you will be working on adding more complex features to your game in the upcoming lessons (Or when you will create battle system of any other game).



## Health Points (HP): The Life Force of Pokémon


---

Health is the life force of any Pokémon. In a battle, if a Pokémon's health degrades too much, it becomes unable to fight, allowing the other one to win.



So, health points are the measure of a Pokémon's vitality. 

And if this health point of a Pokémon reaches to zero then it faints, and the battle is over.



You can think of HP as a Pokémon's energy bar. The greater number of hits it takes, the more this bar depletes.



Now, let's Implement this health points in your game



> **TODO: Health Points**
> ✅ In `pokemon.hpp` , inside the Pokémon class include an attribute `health` of type integer 
> ✅ Add another attribute `maxHealth` of type integer

> ✅ Create a method `TakeDamage()` whose return type will be void and it will take a damage integer as argument. This method will reduce the health

> ✅ Create another method `isFainted()` which will return true if the health of a pokemon becomes zero or goes below




Example code:```cpp
class Pokemon {
public:
    string name;
    PokemonType type;
    int health; // Represents the current HP
    int maxHealth; // Represents the maximum HP

    Pokemon(); // Default constructor
    Pokemon(string p_name, PokemonType p_type, int p_health);

    void takeDamage(int damage); // Method to reduce HP
    bool isFainted() const; // Method to check if the Pokemon has fainted
};

```



## Implementing Damage


---



In the above code you have taken damage as an argument in the method `TakeDamage()`



What is damage? 



Basically, damage represents the amount of health that a pokemon losses when it is attacked.

For simplicity, we are keeping the value of damage fixed in the basic battle system.



Later on, when you will create more complex systems, you will be varying damage value with factors like attack power, defense and type of pokemon.



You have declared the methods in the pokemon class. Now let's define them in the source file 



> **TODO: **`**TakeDamge()**`** and **`**isFainted()**`
> ✅Inside the pokemon class in `pokemon.cpp` define the method `TakeDamage()` 
> ✅Reduce the health by damage amount

> ✅Write an if condition that if health < 0 than assign health = 0;

> ✅ Inside the method `isFainted()`  return if health <= 0 or not





Example code:```cpp
void Pokemon::takeDamage(int damage) {
    health -= damage; // Reduce HP by the damage amount
    if (health < 0) {
        health = 0; // Ensure HP doesn't go below 0
    }
}

bool Pokemon::isFainted() const {
    return health <= 0; // Return true if HP is 0 or less
}

```



## Turn-based combat


---

The battle that you are designing is a turn-based combat.



![Image result for gif of a battle starting between pokemon fighting with wild pokemon in forest](https://www.bing.com/th/id/OGC.43d73b453c1f7da9ca77e1cb0d522a5b?pid=1.7&rurl=https%3a%2f%2f31.media.tumblr.com%2fe37299562c3982038a68cbd8d50f77ae%2ftumblr_mr8wqscbwY1szx1oxo1_500.gif&ehk=3AXfSsTh3%2biVC6PQeR1tSc268178NMu0h7lWxLRmq1g%3d)



I have explained to you in the previous lesson what turn based combat is. 

The player’s Pokémon and the wild Pokémon take turns while attacking each other.



In each turn, one Pokémon will attack and the other will defend and they will continue doing this until one of the pokemon's health is 0 and it faints.



So, how will you implement the logic for attack?



In the Pokemon class you have created the method `attack()` 

This method simulates an attack on another Pokémon. It inflicts a fixed amount of damage to the target Pokémon.



You haven't written any logic as it was not explained to you that time.

Now the time has come that you write the logic for this method



> **TODO: **`**attack()**`
> ✅The attack method will take the reference of the pokemon that will be attacked. Name it target. 
> ✅Inside the attack method declare the damage variable of type int and assign value 10 to it

> ✅Print a statement {name<< " attacks " << target.name << " for " << damage << " damage!\\n";}

> ✅ The target will call the method `takeDamage()` and pass damage to it





Example code:```cpp
void Pokemon::attack(Pokemon &target) {
    int damage = 10; // Fixed damage for simplicity
    cout << name << " attacks " << target.name << " for " << damage << " damage!\\n";
    target.takeDamage(damage); // Apply damage to the target Pokémon
}

```



## Implementing a Simple Battle Simulation


---

You know how to implement the mechanics that you need for creating a battle in your game.



Now, don't you want to create a battle scenario where the player’s Pokémon battles a wild Pokémon. I know you do!!!



So, I will be teaching you to create a simple loop for a battle that continues until one Pokémon faints. 



![This Is Why Pokémon Bank Exists. Pokémon Black/White Still Seeing DLC ...](/Full-Stack-Game-Development/images/765e651a1c6fbaae.jpg)



**Note: **You can create a separate class `**BattleManager**` to manage the Battle!



You can have a method named battle which will take the reference to both the playerPokemon and wildPokemon and will return void.



We will have a while loop which will keep checking if any of the pokemon has fainted. 



Inside the while loop the PlayerPokemon will attack the wildPokemon first. 



Then we will check if the wildPokemon has fainted if it didn't then it will attack back the Player's Pokemon.



In the end after the while loop you can print the statement "playerPokemon.name has fainted! You lose the battle." If the Player's pokemon has fainted else you can print "You defeated the wild wildPokemon.name"



Example code: `BattleManager.cpp````cpp
void battle(Pokemon &playerPokemon, Pokemon &wildPokemon) {
    cout << "A wild " << wildPokemon.name << " appeared!\\n";

    while (!playerPokemon.isFainted() && !wildPokemon.isFainted()) {
        playerPokemon.attack(wildPokemon); // Player attacks first

        if (!wildPokemon.isFainted()) {
            wildPokemon.attack(playerPokemon); // Wild Pokémon attacks back
        }
    }

    if (playerPokemon.isFainted()) {
        cout << playerPokemon.name << " has fainted! You lose the battle.\\n";
    } else {
        cout << "You defeated the wild " << wildPokemon.name << "!\\n";
    }
}

```



![Image](/Full-Stack-Game-Development/images/1c531812e52c83ce.png)



Yes, Professor Oak we know that. 

We implemented this to make our fundamentals strong in battle loop and we know to make our game more exciting we need to add more advanced mechanics like different moves, type effectiveness, and strategies



We will add them when they are introduced in the upcoming lessons!!



Now try running your code. Were you able to play?

NO!! why?

Because you have just implemented the logics for the mechanics in the battle loop. You still need to integrate this basic battle logic into the actual game loop,

So that the player gets to engage in battles with wild Pokémon they encounter.



In the next lessons you are going to that. You will also learn how to track the state of the battle and handle the win/loss conditions.
