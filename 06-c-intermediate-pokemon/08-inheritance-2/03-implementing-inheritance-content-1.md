In the previous lesson, 

you got to learn about **Inheritance** and its types. 



In this lesson, 

you will actually implement Inheritance in your code and use it!



You already have the theoretical knowledge, 

required to implement different Pokémon with unique moves using inheritance, 

as covered in the previous lesson.



Now, all you need to do is implement what you have learnt.



By the end of this lesson, 

you will have different `Pokemon` classes 

like `Zubat`, `Pikachu`, and `Caterpie` in your code, 

each inheriting the base class `Pokemon` ,

with their own unique behaviors or moves.



But to implement inheritance you need to know the syntax first.

Let's understand the syntax for inheritance through an example.



The current `Pokemon` class have properties and methods,

that is common to all the Pokemons.



 For reference, have a look in the `Pokemon` class given below:



Pokemon.cpp```cpp
#include "../../include/Pokemon/Pokemon.hpp"
#include "../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {

using namespace std;

  // Default constructor
  Pokemon::Pokemon() {
    name = "Unknown";
    type = PokemonType::NORMAL;
    health = 50;
    maxHealth = 50;
    attackPower = 10;
  }
  
  // Parameterized constructor
  Pokemon::Pokemon(string p_name, PokemonType p_type, int p_health,
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
    cout << name << " attacks " << target.name << " for " << attackPower
              << " damage!\n";
    target.takeDamage(attackPower);
  }
} // namespace N_Pokemon
```



The `Pokemon` class have the common functionalities, 

that different `Pokemon` like `Pikachu`, `Zubat`, `Caterpie`, and others can inherit from. 



Now, let's start creating `Pikachu` for your game,

and then you can create other different `Pokemon` by your own.



Create a file in the path `include/Pokemon/Pokemons/Pikachu.hpp`.

This will be the header file for your `Pikachu` class.

Name it `Pikachu.hpp`



Inside the header file, 

include the files `../Pokemon.hpp` and `#pragma once`



Include the namespace `N_Pokemon`.

Inside `N_Pokemon`, include another namespace `N_Pokemons`.



This are the name of the folders inside which you are creating your `Pikachu.hpp` file.



Create a `Pikachu` class,

which will inherit the `Pokemon` class,

like I have shown below.



```cpp
class Pikachu : public Pokemon { };
```



Inside the `Pikachu` class,

Declare public constructor and unique move method for `Pikachu`, `thunderShock()`.

`thunderShock()` will take a reference to a `Pokemon` and will return void.



```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
  
    class Pikachu : public Pokemon {
    public:
      Pikachu();
      void thunderShock(Pokemon &target);
    };
    
  }
}
```



You have created the header file for your `Pikachu` class,

now it's time to create the source file for the same.



Create another file in the path `src/Pokemon/Pokemons/Pikachu.cpp`,

and name it `Pikachu.cpp`.



Inside `Pikachu.cpp` include the files, `Pikachu.hpp`, `PokemonType.hpp` and `<iostream>`.



> 💡**PRO-TIP: **Always check the path of the files when you are including them. If you don't add the correct path, you might get errors later, while running your game.

> Here, the path of the files that you have added are like below:

> 

> `Pikachu.hpp` is `../../../include/Pokemon/Pokemons/Pikachu.hpp`

> `PokemonType.hpp` is `../../../include/Pokemon/PokemonType.hpp`



Define public methods,

that you have define in your `Pikachu.hpp`



Create a `Pokemon` in the constructor,

and name it `Pikachu`.

Its type will be `Electric` and `health` and `attackPower` will be 100 and 15.



Define the method `thunderShock()` as well.

You can take reference from the code snippet that I have given below:



Code Example: `Pikachu.cpp`

```cpp
#include "../../../include/Pokemon/Pokemons/Pikachu.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {
  namespace N_Pokemons {

    using namespace std;
    
    Pikachu::Pikachu() : Pokemon("Pikachu", PokemonType::ELECTRIC, 100, 20) {}
    
    void Pikachu::thunderShock(Pokemon &target) {
        cout << name << " uses Thunder Shock on " << target.name << "!\n";
        target.takeDamage(20);
    }
  }
}
```



Congratulations!

You have created Pikachu for your game.



Now it's time that you create other Pokemons in your game.

Start with Pidgey first:



> **TODO: Pidgey.hpp **
> ✅Create a separate header file for Pidgey in the path `include/Pokemon/Pokemons/Pidgey.hpp` and name it `Pidgey.hpp`
> ✅Include `../Pokemon.hpp` header file and pragma once in your pidgey.hpp
> ✅Create `Pidgy` class, which will inherit the `Pokemon` class 
> ✅Declare the constructor for `Pidgy` and a method `wingAttack()` that will take the reference to a `Pokemon` object and will return void



