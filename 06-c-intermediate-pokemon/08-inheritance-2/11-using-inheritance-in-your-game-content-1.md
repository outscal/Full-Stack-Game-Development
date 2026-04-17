You have created four different child Pokemon classes till now, 

Pikachu, Pidgey, Caterpie and Zubat



Did you forget about Charmander, Squirtle and Bulbasaur?

You need to create them in your game as well.

So, let's start this chapter by creating them first.



Start with Charmander.



> **TODO: Charmander.hpp **
> ✅Create a separate header file for Charmander in the path `include/Pokemon/Pokemons/Caterpie.hpp` and name it `Charmander.hpp`
> ✅Include `../Pokemon.hpp` header file and pragma once in your `Charmander.hpp`
> ✅Create `Charmander` class, which will inherit the `Pokemon` class 
> ✅Declare the constructor for `Charmander` and a method `flameBurst()` that will take the reference to a `Pokemon` object and will return void





**Charmander.hpp **```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
    
    class Charmander : public Pokemon {
    private:
    void flameThrower(Pokemon &target);
    
    public:
      Charmander();
      
    };
    
  }
}
```



> **TODO: Charmander.cpp **
> ✅Create a separate source file for `Charmander`  in the path `src/Pokemon/Pokemons/Charmander.cpp` and name it `Charmander.cpp`
> ✅Include `../../../include/Pokemon/Pokemons/Charmander.hpp`, `../../../include/Pokemon/PokemonType.hpp`header files and `<iostream>` in your `Charmander.cpp`
> ✅Define the constructor for `Charmander` class and create a `Pokemon` named `Charmander` in the constructor of `Pokemon` class with `TYPE::FIRE` , `health = 100` and `attackPower = 35`
> ✅Define the `flameBurst()` method that will print a statement `"Charmender uses Flame Thrower on target.name!"` and will call the method `takeDamage()` of the target `Pokemon` by passing 20 to it





**Charmander.cpp **```cpp
#include "../../../include/Pokemon/Pokemons/Charmander.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {
  namespace N_Pokemons {
    using namespace std;
    
    Charmander::Charmander() : Pokemon("Charmander", PokemonType::FIRE, 100, 35) {}
    
    void Charmander::flameThrower(Pokemon &target) {
      cout << name << " uses Flame Thrower on " << target.name << "!\n";
      target.takeDamage(20);
    }
  }
}
```





Next, let's make Squirtle.



> **TODO: Squirtle.hpp **
> ✅Create a separate header file for `Squirtle` in the path `include/Pokemon/Pokemons/Squirtle.hpp`and name it `Squirtle.hpp`
> ✅Include `../Pokemon.hpp` header file and `pragma once` in your `Squirtle.hpp`
> ✅Create `Squirtle` class which will inherit the `Pokemon` class 
> ✅Declare the constructor for `Squirtle` and a method `WaterSplash()` that will take the reference to a `Pokemon` object and will return void





**Squirtle.hpp **```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
    
    class Squirtle : public Pokemon {
    private:
    void waterSplash(Pokemon &target);
    
    public:
      Squirtle();
      
    };
    
  }
}
```



> **TODO: Squirtle.cpp **
> ✅Create a separate source file for `Squirtle` in the path `src/Pokemon/Pokemons/Squirtle.cpp` and name it `Squirtle.cpp`
> ✅Include `../../../include/Pokemon/Pokemons/Squirtle.hpp`, `../../../include/Pokemon/PokemonType.hpp`header files and `<iostream>` in your `Squirtle.cpp`
> ✅Define the constructor for `Squirtle` class and create a `Pokemon` named `Squirtle` in the constructor of `Pokemon` class with `TYPE::WATER` , `health = 100` and `attackPower = 35`
> ✅Define the `waterSplash()` method that will print a statement `"Squirtle uses Water splash on target.name!"` and will call the method `takeDamage()` of the target `Pokemon` by passing 20 to it





