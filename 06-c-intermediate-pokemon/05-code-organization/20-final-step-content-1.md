You've come so far in building your Pokémon adventure.

And now it's time to **finish strong**. 



These last steps are **crucial**—they’re what will bring everything together and make your game **truly shine**.



**Let’s fix those last pieces of code** and take your game to the finish line! 💥 

You’re almost a true Pokémon Master, and the adventure awaits!





**Firstly**

-  Modify `choosePokemon()` function in `Player.cpp`.
- Go to switch statement implement in the `choosePokemon()` Function.
- Put PokemonType as the prefix of choice in close bracket like below code.

```cpp
switch((PokemonType) choice)
```

- Data type of choice is `int`. but we put PokemonType variable in different cases.
- So you have to typeCast choice from int to pokemonType.



> 💡**PRO TIP** :  Typecasting is used for change data type of a variable. will be discuss later in the further module.



and Final `Player.cpp `Code :



Player.cpp```cpp
// Player.cpp
#include "Player.hpp"
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include "iostream"

Player::Player() {
  name = "Trainer";
  chosenPokemon = Pokemon(); // Using the default Pokemon constructor
}

Player::Player(std::string p_name, Pokemon p_chosenPokemon) {
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
  std::cout << "Player " << name << " chose " << chosenPokemon.name << "!\n";
  Utility::waitForEnter(); // Wait for user to press Enter before proceeding
}
```



.Now second thing,



# Include` Pokemon.hpp` inside `Player.hpp`


---



Before we finalize your code.

It’s important to **include "Pokemon.hpp"** inside **"Player.hpp"**.Why? 



The `Player` class contains an instance of the `Pokemon` class (i.e., `chosenPokemon`). 

Since `Pokemon` is used directly as a member variable, **forward declaration** wouldn’t work here. 

Forward declarations only work when you're dealing with pointers or references to a class. 



But since You're using the full `Pokemon` object.

The **compiler needs to know the complete definition** of the `Pokemon` class, which requires including the header.



`Player.hpp` code after including `Pokemon.hpp` header file.



Player.hpp```cpp
#include <string>
#include "Pokemon.hpp"
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





# Remove `Pokemon.hpp` header file from main.cpp


---



Remove `Pokemon.hpp` from `main.cpp` because it is already included indirectly through `Player.hpp`. 

Since `Player.hpp` includes `Pokemon.hpp` for the `chosenPokemon` member.



There's no need to include it again in `main.cpp`. 

This avoids the redefinition of `pokemon.hpp` header file and keeps the code redundant free.



main.cpp```cpp
#include "Player.hpp"
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include <iostream>
#include <limits> // Include this header to use std::numeric_limits
#include <string>
using namespace std;

// ProfessorOak class definition
class ProfessorOak {
public:
  string name;

  // Parameterized constructor
  ProfessorOak(std::string p_name) { name = p_name; }

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
      std::cout << "That's not a valid choice. Try again!\n";
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



You’ve done it! 

You’ve successfully tackled all the errors in `main.cpp` and refined your code to run smoothly. 🏆
Your journey through debugging and refining your code has made you a better programmer. 🎓 



Keep up the great work, and remember, every error you solve is a step towards becoming a coding master.

**Celebrate your success!** You've earned it. 🥳
