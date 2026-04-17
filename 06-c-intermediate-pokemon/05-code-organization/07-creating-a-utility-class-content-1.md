In your Pokémon journey, you've already accomplished something important. 

You've taken the enums and moved them into their own header files. 

This simple step made your code more organized and easier to work with.



But if you take a closer look at your `main.cpp` file.

you'll notice it's still packed with many functions and lines of code. 

The file is doing too much, and it's getting a bit crowded.



**Let’s take a moment to think:** 

Are there other parts of the code that you can separate out? 

What about the functions that you find yourself using over and over again?



You've probably already guessed it—functions like `clearConsole()` and `waitForEnter()` are great candidates for separation. 

They’re used frequently and belong in a special place where they can be easily accessed and managed.



# Introduction to Utility Class


---



Imagine you have a toolbox filled with your favorite tools. 

Every time you need to fix something, you go to this toolbox. 

You know exactly where each tool is, and it makes your work much easier. 



A utility class is just like this toolbox. 

It's a place in your code where you can keep all the useful functions that you use often.

By grouping these functions together in one class, you make your code cleaner and your life easier.



Instead of having these functions scattered throughout your code,.

you'll have them neatly organized in one place.



## Benefits of utility class


---



Centralized Management

Imagine your utility class as a toolbox, holding all your essential tools.

Whenever you need to update or change a function, you know exactly where to find it.

As your game grows, this organized toolbox becomes even more valuable, keeping everything in one place.



Cleaner Code

A utility class helps keep our code clean by **organizing reusable functions** in one place, avoiding code duplication. 

This makes the code **easier to maintain** and ensures that common tasks are handled across different parts of the program.





# Creating the Utility Class


---



**Step 1: Creating **`**Utility.h**`

- Start by creating a new header file named `Utility.h`. 
- This is where you'll declare the utility class and its methods.



> TODO:
> ✅Create a new file in the same folder as your source file
> ✅Rename it as `Utility.hpp`
> ✅Write declaration of Utility  Function `clearConsole() `and `WaitForEnter() `in` Utility.hpp`
> ✅ Also Add One New Utility Function `clearInputBuffer() `declaration in `Utility.hpp`





Solution - Utility.hpp

```cpp
// Utility.h
class Utility {
public:
    static void clearConsole();
    static void waitForEnter();
    static void clearInputBuffer(); // New helper function
};
```



Now, You might be think.

What is this `clearInputBuffer()` Function?



Imagine you're eating popcorn.

But some kernels get stuck in your teeth. **Annoying, right**?

Just like that, when you enter input in a program.

Sometimes, extra characters get stuck in the input buffer, causing issues later.



> **💡PRO TIP : **

> The **input buffer** temporarily holds user input before it's processed by the program.

> Functions like `cin` retrieve data from this buffer.



The` clearInputBuffer() `function is like flossing for your code! 

It cleans out any leftover characters in the buffer so your next input is fresh and ready.



Why** static Keyword** Used for declaration of Function ?



The `static` keyword makes a function belong to the class itself, not to any object. 

You can call it using the class name`**Utility :: clearConsole()**` , without needing to create an instance.



> Note :  Don't Need to Worry. You will learn about static keyword more in the later chapter in this module.





**Step 2: Creating **`**Utility.cpp**`

- Next, create a source file named `Utility.cpp` 
- Where you'll define what these utility functions actually do.





> TODO:
> ✅Create a new file in the same folder as your source file
> ✅Rename it as `Utility.cpp`
> ✅Write definition of Utility  Function `clearConsole() `and `WaitForEnter() `in` Utility.hpp`
> ✅ Also Add definition of Function `clearInputBuffer() `in `Utility.cpp`

> ✅ Include `Utility.hpp `in `Utility.cpp` file.





Solution - Utility.cpp```cpp
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




---



Now, when you include `Utility.hpp` in your `main.cpp` file, you might see some errors. 

Don't worry, this is because the compiler doesn't yet know which class these functions belong to.





Here's how your `main.cpp` will look after these changes:

```cpp
#include "PokemonChoice.hpp"
#include "PokemonType.hpp"
#include "Utility.hpp"
#include <iostream>
#include <limits> // Include this header to use numeric_limits
#include <string>

// The rest of the code remains the same, with all utility function calls now using Utility:: prefix
```



**To fix this : **

> **💡PRO TIP** :  Use the **scope resolution operator** (`::`).



For example, instead of just calling `clearConsole()`, you'll call `Utility::clearConsole()`.



> TODO :

> ✅Fix each error in your `main.cpp` and use `Utility::` to fix them.





This is How the Main.cpp look like

```cpp
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



By moving your frequently used functions into a utility class.

you've taken another big step in keeping your code clean and organized. 



Now, your `main.cpp` is less cluttered.

And your utility functions are all in one place.

Ready to be reused whenever you need them.



Code until here

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







**Great job🎉!**
