Currently, all the different types of Pokemon,

that are present in your code have just one special move.



Are you satisfied with this only?

Don't you want to implement multiple moves for each Pokemon?



How would you feel,

if the Charmander could **Bug Bite** the opponent?

Or if he could give a **Thunder Shock**?



Not only the Charmander, 

but also the other Pokemon in your game.



What if they all have multiple moves to use in the battle?

Wouldn't that be crazy? Isn't it?



And what if I tell you that, 

all the Pokemon will not only have each other moves,

but you can also implement your custom-defined moves in the game.



That means whatever move you can imagine,

will be in your game. 🥳🥳



So, let's move forward to the coding part to implement the above-discussed functionality.

Excited? 😎





# Coding Time


---

First, you need to design a structure,

that binds all the data related to **moves** together.



For a particular **move**, you require mainly two things

- Move Name
- Move Power



So, create a struct in `move.hpp` file to handle moves.



Move.hpp```cpp
#pragma once
#include <string>
using namespace std;

namespace N_Pokemon{
    struct Move{
        string name;
        int power;

        Move(const string& moveName, int movePower){
            name = moveName;
            power = movePower;
        }
    };
}
```



Forward Declare the `Move` struct in `Pokemon.hpp` file.



Under `Pokemon` class,

declare a vector `moves` that will consist of,

all the types of moves a Pokemon can perform.



Also, you will need a function `selectAndUseMove()` to use a move,

that function will also be declared under `Pokemon.hpp`.





Pokemon.hpp```cpp
#pragma once
#include <string>
#include <vector>
using namespace std;

namespace N_Pokemon {

    struct Move;
    enum class PokemonType;

    class Pokemon {
        int health; 
        int maxHealth; 
        int attackPower;
        vector<Move> moves; // Store the list of moves

        Pokemon(); 
        Pokemon(string p_name, PokemonType p_type, int p_health, int p_attackPower);

        void heal();
        virtual void attack(Pokemon* target);
        void takeDamage(int damage);

    protected:
        // Base implementation for selecting and using a move
        void selectAndUseMove(Pokemon* target);
        
    };
}
```





Since in this lesson, 

you have declared the functions in the header files,

in the next lesson, you will define all these functions and,

will make all the Pokemon, move.
