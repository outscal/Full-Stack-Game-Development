You are feeling exhausted by fixing errors in the code. 

Congratulations! You’ve made it through a tricky part of coding. 

Great job sticking with it and solving the issue. 🎉



Now the only error that remains in your main file is: **”redefinition of PokemonChoice”.**



![redefinitionofpokemon](//outscal.github.io/Full-Stack-Game-Development/images/3c9205befda968a3.png)



This simply means that the header file **PokemonType** is getting included twice.



> 💡**PRO TIP:**
> To see how this issue can affect your code.

> Try including a header file multiple times in different places and observe how the error appears.





So, During Your Implementation Journey.

You Indirectly Include **"PokemonChoice.hpp"** and **"PokemonType.hpp"**  and **"Utility.hpp"** twice.



Look at this Flow Diagram - ಠ_ಠ.



![img](//outscal.github.io/Full-Stack-Game-Development/images/099bfd3630d5d463.png)





First You Included** **`**PokemonChoice.hpp**`** **in** **`**main.cpp.**`**   ------->** First Definition in main file about Pokemon.hpp.

Now , You again Included `**Player.hpp**` in Main File  ----> Redefinition of `**PokemonChoice.hpp**` through `**Player.hpp**`

Because You also Included `**PokemonChoice.hpp**` in `**Player.hpp**`** **as well.



> **TODO:**
> ✅Analyse your code for `PokemonType.hpp` & `Utility.hpp` Re-definition issue. 
> ✅Think How can we Resolve it.





To Resolve this Error.

Shift the `PokemonCoice.hpp` , `PokemonType.hpp` &  `Utility.hpp` includes from` Player.hpp` to `Player.cpp`.

`Player.cpp` not included in `main.cpp `directly.

So, this solves the issue of Redefinition.



![img](//outscal.github.io/Full-Stack-Game-Development/images/500d5924815ded00.png)




---



Now, it's time to make changes in a code.

This is the `player.hpp` header file code Till Now, We have.



Code - Player.hpp```cpp
// Player.h
#include <string>
#include "PokemonType.hpp"      // shift to player.cpp
#include "PokemonChoice.hpp"  // shift to player.cpp
#include "Utility.hpp"      // shift this to player.cpp
using namespace std;    
class Player {
public:
    string name;
    Pokemon chosenPokemon;

    Player(); // Default constructor
    Player(std::string p_name, Pokemon p_chosenPokemon); // Parameterized constructor

    void choosePokemon(int choice); // Method to choose a Pokemon
};
```



Shift the `#include` header files of `PokemonType.cpp`, `PokemonChoice.cpp` and `Utility.hpp` in Player.cpp file.

After shifting these  three header files in `Player.cpp`.



The Final Code of `Player.hpp` and `Player.cpp` :



Code - Player.hpp```cpp
#include <string>
using namespace std;  
  
class Player {
public:
    string name;
    Pokemon chosenPokemon;

    Player(); // Default constructor
    Player(std::string p_name, Pokemon p_chosenPokemon); // Parameterized constructor

    void choosePokemon(int choice); // Method to choose a Pokemon
};
```



Code - Player.cpp```cpp
#include "Player.hpp"
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include <iostream>
using namespace std;
// Player class definition
  

  // Default constructor
 Player :: Player() {
    name = "Trainer";
    chosenPokemon = Pokemon(); // Using the default Pokemon constructor
  }

  // Parameterized constructor
  Player :: Player(string p_name, Pokemon p_chosenPokemon) {
    name = p_name;
    chosenPokemon = p_chosenPokemon;
  }

  void Player :: choosePokemon(int choice) {
    switch (choice) {
    case CHARMANDER:
      chosenPokemon = Pokemon("Charmander", FIRE, 100);
      break;
    case BULBASAUR:
      chosenPokemon = Pokemon("Bulbasaur", GRASS, 100);
      break;
    case SQUIRTLE:
      chosenPokemon = Pokemon("Squirtle", WATER, 100);
      break;
    default:
      chosenPokemon = Pokemon("Pikachu", ELECTRIC, 100);
      break;
    }
    cout << "Player " << name << " chose " << chosenPokemon.name << "!\n";
    Utility::waitForEnter(); // Wait for user to press Enter before proceeding
  }
```



Now , You can check your Main.cpp File, the Redefinition issue has been gone. wow !



Congratulations! 🎉 You’ve successfully tackled all the errors in `main.cpp`. 

Your code is now clean and error-free, thanks to your careful management of header file inclusions.



Now, check Your `Player.cpp` File.

What you Noticed ?

![img](//outscal.github.io/Full-Stack-Game-Development/images/66059a7371d5be76.jpg)



`Player.cpp` still is not able to recognize the Pokemon class 😂.

But this will get resolved in the next section when You create separate files for Pokemon class as well.



Code Till Here

PokemonType.hpp```cpp
// Define an enum for Pokemon types
enum class PokemonType {
  FIRE,
  GRASS,
  WATER,
  ELECTRIC,
  NORMAL // Added for the default constructor
};
```



PokemonChoice.hpp```cpp
// Define an enum for Pokemon choices
enum class PokemonChoice {
  CHARMANDER = 1,
  BULBASAUR,
  SQUIRTLE,
  PIKACHU // Default choice
};
```



Utility.hpp```cpp
// Utility.h
class Utility {
public:
    static void clearConsole();
    static void waitForEnter();
    static void clearInputBuffer(); // New helper function
};
```



Utility.cpp```cpp
// Utility.cpp
#include "Utility.hpp"
#include <iostream>
#include <limits>
using namespace std;

void Utility :: clearConsole() {
#ifdef _WIN32
    system("cls");
#else
    system("clear");
#endif
}

void Utility :: waitForEnter() {
    cin.get();
}

void Utility :: clearInputBuffer() {
    cin.ignore(numeric_limits<streamsize>::max(), '\n');
}
```



Player.hpp```cpp
#include <string>
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



Player.cpp```cpp
#include "Player.hpp"
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include <iostream>
using namespace std;
// Player class definition
  

  // Default constructor
 Player :: Player() {
    name = "Trainer";
    chosenPokemon = Pokemon(); // Using the default Pokemon constructor
  }

  // Parameterized constructor
  Player :: Player(string p_name, Pokemon p_chosenPokemon) {
    name = p_name;
    chosenPokemon = p_chosenPokemon;
  }

  void Player :: choosePokemon(int choice) {
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



main.cpp```cpp
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include <iostream>
#include <limits> // Include this header to use numeric_limits
#include <string>
using namespace std;

// Pokemon class definition
class Pokemon {
public:
   string name;
  PokemonType type;
  int health;

  // Default constructor
  Pokemon() {
    name = "Unknown";
    type = PokemonType::NORMAL;
    health = 50;
  }

  // Parameterized constructor
  Pokemon(string p_name, PokemonType p_type, int p_health) {
    name = p_name;
    type = p_type;
    health = p_health;
  }

  // Copy constructor
  Pokemon(const Pokemon &other) {
    name = other.name;
    type = other.type;
    health = other.health;
  }

  // Destructor
  ~Pokemon() {
    // Destructor message removed
  }

  void attack() { cout << name << " attacks with a powerful move!\n"; }
};

// Player class definition
class Player {
public:
 string name;
  Pokemon chosenPokemon;

  // Default constructor
  Player() {
    name = "Trainer";
    chosenPokemon = Pokemon(); // Using the default Pokemon constructor
  }

  // Parameterized constructor
  Player(string p_name, Pokemon p_chosenPokemon) {
    name = p_name;
    chosenPokemon = p_chosenPokemon;
  }

  void choosePokemon(int choice) {
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
};

// ProfessorOak class definition
class ProfessorOak {
public:
  string name;

  // Parameterized constructor
  ProfessorOak(string p_name) { name = p_name; }

  void greetPlayer(Player &player) {
    cout << name << ": Hello there! Welcome to the world of Pokemon!\n";
    Utility::waitForEnter();
    cout << name
              << ": My name is Oak. People call me the Pokemon Professor!\n";
    Utility::waitForEnter();
    cout << name << ": But enough about me. Let's talk about you!\n";
    Utility::waitForEnter();
  }

  void offerPokemonChoices(Player &player) {
    cout
        << name
        << ": First, tell me, what’s your name? \t [Please Enter Your Name]\n";
    getline(cin, player.name);
    cout << name << ": Ah, " << player.name
              << "! What a fantastic name!\n";
    Utility::waitForEnter();
    cout << name
              << ": You must be eager to start your adventure. But first, "
                 "you’ll need a Pokemon of your own!\n";
    Utility::waitForEnter();

    // Presenting Pokemon choices
    cout
        << name
        << ": I have three Pokemon here with me. They’re all quite feisty!\n";
    Utility::waitForEnter();
    cout << name << ": Choose wisely...\n";
    cout << "1. Charmander - The fire type. A real hothead!\n";
    cout << "2. Bulbasaur - The grass type. Calm and collected!\n";
    cout << "3. Squirtle - The water type. Cool as a cucumber!\n";

    int choice;
    cout
        << name
        << ": So, which one will it be? Enter the number of your choice: ";
    cin >> choice;

    player.choosePokemon(choice);
    Utility::waitForEnter();
  }

  // New method for the main quest conversation
  void explainMainQuest(Player &player) {
    // Clear the console
    Utility::clearConsole();

  cout << "Professor Oak: " << player.name
              << "!, I am about to explain you about your upcoming grand "
                 "adventure.\n";
    Utility::waitForEnter();
    cout << "Professor Oak: You see, becoming a Pokémon Master is no easy "
                 "feat. It takes courage, wisdom, and a bit of luck!\n";
    Utility::waitForEnter();
    cout
        << "Professor Oak: Your mission, should you choose to accept it—and "
           "trust me, you really don’t have a choice—is to collect all the "
           "Pokémon Badges and conquer the Pokémon League.\n";
    Utility::waitForEnter();

  cout << "\n"
              << player.name
              << ": Wait... that sounds a lot like every other Pokémon game "
                 "out there...\n";
    Utility::waitForEnter();
   cout << "Professor Oak: Shhh! Don't break the fourth wall, "
              << player.name << "! This is serious business!\n";
    Utility::waitForEnter();

    cout << "\nProfessor Oak: To achieve this, you’ll need to battle wild "
                 "Pokémon, challenge gym leaders, and of course, keep your "
                 "Pokémon healthy at the PokeCenter.\n";
    Utility::waitForEnter();
    cout << "Professor Oak: Along the way, you'll capture new Pokémon to "
                 "strengthen your team. Just remember—there’s a limit to how "
                 "many Pokémon you can carry, so choose wisely!\n";
    Utility::waitForEnter();

   cout << "\n"
              << player.name << ": Sounds like a walk in the park... right?\n";
    Utility::waitForEnter();
    cout << "Professor Oak: Hah! That’s what they all say! But beware, "
                 "young Trainer, the path to victory is fraught with "
                 "challenges. And if you lose a battle... well, let’s just say "
                 "you'll be starting from square one.\n";
    Utility::waitForEnter();

    cout << "\nProfessor Oak: So, what do you say? Are you ready to "
                 "become the next Pokémon Champion?\n";
    Utility::waitForEnter();
    cout << "\n" << player.name << ": Ready as I’ll ever be, Professor!\n";
    Utility::waitForEnter();

    cout
        << "\nProfessor Oak: That’s the spirit! Now, your journey begins...\n";
    Utility::waitForEnter();
    cout << "Professor Oak: But first... let's just pretend I didn't "
                 "forget to set up the actual game loop... Ahem, onwards!\n";
    Utility::waitForEnter();
  }
};

// Function to handle the main game loop
void gameLoop(Player &player) {
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
    case 1:
      cout << "You look around... but all the wild Pokémon are on "
                   "vacation. Maybe try again later?\n";
      break;
    case 2:
      cout
          << "You head to the PokeCenter, but Nurse Joy is out on a coffee "
             "break. Guess your Pokémon will have to tough it out for now!\n";
      break;
    case 3:
      cout << "You march up to the Gym, but it's closed for renovations. "
                   "Seems like even Gym Leaders need a break!\n";
      break;
    case 4:
      cout << "You boldly step towards the Pokémon League... but the "
                   "gatekeeper laughs and says, 'Maybe next time, champ!'\n";
      break;
    case 5:
      cout << "You try to quit, but Professor Oak's voice echoes: "
                   "'There's no quitting in Pokémon training!'\n";
      cout << "Are you sure you want to quit? (y/n): ";
      char quitChoice;
      cin >> quitChoice;
      if (quitChoice == 'y' || quitChoice == 'Y') {
        keepPlaying = false;
      }
      break;
    default:
      cout << "That's not a valid choice. Try again!\n";
      break;
    }

    // Wait for Enter key before the screen is cleared and the menu is shown
    // again
    Utility::waitForEnter();
  }

  cout << "Goodbye, " << player.name << "! Thanks for playing!\n";
}

int main() {
  // Create Pokemon and Player objects for the game
  Pokemon charmander("Charmander", PokemonType::FIRE,
                     100); // Using parameterized constructor

  // Continue with the main flow of the game
  ProfessorOak professor("Professor Oak");
  Player player("Ash", charmander);

  // Greet the player and offer Pokemon choices
  professor.greetPlayer(player);
  professor.offerPokemonChoices(player);

  // Explain the main quest
  professor.explainMainQuest(player);

  // Start the main game loop
  gameLoop(player);

  return 0;
}
```





**Great Job🎉!**