Example code: `Pidgey.hpp````cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
  
    class Pidgey : public Pokemon {
    public:
    Pidgey();
      void wingAttack(Pokemon &target);
    };
    
  }
}
```



> **TODO: Pidgey.cpp **
> ✅Create a separate source file for `Pidgey` in the path `src/Pokemon/Pokemons/Pidgey.cpp` and name it `Pidgey.cpp`
> ✅Include `../../../include/Pokemon/Pokemons/Pidgey.hpp`, `../../../include/Pokemon/PokemonType.hpp`header files and `<iostream>` in your `Pidgey.cpp`
> ✅Define the constructor for `Pidgey` class and create a `Pokemon` named `Pidgey` in the constructor of `Pokemon` class with `TYPE::NORMAL` , `health = 100` and `attackPower = 35`
> ✅Define the `wingAttack()` method that will print a statement `"name uses Wing Attack on target.name!"` and will call the method `takeDamage()` of the target `Pokemon` by passing 20 to it





Example code: `Pidgey.cpp````cpp
#include "../../../include/Pokemon/Pokemons/Pidgey.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {
  namespace N_Pokemons {
    using namespace std;
    
    Pidgey::Pidgey() : Pokemon("Pidgey", PokemonType::NORMAL, 100, 35) {}
    
    void Pidgey::wingAttack(Pokemon &target) {
      cout << name << " uses Wing Attack on " << target.name << "!\n";
      target.takeDamage(20);
    }
  }
}
```



Next, Make Caterpie.



> **TODO: Caterpie.hpp **
> ✅Create a separate header file for `Caterpie` in the path `include/Pokemon/Pokemons/Caterpie.hpp`and name it `Caterpie.hpp`
> ✅Include `../Pokemon.hpp` header file and pragma once in your `Caterpie.hpp`
> ✅Create `Caterpie` class which will inherit the `Pokemon` class 
> ✅Declare the constructor for `Caterpie` and a method `bugBite()` that will take the reference to a `Pokemon` object and will return void



Example code: `Caterpie.hpp````cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
    
    class Caterpie : public Pokemon {
    public:
      Caterpie();
      void bugBite(Pokemon &target);
    };

  }
}
```



> **TODO: Caterpie.cpp **
> ✅Create a separate source file for Caterpie in the path `src/Pokemon/Pokemons/Pidgey.cpp` and name it `Caterpie.cpp`
> ✅Include `../../../include/Pokemon/Pokemons/Caterpie.hpp`, `../../../include/Pokemon/PokemonType.hpp`header files and `<iostream>`in your `Caterpie.cpp`
> ✅Define the constructor for `Caterpie` class and create a `Pokemon` named `Caterpie` in the constructor of `Pokemon` class with `TYPE::BUG`, `health = 100` and `attackPower = 10`
> ✅Define the method `bugBite()` that will print a statement `"name uses Wing Attack on target.name!"` and will call the method `takeDamage()` of the target `Pokemon` by passing 20 to it





Example code: `Caterpie.cpp````cpp
#include "../../../include/Pokemon/Pokemons/Caterpie.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {

  namespace N_Pokemons {
    
    using namespace std;
    
    Caterpie::Caterpie() : Pokemon("Caterpie", PokemonType::BUG, 100, 10) {}
    
    void Caterpie::bugBite(Pokemon &target) {
      cout << name << " uses Bug Bite on " << target.name << "!\n";
      target.takeDamage(20);
    }
  }
}
```



Time for Zubat Pokemon.



> **TODO: Zubat.hpp **
> ✅Create a separate header file for Zubat in the path `include/Pokemon/Pokemons/Zubat.hpp` and name it `Zubat.hpp`
> ✅Include `../Pokemon.hpp` header file and pragma once in your `Zubat.hpp`
> ✅Create `Zubat` class which will inherit the `Pokemon` class 
> ✅Declare the constructor for `Zubat` and a method `supersonic()` that will take the reference to a `Pokemon` object and will return void





Example code: `Zubat.hpp````cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
  
    class Zubat : public Pokemon {
    public:
      Zubat();
      void supersonic(Pokemon &target);
    };
    
  }
}
```



> **TODO: Caterpie.cpp **
> ✅Create a separate source file for `Zubat` in the path `src/Pokemon/Pokemons/Zubat.cpp` and name it `Zubat.cpp`
> ✅Include `../../../include/Pokemon/Pokemons/Zubat.hpp`, `../../../include/Pokemon/PokemonType.hpp`header files and `<iostream>` in your `Zubat.cpp`
> ✅Define the constructor for `Zubat` class and create a `Pokemon` named `Zubat` in the constructor of `Pokemon` class with `TYPE::POISON`, `health = 100` and `attackPower = 20`
> ✅Define the method `supersonic()` that will print a statement `"name uses Wing Attack on target.name!`" and will call the method `takeDamage()` of the target `Pokemon` by passing 20 to it



Example code: `Zubat.cpp````cpp
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
