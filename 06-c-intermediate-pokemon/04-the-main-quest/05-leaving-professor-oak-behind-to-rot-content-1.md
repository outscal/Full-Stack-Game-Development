It's time to leave Professor Oak behind.

move on to your next adventure.



![Pokemon Champion](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_28_2024__09_28_35.png)







It’s time to bring your game to life. 

The key to making your game fun and interactive is a **game loop**. 

This loop will allow the player to make choices and keep the game moving.



# Setting Up the Basics


---



Before we jump into the loop, let’s start with the core structure. 

The game loop needs to keep running as long as the player is playing. 

This means we need a way to keep the loop going until the player exits the game and handle player input.



> **TODO:**
> ✅ Create a `gameLoop` Function and Pass Player Object as an Parameter just below of `ProfessorOak` Class.

> ✅ Return type of this Function should be  `void` .

> ✅ Make a `bool` variable `keepPlaying `and set as true inside gameLoop.

> ✅ create `while loop` inside `gameLoop` Function and set condition of loop is `keepPlaying`.



Click Here - Solution

```cpp
/*
   ProfessorOak class
*/

void gameLoop(Player &player) {
	 
	   bool keepPlaying = true;

		  while (keepPlaying) {
		      // this is gameLoop
		      // Run Untill Player Quit the Game and Make KeepPlaying false.
		  }

}

/*
   Main()  Function Code

*/


```



Now, the Pokémon world is open to explore.

It’s time to **decide what to do next**.

You are in control, and **each choice you make shapes your adventure**.



Do you want to **walk through the tall grass** and look for wild Pokémon?

Or maybe you’ll **challenge a Gym Leader**, fight hard, and win badges.



You could also **visit the PokeCenter** and heal your team after a tough battle.

If you're low on supplies, go to the **PokeMart** and get items for your next adventure.



Just like in the real Pokémon games, every choice will bring new challenges and rewards.

It’s not just about fighting—**you can explore towns**, **talk to people.**

And make choices that bring you closer to becoming the Pokémon Champion.



The world is yours to explore!

**What will you do next?**




---



Now, its time to make changes in code.

As you can Have different choice to explore in the game.



> **TODO:**
> ✅ Display Messages for choices to the player.

> ✅ Make a variable `choice` and take input of  `choice` from the player.

> ✅ Display a Message to player to enter choice.

> ✅ This all should be keep in game loop.





Choices for Players

What would you like to do next - [Player.name]

1.  Battle Wild Pokémon
2. Visit PokeCenter
3. Challenge Gyms
4. Enter Pokémon League
5. Quit



Click Here - Solution```cpp
// Function to handle the main game loop
void gameLoop(Player &player) {
  int choice;
  bool keepPlaying = true;

  while (keepPlaying) {
	    // Clear console before showing options  -> clear all previous mssg which was on the screen 
	    clearconsole();

	    // Display options to the player
	    cout << "\nWhat would you like to do next, " << player.name << "?\n";
	    cout << "1. Battle Wild Pokémon\n";
	    cout << "2. Visit PokeCenter\n";
	    cout << "3. Challenge Gyms\n";
	    cout << "4. Enter Pokémon League\n";
	    cout << "5. Quit\n";
	    cout << "Enter your choice: ";
	    cin >> choice;

  
   } 

}

```



you’ve created a variable `choice` to store the player’s input.

And a `bool keepPlaying` to control the loop.

The `while (keepPlaying)` part ensures that the game keeps running until the player decides to quit.



The game clears the screen with `clearconsole()` before displaying the player's choices.

You then prompt the player to enter their choice and store it in `choice`.



# Handling Player Choices


---



Now that you have a basic loop, let’s handle the player’s choices. 

Depending on what the player selects, the game will respond with a message (for now). 

You will implement each of these choices or features later in the course.



Now, can you think?

How will these choices be implemented in our game code?



Yes, you can use the switch case and display some funny messages.



Now, Its time to make changes in a code



> **TODO:**
> ✅ Implement  a Switch Case of all above choices in `while loop` of `gameLoop` Function.

> ✅ Print Funny Messages given below.[functionalities not implemented till now]



Funny Messages

**1. Battle Wild Pokémon**

```cpp
 "You look around... but all the wild Pokemon are on vacation. Maybe try again later?\\n";
```



**2. Visit PokeCenter**

```cpp
 "You head to the PokeCenter, but Nurse Joy is out on a coffee break. Guess your Pokemon will have to tough it out for now!\\n";
```



**3. Challenge Gyms**

```cpp
 "You march up to the Gym, but it's closed for renovations. Seems like even Gym Leaders need a break!\\n";
```



**4. Enter Pokemon League**

```cpp
 "You boldly step towards the Pokemon League... but the gatekeeper laughs and says, 'Maybe next time, champ!'\\n";
```



**5. Quit**

```cpp
 "You try to quit, but Professor Oak's voice echoes: 'There's no quitting in Pokemon training!'\\n";
```





Click Here - Solution```cpp
// Function to handle the main game loop
void gameLoop(Player &player) {
  int choice;
  bool keepPlaying = true;

  while (keepPlaying) {
    // Clear console before showing options
    clearconsole();

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


```



After quitting, the game thanks the player for playing and displays a friendly goodbye message.



You now have a fully functional **game loop** that lets players make choices, and it responds with funny messages.

While we haven’t implemented the full logic yet, you’ve laid the foundation for a smooth, interactive Pokémon game.



In the next lesson, you’ll start adding real game logic to handle battles, healing at the PokéCenter, and much more!

Get ready for your Pokémon adventure to evolve!



Code Till Now

```cpp
#include <iostream>
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
enum class PokemonChoice {
  CHARMANDER = 1,
  BULBASAUR,
  SQUIRTLE,
  PIKACHU // Default choice
};

// Define an enum for Pokemon types
enum class PokemonType {
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
    type = PokemonType::NORMAL;
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





**Great Job 🎉!**
