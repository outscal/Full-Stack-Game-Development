After refactoring the Pokemon class, some issues still remain in your code.

Don't get scared of these minor problems, I know you're strong and brave.



So, the issue arising in your code is about multiple definitions of files.

What does that mean?



Okay, I'll tell you step by step.

Look at the map below to understand it more clearly.



![  ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/12_24_2024__12_46_37.png)





`Pokemon.hpp` is including `PokemonType.hpp` in it.

And `Player.hpp` is including `Pokemon.hpp` in it.



Now, after all of this.

`main.cpp` includes `Player.hpp`, `Pokemon.hpp` and `PokemonType.hpp` individually.



That means `main.cpp` is having 3 instances of `PokemonType.hpp` file,

1 directly and 2 in directly.



Similarly, it is having 2 instances of `Pokemon.hpp`



The same problem occurs with `Player.cpp` as well in your code.

Source files only require 1 instance of the header files.



So, how would you deal with this issue?

What do you think,

from which point does the problem get started?



I guess the link between header files creates this problem.

What if you remove those links?

I mean to say, just stop including header files into one another.



But if you do so,

how will `Pokemon.hpp` be able to use `PokemonType.hpp` in it?



Think for some time about this.





# Solution


---

So till now, you have learnt that you can include a file in some other file,

and then you can use all of its variables and functions there.



There is another way to do it.

In the world of programming, it is known as ***forward declaration***.



Before getting into the details about the forward declaration,

I think you should first understand its usecase.



What does it exactly do?



Suppose there are 2 classes, A and B, in different files.

The programmer wants to declare a variable of type B in the class A.



So, one way to do this is to include B's file into A's file.



But, inside the A class, the programmer just wants to declare a single variable of B's class,

and does not want to use any of it's functions.



So, is it feasible to bring the whole file of B just for only one variable?

I don't think so.



To tackle this problem, forward declaration is used.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_14_2024__10_57_55.png)





# What is Forward Declaration


---

Before moving to forward declaration,

let's understand normal declaration.



What is a declaration?

You have understood this in previous lessons,

but still, let me remind you.



Announcing that,

some variable or function exists, is known as **declaration**.



Normal declaration means, declaring at any place,

without a purpose.





But, in the **forward declaration**,

you need to be concerned about the place of declaration.



For example,

if you declare at line 5,

then, you will be able to use that declaration only after the 5th line.

You can't use it at any line before that.

```cpp
/*
functionName is not accessible here
..
*/
int functionName (int variable);

// After the declaration, you can use functionName anywhere in this file
```





In simple words, you can understand forward declaration as,

informing the compiler that some particular class exists,

and let the programmer use that class to create variables without including it.



Let's come back to your code.



To ***forward declare*** `PokemonType.hpp` in `Pokemon.hpp`,

you first need to remove the include statement,

and add the below code in `Pokemon.hpp`

```cpp
#include <string>
using namespace std;

enum class PokemonType;
.........
```



Try to implement forward declaration similarly in `Player.hpp` for `Pokemon.hpp`



> **NOTE:** `Pokemon.hpp` was using enum of `PokemonType.hpp`, but `Playler.hpp` is using class of `Pokemon.hpp`, so class will be forward declared and not enum





Once you are done with forward declaring header files instead of including them,

save and refresh your code.



Now, you won't be getting redefinition errors.



> **NOTE:** Below final code is just for your understanding, it is not meant to be run properly. It still having some minor errors which you will resolve in the upcoming lessons





Code until here

main.cpp```cpp
#include "Player.hpp"
#include "Pokemon.hpp"
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include <iostream>
#include <limits> // Include this header to use numeric_limits
#include <string>
using namespace std;

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



Player.cpp```cpp
// Player.cpp
#include "Player.hpp"
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
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



Player.hpp```cpp
// Player.hpp
#include <string>
using namespace std;

class Pokemon;

class Player {
public:
    string name;
    Pokemon chosenPokemon;

    Player(); // Default constructor
    Player(string p_name, Pokemon p_chosenPokemon); // Parameterized constructor

    void choosePokemon(int choice); // Method to choose a Pokemon
};
```



Pokemon.cpp```cpp
#include "Pokemon.hpp"
#include <iostream>
#include "PokemonType.hpp"
using namespace std;

// Default constructor
Pokemon::Pokemon() {
  name = "Unknown";
  type = PokemonType::NORMAL;
  health = 50;
}

// Parameterized constructor
Pokemon::Pokemon(string p_name, PokemonType p_type, int p_health) {
  name = p_name;
  type = p_type;
  health = p_health;
}

// Copy constructor
Pokemon::Pokemon(const Pokemon &other) {
  name = other.name;
  type = other.type;
  health = other.health;
}

// Destructor
Pokemon::~Pokemon() {
  // Destructor logic (if any) goes here
}

void Pokemon::attack() {
  cout << name << " attacks with a powerful move!\n";
}
```



Pokemon.hpp```cpp
#include <string>
using namespace std;

enum class PokemonType;

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



PokemonChoice.hpp```cpp
// Define an enum for Pokemon choices
enum class PokemonChoice {
  CHARMANDER = 1,
  BULBASAUR,
  SQUIRTLE,
  PIKACHU // Default choice
};
```



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



Utility.cpp```cpp
// Utility.cpp
#include "Utility.hpp"
#include <iostream>
#include <limits>
using namespace std;

void Utility::clearConsole() {
#ifdef _WIN32
  system("cls");
#else
  system("clear");
#endif
}

void Utility::waitForEnter() { cin.get(); }

void Utility::clearInputBuffer() {
  cin.ignore(numeric_limits<streamsize>::max(), '\n');
}
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
