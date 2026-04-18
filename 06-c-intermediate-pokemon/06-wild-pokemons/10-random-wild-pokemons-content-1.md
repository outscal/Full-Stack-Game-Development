Professor Oak: "Now that we know how randomness works, 

                it’s time to bring some unpredictability to your Pokémon journey!"



When the player in your game goes for his journey to become a Pokémon trainer,

he will encounter random wild Pokémon,

while exploring different patches of grass. 



![Image result for gif of Ash going into the jungle with pikachu](//outscal.github.io/Full-Stack-Game-Development/images/fb3dcdac9fa820a8.gif)



This will make your game more interesting.



The goal of this lesson is to create this feature in your game.



What comes to your mind when I say, "player encountering wild pokemon"?

Wild pokemon? 

Which wild pokemon? 

Where will the wild pokemon be kept in the grass?



Yes, you need a class that will manage,

 which wild `Pokemon` the `Player` will encounter from the grass.



## Why a New Class?


---

You have learned in your earlier chapters,

that separating different functionalities in your code,

makes it more organized and easier to manage.



So, 

it's a good practice,

that you create a separate class that manages wild Pokemon encounters. 

This class will handle selecting a random Pokémon from the grass.



So, What's next?

Start creating a separate header file for this class!



> **TODO: WildEncounterManager.hpp**
> ✅ Create a header file and name it `WildEncounterManager.hpp`
> ✅ Include the header file `Grass.hpp`and the header file for vector in `WildEncounterManager.hpp`

> ✅ Create a public method `getRandomPokemonFromGrass()` inside `WildEncounterManager` class.

> ✅ `getRandomPokemonFromGrass()` will take a `Grass` object as parameter and returns a randomly selected `WildPokemon`.





Example `WildEncounterManager.hpp````cpp
#include <vector>
#include "Grass.hpp" // Assuming the Grass struct is defined here 

class WildEncounterManager { 
   public: 
   WildPokemon getRandomPokemonFromGrass(const Grass& grass
   ); 
};
```





> **TODO: WildEncounterManager.cpp**
> ✅ Create a source file and name it `WildEncounterManager.cpp`
> ✅ Include the header file `WildEncounterManager.hpp` , `<cstdlib>` for `rand()` and `<ctime>` for `time()` in `WildEncounterManager.cpp`

> ✅ Implement the constructor for `WildEncounterManager` class. The constructor will seed the random number generator with the current time

> ✅ In the method `getRandomPokemonFromGrass()` create an integer `randomIndex`

> ✅ The value of `RandomIndex` will be dividing the random number generated from the size of the vector `wildPokemonList` in `grass` struct.

> ✅ This method will return the `Pokemon` in index `randomIndex` of `wildPokemonList` vector



Example `WildEncounterManager.cpp````cpp
#include "WildEncounterManager.hpp"
#include <cstdlib> // For rand()
#include <ctime>   // For time()

WildEncounterManager::WildEncounterManager() {
    srand(time(0)); // Seed the random number generator
}

WildPokemon WildEncounterManager::getRandomPokemonFromGrass(const Grass& grass) {
    int randomIndex = rand() % grass.wildPokemonList.size();
    return grass.wildPokemonList[randomIndex];
}
```





## Integrating the Class into the Game


---



Now, the question is....

Where would you integrate the class into your game?

Where do you think you can?



Yes, the game class that handles the main game loop. 



> **TODO: Initializing forestGrass in Game constructor**
> ✅ Include `Grass.hpp` in `Game.hpp` file

> ✅ In `Game.hpp` file create a private member `forestGrass` of type `grass` struct
> ✅ In constructor of Game class `Game.cpp` initialize `forestGrass` with actual `Pokemon` object





Example `forestGrass in Game.cpp````cpp
Game::Game() { 
// Create a sample grass environment with actual Pokemon objects 
forestGrass = {"Forest", 
                        {Pokemon("Pidgey", PokemonType::NORMAL, 40), 
                        Pokemon("Caterpie", PokemonType::BUG, 35), 
                        Pokemon("Zubat", PokemonType::POISON, 30)}, 
                        70}; 
 }
```



Earlier inside the `gameloop` method, 

where you have written the switch statement for different actions in the game, 

remember writing `"You look around... but all the wild Pokémon are on vacation. Maybe try again later?"`,

for the `case: Battle wild pokemon`.



Now, 

the time has come to write the actual game logic in it, 

instead of giving a single line statement as output.





> **TODO: Case Battle Wild Pokemon**
> ✅ Include `WildEncounterManager.hpp` in `Game.cpp` file.

> ✅ In case 1: inside the switch statement create an object of class WildEncounterManager as `encounterManager`
> ✅ Create a pokemon object `encounteredPokemon`

> ✅ Call the method `getRandomPokemonFromGrass()` of `encounterManager` which will take forestGrass as parameter

> ✅ The value of `encounteredPokemon` will be the pokemon that is returned by the method `getRandomPokemonFromGrass()`

> ✅ Print a statement "A wild name_of_encountered_pokemon appeared!"





Example ** **`**Case Battle Wild Pokemon**````cpp
case 1: { 
// Create a scope within case 1 
 WildEncounterManager encounterManager; 
 Pokemon encounteredPokemon = encounterManager.getRandomPokemonFromGrass(forestGrass); 
 cout << "A wild " << encounteredPokemon.name << " appeared!\n"; 
 break; 
}
```





SEE here for the entire Game.hpp code```cpp
#include "Grass.hpp"

class Player;

class Game {
private:
  Grass forestGrass;
public:
  Game();
  void gameLoop(Player &player);
};
```





SEE here for the entire Game.cpp code```cpp
#include "Game.hpp"
#include "Player.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include "WildEncounterManager.hpp"
#include <iostream>
using namespace std;

Game::Game() {
  // Create a sample grass environment with actual Pokemon objects
  forestGrass = {"Forest",
                 {Pokemon("Pidgey", PokemonType::NORMAL, 40),
                  Pokemon("Caterpie", PokemonType::BUG, 35),
                  Pokemon("Zubat", PokemonType::POISON, 30)},
                 70};
}

void Game::gameLoop(Player &player) {

  int choice;
  bool keepPlaying = true;

  while (keepPlaying) {
    // Clear console before showing options
    Utility::clearConsole();

    // Display options to the player
    cout << "\nWhat would you like to do next, " << player.name << "?\n";
    cout << "1. Battle Wild Pokémon\n";
    cout << "2. Visit PokeCenter\n";
    cout << "3. Challenge Gyms\n";
    cout << "4. Enter Pokémon League\n";
    cout << "5. Quit\n";
    cout << "Enter your choice: ";
    cin >> choice;

    Utility::clearInputBuffer(); // Clear the input buffer

    // Process the player's choice and display the corresponding message
    switch (choice) {
    case 1: {
      // Create a scope within case 1
      WildEncounterManager encounterManager;
      Pokemon encounteredPokemon =
          encounterManager.getRandomPokemonFromGrass(forestGrass);
      cout << "A wild " << encounteredPokemon.name << " appeared!\n";
      break;
    }
    case 2: {
      cout << "You head to the PokeCenter, but Nurse Joy is out on a coffee "
              "break. Guess your Pokémon will have to tough it out for now!\n";
      break;
    }
    case 3: {
      cout << "You march up to the Gym, but it's closed for renovations. Seems "
              "like even Gym Leaders need a break!\n";
      break;
    }
    case 4: {
      cout << "You boldly step towards the Pokémon League... but the "
              "gatekeeper laughs and says, 'Maybe next time, champ!'\n";
      break;
    }
    case 5: {
      cout << "You try to quit, but Professor Oak's voice echoes: 'There's no "
              "quitting in Pokémon training!'\n";
      cout << "Are you sure you want to quit? (y/n): ";
      char quitChoice;
      cin >> quitChoice;
      if (quitChoice == 'y' || quitChoice == 'Y') {
        keepPlaying = false;
      }
      break;
    }
    default: {
      cout << "That's not a valid choice. Try again!\n";
      break;
    }
    }

    // Wait for Enter key before the screen is cleared and the menu is shown
    // again
    Utility::waitForEnter();
  }

  cout << "Goodbye, " << player.name << "! Thanks for playing!\n";
}
```