Squirtle.cpp```cpp
#include "../../../include/Pokemon/Pokemons/Squirtle.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {
  namespace N_Pokemons {
    using namespace std;
    
    Squirtle::Squirtle() : Pokemon("Charmander", PokemonType::FIRE, 100, 35) {}
    
    void Squirtle::waterSpalsh(Pokemon &target) {
      cout << name << " uses Water splash on " << target.name << "!\n";
      target.takeDamage(20);
    }
  }
}
```





Now, it's time for Balbasaur.



> **TODO: Balbasaur.hpp **
> ✅Create a separate header file for `Balbasaur` in the path `inlcude/Pokemon/Pokemons/Balbasaur.hpp` and name it `Balbasaur.hpp`
> ✅Include `../Pokemon.hpp` header file and `pragma once` in your `Balbasaur.hpp`
> ✅Create `Balbasaur` class which will inherit the `Pokemon` class 
> ✅Declare the constructor for `Balbasaur` and a method `vineWhip()` that will take the reference to a `Pokemon` object and will return void





Bulbasaur.hpp```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
    
    class Balbasaur : public Pokemon {
    private:
    void vineWhip(Pokemon &target);
    
    public:
      Balbasaur();
      
    };
    
  }
}
```



> **TODO: Balbasaur.cpp **
> ✅Create a separate source file for `Balbasaur` int the path `src/Pokemon/Pokemons/Balbasaur.cpp` and name it,`Balbasaur.cpp`
> ✅Include `../../../include/Pokemon/Pokemons/Balbasaur.hpp`, `../../../include/Pokemon/PokemonType.hpp`header files and `<iostream>` in your `Balbasaur.cpp`
> ✅Define the constructor for `Balbasaur` class and create a `Pokemon` named `Balbasaur` in the constructor of `Pokemon` class with `TYPE::GRASS` , `health = 100` and `attackPower = 35`
> ✅Define the `vineWhip()` method that will print a statement `"Balbasaur uses vine whip on target.name!"` and will call the method `takeDamage()` of the target `Pokemon` by passing 20 to it





Bulbasaur.cpp```cpp
#include "../../../include/Pokemon/Pokemons/Balbasaur.hpp"
#include "../../../include/Pokemon/PokemonType.hpp"
#include <iostream>

namespace N_Pokemon {
  namespace N_Pokemons {
    using namespace std;
    
    Balbasaur::Balbasaur() : Pokemon("Charmander", PokemonType::FIRE, 100, 35) {}
    
    void Balbasaur::vineWhip(Pokemon &target) {
      cout << name << " uses vine Whip on " << target.name << "!\n";
      target.takeDamage(20);
    }
  }
}
```



Now that you have created so many Pokemon in your game,

How is the game now?

You must be using different moves and strategies in your Pokemon battles?

No?

But why?



Because they are still not being used in your game,

and it's the same old boring gameplay. 



The `battle()` method of the `BattleManager` class,

is not using different attack methods, 

that you have created in the child classes 

e.g., `Pikachu`, `Zubat`, etc.



It is only using the common `attack()` method inside it.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_06_2024__09_22_25.png)



So, instead of calling the common `attack()` method,

you should call different attack methods, 

that you have create till now, right?



Let's do this. 

Instead of calling  `playerPokemon.attack()`  inside the `battle()` function,

use `playerPokemon.thundershock()`.



Did you get an error saying no member named 'thunderShock' in Pokemon?



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_06_2024__09_27_52.png)



What does this error mean? 

Why are you getting this error?



The error is because the compiler does not know that `thundershock()` belongs to the `Pikachu` class,

when it is calling the `thundershock()` method for the `playerPokemon`.



This is because you can store an Object of `Pikachu` in a `Pokemon`  type pointer (Pikachu Is-A Pokemon),

but you cannot access the unique methods in Pikachu class from a pointer of type `Pokemon`.



Isn't that unfair?



Let's understand this through a simple example:

Consider a game where we have a base class Vehicle, 

and child classes like Car, Bike, and Plane. 



Each vehicle has a general `move()` method, 

