![Image](//outscal.github.io/Full-Stack-Game-Development/images/434c81845cc131de.png)



Oh, Professor Oak, for a professor you know too less. 

So, stop demotivating us,



We have just started a new topic, 

and it takes time to practice and become a good game developer. 



Also, we are near to our goal of refactoring `main.cpp` ,

as only the classes are left to be shifted to different files. 



So, congratulations on making it this far! 

and I promise you there's only a little bit more to go.



You already have all the knowledge related to header files and source files.



You have done so much to separate the functionalities of your code.

So, why don't you work a little more and create different files for different classes. 



Try with Player class first. 



> **TODO: **
> ✅ Create a file in your main directory and name it `Player.hpp`

> ✅ Include the `PokemonType.hpp`, `PokemonChoice.hpp` and `Utility.hpp` files in your `Player.hpp`

> ✅ Declare an empty class `Player` inside it

> ✅ Copy and paste the declarations of all the data members and methods of `Player` class in it.

> ✅ Comment out the `Player` class that you have in your `main.cpp` file.



Player.hpp```cpp
// Player.h
#include <string>
#include "PokemonType.hpp"
#include "PokemonChoice.hpp"
#include "Utility.hpp"
using namespace std;

class Player {
public:
    string name;
    Pokemon chosenPokemon;

    Player(); // Default constructor
    Player(string p_name, Pokemon p_chosenPokemon); // Parameterized constructor

    void choosePokemon(int choice); // Method to choose a Pokemon
};
```





After creating the `Player.hpp` file,

You might be getting some errors in your `main.cpp` file.



This is because the `main.cpp` file cannot recognize the`Player` class anymore.



But why is it happening?



It is because you have created the header file for the`Player` class,

But the `main.cpp` file doesn't know about this.



It doesn't know that there is a header file present in the directory,

that has the declarations for all the methods and data members of the `Player` class.



At this point `main.cpp` does not even know what Player class is.



So, for that you need to include `Player.hpp` in `main.cpp`.

Go on and include the `Player.hpp` file in your `main.cpp`file.



You have created a separate header file for your `Player` class and included it in the `main.cpp` file.

But where have you defined the methods and members of your `Player` class?



You need to create the source file `Player.cpp`for the `Player` class first.



So, let's do this.



> **TODO: Player Class**
> ✅ Create another file in your main directory and name it `Player.cpp`

> ✅ Include `Player.hpp` in `Player.cpp` file

> ✅ Cut and paste the functions from the `Player` class that you previously had in the main file.



Player.cpp```cpp
// Player.cpp
#include "Player.hpp"
#include "iostream"
using namespace std;

Player::Player() {
  name = "Trainer";
  chosenPokemon = Pokemon(); // Using the default Pokemon constructor
}

Player::Player(string p_name, Pokemon p_chosenPokemon) {
  name = p_name;
  chosenPokemon = p_chosenPokemon;
}

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



Now, since you have created separate files for your `Player` class,

and included them in your `main.cpp` as well, 

you might think that all the errors have gone.



But wait,

no, 

debugging has just begun!



You will see an error like the one below in your `Player.cpp` after implementing it

![Image](//outscal.github.io/Full-Stack-Game-Development/images/b17bcac92716688f.png)



You will also see this error in your `main.cpp` file

![Image](//outscal.github.io/Full-Stack-Game-Development/images/30a3d89ceb3d9091.png)



What does these errors mean?





![Image](//outscal.github.io/Full-Stack-Game-Development/images/2d89337be1e6e41f.png)





Yes, you are correct Professor Oak. 

But why? 



Why is `Player.cpp` is not able to recognize the `Pokemon` class?

And `main.cpp` is not able to recognize the `Player` class?



It's because `Pokemon` class is defined inside `main.cpp` ,

and you have shifted your `Player` class from `main.cpp` to a different file. 



Your `Player.cpp` is not able to get access to your `Pokemon` class,

that you have defined in your `main.cpp` file. 



Simply explaining in short,

- Your `main.cpp` knows about the `Pokemon` class
- But your `Player.cpp` does not



Similarly, if you take a look at your `main.cpp`, there is the following error as well:

![Image](//outscal.github.io/Full-Stack-Game-Development/images/30a3d89ceb3d9091.png)

<!-- image unavailable: image.png -->



This means that your `main.cpp` does not know about `Player` class!



So, how will you resolve all these errors?



Don't worry, 

In the next lesson you will resolve all these errors in your game, 

and you will be happy watch your game running!!
