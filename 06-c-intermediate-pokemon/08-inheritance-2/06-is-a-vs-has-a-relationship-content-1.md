From the very beginning of this module, 

your goal is to separate the functionalities of your code, 

make it maintainable and more scalable. 



And for that,

understanding the relationships between objects is critical,

because these relationships define, 

how objects (instances of classes) interact with each other,

and how responsibilities are divided among them.



In the real world, 

everything we interact with, 

from physical objects like cars and books,

to abstract concepts like orders and customers, 

can be modeled as objects in OOP. 



These objects interact with each other in ways. 

that mirror relationships found in the real world.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_20_2024__11_49_03.png)



In OOP, 

relationships between objects can be categorized into two types: 

- **IS-A (inheritance)**
- **HAS-A (association).**



In this lesson you will learn what IS-A and HAS-A relationships is,

and how are you going to apply them in your `Pokemon` game.



So, let's begin.



## IS-a relationship (inheritance)


---

When a subclass inherits properties and behaviors from a superclass,

the relationship between them is called **"is-a"** relationship. 



In the previous lessons, 

you have created so many different `Pokemon` classes,

like the `Pikachu`, `Zubat`, `Pidgey`.



All these classes are inheriting the common features from the `Pokemon` class,

like `health`, `attack power` and other methods.



Let's understand this more by looking into the code snippets of `Zubat` Pokemon once:



Example of Pokemon class:```cpp
#include "../../include/Pokemon/Pokemon.hpp"
#include "../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {

  // Default constructor
  Pokemon::Pokemon() {
    name = "Unknown";
    type = PokemonType::NORMAL;
    health = 50;
    maxHealth = 50;
    attackPower = 10;
  }
  
  // Parameterized constructor
  Pokemon::Pokemon(std::string p_name, PokemonType p_type, int p_health,
                   int p_attackPower) {
    name = p_name;
    type = p_type;
    maxHealth = p_health;
    health = p_health;
    attackPower = p_attackPower;
  }
  
  // Copy constructor
  Pokemon::Pokemon(const Pokemon &other) {
    name = other.name;
    type = other.type;
    health = other.health;
    maxHealth = other.maxHealth;
    attackPower = other.attackPower;
  }
  
  // Reduce HP by the damage amount
  void Pokemon::takeDamage(int damage) {
    health -= damage;
    if (health < 0) {
      health = 0;
    }
  }
  
  // Check if the Pokemon has fainted
  bool Pokemon::isFainted() const { return health <= 0; }
  
  // Restore health to full
  void Pokemon::heal() { health = maxHealth; }
  
  // Attack another Pokemon
  void Pokemon::attack(Pokemon &target) {
    std::cout << name << " attacks " << target.name << " for " << attackPower
              << " damage!\n";
    target.takeDamage(attackPower);
  }
} // namespace N_Pokemon
```



Example of Zubat class:```cpp
#include "../../../include/Pokemon/Pokemons/Zubat.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {
  namespace N_Pokemons {
  
    using namespace std;
    
    Zubat::Zubat() : Pokemon("Zubat", PokemonType::POISON, 100, 20) {}
    
    void Zubat::supersonic(Pokemon &target) {
      cout << name << " uses Supersonic on " << target.name << "!\n";
      target.takeDamage(20);
    }
  
  }
}
```



The code for `Pikachu`, `Pidgey` and others is similar.



`Zubat` is inheriting the properties of `Pokemon` class.

When you are calling the constructor of `Zubat` class, 

you have given its `Pokemon` a `name`, `Type`, `health` and attacking Powers.



But you haven't declared them anywhere in your `Zubat` class. 



It's because when `Zubat` inherited `Pokemon` class, 

all the Properties of `Pokemon` class became the Properties of `Zubat` class. 



It became a `Pokemon`.

What do you understand from this?



`Zubat` is a `Pokemon`.

`Pikachu` is a `Pokemon`.

`Pidgey` is a `Pokemon`.



But all `Pokemon` are not `Pikachu` or `Zubat` or `Pidgey`.



> Inheritance works similarly in OOP.

> It reduces duplication and promotes reuse, as common functionality can be defined in a base class and shared across subclasses.





## has-a relationship (Association)


---



When a class is composed of other classes, 

the relationship between them is known as **"has-a"(association) **relationship.



Did you understand?

No! (I Know)

Let me explain you in a simpler way.



In your Pokemon game, 

a `Player` has a team of `Pokemon` ,

but is the `Player` a `Pokemon`?

No, it is not!!

Because a `Player` has a `Pokemon`.



Even in the Pokemon TV series, 

Ash has Pikachu but Ash is not Pikachu. 

Association is similar in OOP.



Association is often preferred over inheritance,

because it allows for more flexible and modular code,

where different components can be updated independently.



*You can use associations in Places which involve items that ****someone or something own****. *



Like in the game Valorant, 

there are different characters like Jett, Phoenix, Ryna and others.



Now they all have different weapons, 

but they are not the weapons.

Jett has a Sheriff, Ryna has a Vandal and so on.



Let's understand the difference between IS-A and HAS-A relationship between Objects in OOP with the diagram below:



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_05_2024__19_23_45.png)





Key differences

Code Reusability:

IS-A Relationship (Inheritance)

Inheritance allows the child class (`Pikachu`),

to reuse code from the parent class (`Pokemon`). 



This means you don't have to write the same code again for each new type of Pokémon. 

Like `health()` and `attackPower()`.



HAS-A Relationship (Association)

Code reuse is achieved by associating one class with another. 

The **Player** does not inherit any of the behavior or properties of the **Pokemon**, 

but instead, "uses" Pokemon.





Class Design:

IS-A Relationship (Inheritance)

In an IS-A relationship, 

the derived class (child) is a specialized version of the base class (parent). 

This is useful when you have a hierarchy of related classes that share common behavior.



HAS-A Relationship (Association)

In a HAS-A relationship, 

the contained class (e.g., **Pokemon**) is treated as a separate entity, 

and you can add flexibility by changing the composition. 



For example, 

a **Player** could have multiple Pokémon or switch between them.







In the code, that you have written till now, 

can you think of Places where you have used the IS-A relationship between the different objects?



In the constructor for the Game class, 

you have created a list of `Pokemon`  which you have stored in the `forestGrass`.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_06_2024__12_22_40.png)



But have you noticed,

that instead of storing Object of` Pokemon` class,

`forestGrass` is storing object of `Pidgey`, `Caterpie` and `Zubat`?



And your compiler is not throwing a type mismatch error.

Why?



Because `Pidgey`, `Caterpie` and `Zubat` are inheriting from the `Pokemon` class, 

and hence `Pidgey` is-a `Pokemon` and so are the others. 

So, the compiler considers it of the same type.



We are talking about constructors and destructors, 

parent class and base class, 

but have you wondered, 

how the constructors and destructors of a child class and base class will be called during inheritance?



Don't worry in the next lessons this doubt will also be cleared!!