but specific vehicles have unique methods (e.g., Car has drift() and Plane has fly()).



Let's create a simple class hierarchy with a base class Vehicle and child classes Car, Bike, and Plane in [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp)



> **TODO:**
> ✅Create a class Vehicle with a public method `move()`whose return type is void.

> ✅Print the statement "The vehicle is moving." inside the `move()` method.

> ✅Create a child class Car that is inheriting the vehicle class and have a public method `drift()`that is printing a statement "The car is drifting!"

> ✅Create a child class Bike that is inheriting the vehicle class and have a public method `wheelie()`that is printing a statement "The bike is doing wheelie!"

> ✅Create a child class Plane that is inheriting the vehicle class and have a public method `fly()`that is printing a statement "The Plane is flying!"




Example code:```cpp
// Base class Vehicle
class Vehicle {
public:
    void move() {
        std::cout << "The vehicle is moving.\n";
    }
};

// Child class Car
class Car : public Vehicle {
public:
    void drift() {
        std::cout << "The car is drifting!\n";
    }
};

// Child class Bike
class Bike : public Vehicle {
public:
    void wheelie() {
        std::cout << "The bike is doing a wheelie!\n";
    }
};

// Child class Plane
class Plane : public Vehicle {
public:
    void fly() {
        std::cout << "The plane is flying!\n";
    }
};
```



You can store child class objects (like Car, Bike, and Plane) in a Vehicle variable because they all share the IS-A relationship (Car is a Vehicle).

Let's do it!



> **TODO:**
> ✅In the main function create three pointers of type Vehicle - vehicle1, vehicle2, vehicle3 each pointing to a car, bike and a plane

> ✅Call the method move of vehicle using each of the vehicle 1,2 and 3

> ✅Delete all the pointers



Example code:```cpp
int main() {
    Vehicle* vehicle1 = new Car();    // Car object stored as Vehicle
    Vehicle* vehicle2 = new Bike();   // Bike object stored as Vehicle
    Vehicle* vehicle3 = new Plane();  // Plane object stored as Vehicle

    vehicle1->move();  // Output: The vehicle is moving.
    vehicle2->move();  // Output: The vehicle is moving.
    vehicle3->move();  // Output: The vehicle is moving.

    delete vehicle1;
    delete vehicle2;
    delete vehicle3;

    return 0;
}
```



What is the output?



Output:```cpp
The vehicle is moving.
The vehicle is moving.
The vehicle is moving.
```



Now instead of calling the method `move()` of `Vechicle` class,

call the unique methods like `drift()` or `fly()` from the vehicle1, vehicle2, or vehicle3 variables.



Example code:```cpp
int main() {
    Vehicle* vehicle1 = new Car();
    vehicle1->drift();  // Error: 'class Vehicle' has no member named 'drift'

    delete vehicle1;
    return 0;
}
```



You will get an error: `'class Vehicle' has no member named 'drift'`

Why did the error occur?



Even though `vehicle1` is holding a `Car` object, 

its type is still `Vehicle`.



The compiler only knows about the methods available in the `Vehicle` class,

 so, it won’t allow access to `Car`'s unique methods like `drift()`.



**IS-A Relationship:** A `Car` **is a** `Vehicle`, but a `Vehicle` doesn’t know how to `drift()`—only the `Car` class knows that.



Now that you understood why the error occurred, 

let's go again where we were.




---



You got the same error above, 

when you were trying to access `thundershock()` method from `playerPokemon`.



The `playerPokemon` is of type `Pokemon`

So, the compiler only recognizes methods in the `Pokemon` class, 

and not the unique methods in child classes like `thunderShock()` for Pikachu.



```cpp
Pikachu pikachu;
Pokemon playerPokemon = pikachu;
playerPokemon->thunderShock();  // Error: 'class Pokemon' has no member named 'thunderShock'
```



We have only discussed the Problem till now!!



But what is the solution? 

Can we fix this problem? 

Yes, using Polymorphism.



Polymorphism is the solution to this problem, and you will study about it in the later chapter of this module.
