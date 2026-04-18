You are still left with one error from the last lesson.

`Player.cpp` file is not able to recognize the `Pokemon` class.



But why?



Because,

you have separated the `Player.cpp` from the `main.cpp`,

but you haven't explained what `Pokemon` class is, to `Player.cpp`,

and `Player.cpp` is still using the methods and data members of `Pokemon` class in it.



Like when you were creating different types of `Pokemon` using parameterized constructor in the switch statement.



Code:```cpp
void Player::choosePokemon(int choice) { 
switch ((PokemonChoice)choice) { 
    case PokemonChoice::CHARMANDER: 
        chosenPokemon = Pokemon("Charmander", PokemonType::FIRE, 100); 
        break; 
    case PokemonChoice::BULBASAUR: 
        chosenPokemon = Pokemon("Bulbasaur", PokemonType::GRASS, 100); 
        break; 
    case PokemonChoice::SQUIRTLE: 
        chosenPokemon = Pokemon("Squirtle", PokemonType::WATER, 100); 
        break; 
    
    default: 
        chosenPokemon = Pokemon("Pikachu", PokemonType::ELECTRIC, 100); 
        break; 
    } 

    cout << "Player " << name << " chose " << chosenPokemon.name << "!\n"; 
    Utility::waitForEnter(); // Wait for user to press Enter before proceeding 
}
```



How will the `Player` class know,

how to create a `Pokemon` using parameterized constructor?

If the definitions and declaration of the parameterized constructor is not present in `Player.cpp`.



`Player.cpp` do not know what `Pokemon` class is.



Because the `Pokemon` class is present in the `main.cpp` .



It's time that you separate your `Pokemon` class from the `main.cpp`,

and create its own header file and source file.



This will make the `Pokemon` class reusable in other parts of the project,

and solve the issues related to class recognition in other source files.

Like the one that we have encountered in `Player.cpp`.





> **TODO: **
> ✅ Create a new file named `Pokemon.hpp`.
> ✅ Include the declaration of the `Pokemon` class and its members in the `Pokemon.hpp` file





Example `Pokemon.hpp`:```cpp
#include <string>
#include "PokemonType.hpp"
using namespace std;

class Pokemon {
public:
    string name;
    PokemonType type;
    int health;

    // Default constructor
    Pokemon();

    // Parameterized constructor
    Pokemon(string p_name, PokemonType p_type, int p_health);

    // Copy constructor
    Pokemon(const Pokemon &other);

    // Destructor
    ~Pokemon();

    void attack();
};
```





> **TODO:**
> ✅Create a new file named `Pokemon.cpp`.
> ✅In the `Pokemon.cpp` file include the `Pokemon.hpp` header file and define all the methods present in the `Pokemon` class

> ✅use `::` operator to access all the data members and methods of the `Pokemon` class.





Example `Pokemon.cpp:````cpp

#include "Pokemon.hpp"
#include <iostream>
using namespace std;

// Default constructor
Pokemon::Pokemon() : name("Unknown"), type(PokemonType::NORMAL), health(50) {}

// Parameterized constructor
Pokemon::Pokemon(std::string p_name, PokemonType p_type, int p_health)
    : name(p_name), type(p_type), health(p_health) {}

// Copy constructor
Pokemon::Pokemon(const Pokemon &other)
    : name(other.name), type(other.type), health(other.health) {}

// Destructor
Pokemon::~Pokemon() {
    // Destructor logic (if any) goes here
}

void Pokemon::attack() {
    cout << name << " attacks with a powerful move!\n";
}
```



Since you have separated the `Pokémon` class from the `main.cpp`,

and created its own header and source file,

it's time to debug the error.



You are getting the error because `Player.cpp` is not able to recognize the `Pokemon` class. 



To remove the error,

you have to include the `pokemon.hpp` in the `Player.cpp` file,

So that it gets access to the methods of `Pokemon` class. 





> **TODO: **
> ✅In the `Player.hpp` file include the `Pokemon.hpp` file - write #include"Pokemon.hpp" in top of Player.hpp





Updated `Player.hpp:````cpp

#include <string>
#include "Pokemon.hpp"
using namespace std;

// Include the new Pokemon headerclass 
Player {
public:
    string name;
    Pokemon chosenPokemon;

    Player(); // Default constructor
    Player(string p_name, Pokemon p_chosenPokemon); // Parameterized constructor

    void choosePokemon(int choice); // Method to choose a Pokemon
};
```



Now that you have removed all the errors run the entire game. 



Is Your Pokemon game running as you expected? 

Verify that the `Player` class interacts correctly with the `Pokemon` class,

and that there are no errors related to the `Pokemon` class.



You are doing really Good!!





![Guess where? - Page 115 - World Discovery - Microsoft Flight Simulator ...](//outscal.github.io/Full-Stack-Game-Development/images/2cd79f8685812cd8.gif)






---



You must have experienced importance of separation of functionalities in code,

and how doing this can make your code more manageable and reusable. 

Let's revise it once again:



- Suppose you and your friend are working on the same game projects. 

            Creating different files for different classes will reduce conflicts that you might encounter,

            if all the classes were in the same file.



- You can easily reuse classes without needing to copy and paste your code in different places.



- Creating different files for different classes will make it easier to debug errors or update any class without affecting other parts of the code.






---





You have created separate files for `Player` and `Pokemon` classes.



Can you think of other classes that you might need to separate,

when your game becomes more complex?



Yes, Professor Oak class is still left to be separated into its own header and source files. 



So, later in this module you will move `ProfessorOak` class into its own header and source files. 

You already know how to do that so it will be a piece of cake for you. 



Just a reminder of how to separate classes into different files,



Create two files,

one header and one source.



Provide the declarations of the data members and methods in the header file.

and all the definitions in the source file. 



You will continue the process of cleaning up `main.cpp`,

and organizing your codebase into manageable components,

until you achieve your goal of completely refactoring the `main.cpp`.
