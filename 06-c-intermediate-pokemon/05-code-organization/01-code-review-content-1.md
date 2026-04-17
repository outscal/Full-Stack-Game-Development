> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your current branch called → ***Feature_4_Code_Organization***

> Let’s start working on the new feature now!




I hope you have seen and understood the whole code till the previous lesson.

Let me explain the code a little bit.



## **clear Console**


---

It does nothing but clears the console (terminal).

Would you like to see hundreds of lines in front of you while playing the game? Obviously not.

That's where it helps, making it easy for the players to read game conversations.





## Wait for enter


---

Keep yourself in place of the player.

Will you like it if many messages appear on the screen at once, and you need to read all of them?

I guess the answer is NO.



Messages should appear like a conversation.

And, players should get enough time to read them up.

So, this function will pause further messages until the player presses the 'enter' key.





## Enum


---


There can be only a limited type of Pokemon.

And a player can choose Pokemon from a given set only.

So, to enhance the readability of the code and avoid errors,

you have used enums.





## Classes


---

If there can be many instances of an entity, you should always make a class for it.

If an entity has many properties, then also, you should create a class to bind all the properties together.

These things will keep the code neat and easy to understand.



In your code, you have made classes for Pokemon, Player, and ProfessorOak.

Because there can be many Pokemon in the game,

and you wanted to bind all related variables and methods of Player and Professor.





## Game loop


---



This is a crucial function for any game.

As the name suggests, you can have an idea of it.



Loop means, it keeps repeating itself throughout the game.

This function updates all the variables inside the game at every frame.





## Main function


---



This is the starting point of the game.

This function calls other things in the code sequentially.



You can relate it to your house's main door.

You can not reach to your bedroom directly.

Unless you jump in from the window like me 😂



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_14_2024__06_12_19.png)





So, do you think everything in the code is perfect?

You have divided every functionality into functions.

You have made separate classes.

Will that be all?





# The real problem


---

Before jumping to the problem, below is the whole code till now.



Code until now```cpp
#include <iostream>
#include <limits> // Include this header to use numeric_limits
#include <string>
using namespace std;

// Function to clear the console
void clearConsole() {
// Platform-specific clear console command
#ifdef _WIN32
  system("cls");
#else
  (void)system("clear");
#endif
}

// Function to wait for user to press Enter
void waitForEnter() {
  cin.get(); // Wait for Enter key
}

// Define an enum for Pokemon choices
enum PokemonChoice {
  CHARMANDER = 1,
  BULBASAUR,
  SQUIRTLE,
  PIKACHU // Default choice
};

// Define an enum for Pokemon types
enum PokemonType {
  FIRE,
  GRASS,
  WATER,
  ELECTRIC,
  NORMAL // Added for the default constructor
};

// Pokemon class definition
class Pokemon {
public:
  string name;
  PokemonType type;
  int health;

  // Default constructor
  Pokemon() {
    name = "Unknown";
    type = NORMAL;
    health = 50;
  }

  // Parameterized constructor
  Pokemon(std::string p_name, PokemonType p_type, int p_health) {
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

  void attack() { std::cout << name << " attacks with a powerful move!\n"; }
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
  Player(std::string p_name, Pokemon p_chosenPokemon) {
    name = p_name;
    chosenPokemon = p_chosenPokemon;
  }

  void choosePokemon(int choice) {
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
    waitForEnter(); // Wait for user to press Enter before proceeding
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
    waitForEnter();
    cout << name
              << ": My name is Oak. People call me the Pokemon Professor!\n";
    waitForEnter();
    cout << name << ": But enough about me. Let's talk about you!\n";
    waitForEnter();
  }

  void offerPokemonChoices(Player &player) {
    cout
        << name
        << ": First, tell me, what’s your name? \t [Please Enter Your Name]\n";
    getline(std::cin, player.name);
    cout << name << ": Ah, " << player.name
              << "! What a fantastic name!\n";
    waitForEnter();
    cout << name
              << ": You must be eager to start your adventure. But first, "
                 "you’ll need a Pokemon of your own!\n";
    waitForEnter();

    // Presenting Pokemon choices
    cout
        << name
        << ": I have three Pokemon here with me. They’re all quite feisty!\n";
    waitForEnter();
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
    waitForEnter();
  }

  // New method for the main quest conversation
  void explainMainQuest(Player &player) {
    // Clear the console
    clearConsole();

    cout << "Professor Oak: " << player.name
              << "!, I am about to explain you about your upcoming grand "
                 "adventure.\n";
    waitForEnter();
    cout << "Professor Oak: You see, becoming a Pokémon Master is no easy "
                 "feat. It takes courage, wisdom, and a bit of luck!\n";
    waitForEnter();
    cout
        << "Professor Oak: Your mission, should you choose to accept it—and "
           "trust me, you really don’t have a choice—is to collect all the "
           "Pokémon Badges and conquer the Pokémon League.\n";
    waitForEnter();

    cout << "\n"
              << player.name
              << ": Wait... that sounds a lot like every other Pokémon game "
                 "out there...\n";
    waitForEnter();
    cout << "Professor Oak: Shhh! Don't break the fourth wall, "
              << player.name << "! This is serious business!\n";
    waitForEnter();

    cout << "\nProfessor Oak: To achieve this, you’ll need to battle wild "
                 "Pokémon, challenge gym leaders, and of course, keep your "
                 "Pokémon healthy at the PokeCenter.\n";
    waitForEnter();
    cout << "Professor Oak: Along the way, you'll capture new Pokémon to "
                 "strengthen your team. Just remember—there’s a limit to how "
                 "many Pokémon you can carry, so choose wisely!\n";
    waitForEnter();

    cout << "\n"
              << player.name << ": Sounds like a walk in the park... right?\n";
    waitForEnter();
    cout << "Professor Oak: Hah! That’s what they all say! But beware, "
                 "young Trainer, the path to victory is fraught with "
                 "challenges. And if you lose a battle... well, let’s just say "
                 "you'll be starting from square one.\n";
    waitForEnter();

    cout << "\nProfessor Oak: So, what do you say? Are you ready to "
                 "become the next Pokémon Champion?\n";
    waitForEnter();
    cout << "\n" << player.name << ": Ready as I’ll ever be, Professor!\n";
    waitForEnter();

    cout
        << "\nProfessor Oak: That’s the spirit! Now, your journey begins...\n";
    waitForEnter();
    cout << "Professor Oak: But first... let's just pretend I didn't "
                 "forget to set up the actual game loop... Ahem, onwards!\n";
    waitForEnter();
  }
};

// Function to handle the main game loop
void gameLoop(Player &player) {
  int choice;
  bool keepPlaying = true;

  while (keepPlaying) {
    // Clear console before showing options
    clearConsole();

    // Display options to the player
    cout << "\nWhat would you like to do next, " << player.name << "?\n";
    cout << "1. Battle Wild Pokémon\n";
    cout << "2. Visit PokeCenter\n";
    cout << "3. Challenge Gyms\n";
    cout << "4. Enter Pokémon League\n";
    cout << "5. Quit\n";
    cout << "Enter your choice: ";
    cin >> choice;

    // Clear the newline character left in the buffer after cin >> choice
    cin.ignore(numeric_limits<streamsize>::max(), '\n');


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
    waitForEnter();
  }

  cout << "Goodbye, " << player.name << "! Thanks for playing!\n";
}

int main() {
  // Create Pokemon and Player objects for the game
  Pokemon charmander("Charmander", FIRE,
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





Now, let me give you a few tasks

- Go to the `main()` function first
- Now find `choosePokemon()` function
- Find `cin.ignore()`



HAHA! What happened?

Are you having a headache?



So, the main problem with this code is all the components are in a single file.

You have to scroll a lot to find a single function.



Now just think,

How would you feel if you had to debug an issue in such a large file?





## Future scope


---

In the future, there can be many updation that you would like to do.

But would you be able to do so in this kind of code?



What if you wanted to add more Pokémon?

What if you wanted to implement more features, like battles with other trainers, a shop to buy items, or more complex AI for gym leaders?

What if multiple people were working on the same codebase?



The code will become much more larger.

And even more challenging to handle.

You can not even think of multiple people working on code like this.





## challenges


---



Would it be easy to find where each feature is implemented?

Would it be easy to update or change parts of the code?

of course NOT!!!





# Solution


---

You have understood the problem,

and you know the reason behind it.



So, can you think of a solution?

I think you have got it.



Yes, guys, dividing the code into multiple folders and files can solve your problem.

Each file should be dedicated for a single functionality.



You will implement this solution in the upcoming lessons.

HOLD ON TIGHT ⚡
