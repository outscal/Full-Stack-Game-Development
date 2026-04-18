In the previous content, you might have noticed that some messages were getting skipped. 

Imagine you're the player—would you enjoy it if many messages appeared on the screen all at once.

and you had to read them all quickly?



I think the answer is NO.

Messages should come up like a real conversation.

Giving the player enough time to read each one.



![c++](https://images-ext-1.discordapp.net/external/86fnV5Opd5SzP6QyLWbfg5vM-mklZE95cruzdfoLST4/https/media.tenor.com/N8Wp9CHroz4AAAPo/game-interface-video-game.gif)

![c++](/Full-Stack-Game-Development/images/a853d6c8f470a226.gif)



To Fix this, You should change your code such that after each dialog there is a pause in the game.

That way, each dialog and each sentence will be shown one by one rather than all at once!

But how will your code know when to display the next line of dialog?



One solution is to make it time dependent. 

That is, after `x` seconds, the next line of dialog is displayed on the screen.

This goes on until all the dialogs are finished.



But there is a problem with this approach. 

Everyone's reading speed is different, some of your players might require more time to read a dialog.

So wouldn't it be a good idea to give your players control over when to display the next dialog?!



You can update your code in such a way that when players press `**Enter**` then only the next dialog is displayed.

How can you pause the execution of code until you received input from the player.


---





Lets understand this with an example.

Try to print 4-5 cout statement  in c++ compiler. [[click here](https://outscal.com/online-compilers/cpp)]



> Note : Create any other Folder in VsCode or any other IDE , in which you are writing code. and Implement this code.



You can use these statements to print```plaintext
1.  Hello , I am Professor Oak.
2. I want to take rest.
3. I have to Enjoy this winter.
4. I want to eat Pizza.
```



Now, print these statement in a console.

What you noticed ?

All these statements printed once , as discussed already.





Example Code```cpp
#include <iostream>
 using namespace std;
 int main() {
     cout << "Hello , I am Professor Oak." << endl;

     cout << "I want to take rest." << endl;

     cout << "I have to Enjoy this winter." << endl;

     cout << "I want to eat Pizza." << endl;

  return 0;
}

```



Now, Put `cin.get()` function between First and second cout statement.

and again run this code.



What did you notice? 

After printing first cout statement, code stop its execution.

Now, press `Enter` .

Now, all the remaining cout statement will be printed in console once.



So, can you guess?

What is the task `cin.get()` do in the code?



yes, it pause the code execution until player give the input `Enter.`

And using this `cin.get()` function, you can make your code player interactive.



Now, You have to use `cin.get()` Where You Need controlled player interaction.



> **Brainstorming 💡**

> Think about where you can put this `cin.get()` function and to interact with a player in better way.



But, Wait. Instead of directly writing of cin.get() in your code, which does not give essence of what it does.

You can create a separate function named as `waitForEnter() `.

And Call this function where you required a pause for better player Interaction.



# WaitforEnter() Function


---



Now, it's time to make changes to the code.



> **TODO:**
> ✅Create a Function` WaitforEnter() `in main.cpp. just below using namespace std;.
> ✅ Think about Where we Have to Implement inside function the` WaitforEnter()`

> ✅ Put Function Call ` WaitforEnter() `Where ever it's Required To make Controlled User Interaction.



This Function allows you to control player interaction. 



WaitforEnter() Function```cpp
// Function to wait for user to press Enter
void waitForEnter() {
  cin.get(); // Wait for Enter key
}

// cin.get() ---> is function will temporarly pause the program till Press Enter Key
```



After adding this function to your `main.cpp`, code will look like this :



CodeTillNow```cpp
#include <iostream>
#include <string>
using namespace std;


// Function to wait for user to press Enter
void waitForEnter() {
    cin.get();    // Wait for Enter key
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

    void attack() {
        cout << name << " attacks with a powerful move!\n";
    }
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
        waitForEnter(); // Wait for user to press Enter before proceeding
    }
};

// ProfessorOak class definition
class ProfessorOak {
public:
    string name;

    // Parameterized constructor
    ProfessorOak(string p_name) {
        name = p_name;
    }

    void greetPlayer(Player& player) {
        cout << name << ": Hello there! Welcome to the world of Pokemon!\n";
        waitForEnter();
        cout << name << ": My name is Oak. People call me the Pokemon Professor!\n";
        waitForEnter();
        cout << name << ": But enough about me. Let's talk about you!\n";
        waitForEnter();
    }

    void offerPokemonChoices(Player& player) {
        cout << name << ": First, tell me, what’s your name? \t [Please Enter Your Name]\n";
        getline(cin, player.name);
        cout << name << ": Ah, " << player.name << "! What a fantastic name!\n";
        waitForEnter();
        cout << name << ": You must be eager to start your adventure. But first, you’ll need a Pokemon of your own!\n";
        waitForEnter();

        // Presenting Pokemon choices
        cout << name << ": I have three Pokemon here with me. They’re all quite feisty!\n";
        waitForEnter();
        cout << name << ": Choose wisely...\n";
        cout << "1. Charmander - The fire type. A real hothead!\n";
        cout << "2. Bulbasaur - The grass type. Calm and collected!\n";
        cout << "3. Squirtle - The water type. Cool as a cucumber!\n";

        int choice;
        cout << name << ": So, which one will it be? Enter the number of your choice: ";
        cin >> choice;

        player.choosePokemon(choice);
        waitForEnter();
    }

    // New method for the main quest conversation
    void explainMainQuest(Player& player) {
     
        cout << "Professor Oak: Oak-ay" << player.name << "!, I am about to explain you about your upcoming grand adventure.\n";
        waitForEnter();
        cout << "Professor Oak: You see, becoming a Pokémon Master is no easy feat. It takes courage, wisdom, and a bit of luck!\n";
        waitForEnter();
        cout << "Professor Oak: Your mission, should you choose to accept it—and trust me, you really don’t have a choice—is to collect all the Pokémon Badges and conquer the Pokémon League.\n";
        waitForEnter();

        cout << "\n" << player.name << ": Wait... that sounds a lot like every other Pokémon game out there...\n";
        waitForEnter();
        cout << "Professor Oak: Shhh! Don't break the fourth wall, " << player.name << "! This is serious business!\n";
        waitForEnter();

        cout << "\nProfessor Oak: To achieve this, you’ll need to battle wild Pokémon, challenge gym leaders, and of course, keep your Pokémon healthy at the PokeCenter.\n";
        waitForEnter();
        cout << "Professor Oak: Along the way, you'll capture new Pokémon to strengthen your team. Just remember—there’s a limit to how many Pokémon you can carry, so choose wisely!\n";
        waitForEnter();

        cout << "\n" << player.name << ": Sounds like a walk in the park... right?\n";
        waitForEnter();
        cout << "Professor Oak: Hah! That’s what they all say! But beware, young Trainer, the path to victory is fraught with challenges. And if you lose a battle... well, let’s just say you'll be starting from square one.\n";
        waitForEnter();

        cout << "\nProfessor Oak: So, what do you say? Are you ready to become the next Pokémon Champion?\n";
        waitForEnter();
        cout << "\n" << player.name << ": Ready as I’ll ever be, Professor!\n";
        waitForEnter();

        cout << "\nProfessor Oak: That’s the spirit! Now, your journey begins...\n";
        waitForEnter();
        cout << "Professor Oak: But first... let's just pretend I didn't forget to set up the actual game loop... Ahem, onwards!\n";
        waitForEnter();
    }
};

int main() {
    // Create Pokemon and Player objects for the game
    Pokemon charmander("Charmander", PokemonType::FIRE, 100); // Using parameterized constructor

    // Continue with the main flow of the game
    ProfessorOak professor("Professor Oak");
    Player player("Ash", charmander);

    // Greet the player and offer Pokemon choices
    professor.greetPlayer(player);
    professor.offerPokemonChoices(player);

    // Explain the main quest
    professor.explainMainQuest(player);

    // Placeholder for where the game loop will start
    cout << "\n[Placeholder for the Game Loop]\n";

    return 0;
}
```






---





Now, Player can Interact with a game in controlled manner and understand the game.

During interaction, a lot of messages printed on a game console.

And after some time, the screen feels cluttered with information.



And again the problem created that it's hard to understand new information with the cluttered once.

So, you have to clear your screen first before displaying new messages.



Can you think about how to clear the console? Before Printing more information on the screen.



Lets again understand with doing the code.

Try to Print 9-10 Cout statements with Function in a main function separately.



> Note : Create any other Folder in VsCode or any other IDE , in which you are writing code. and Implement this code.



Try these statement to print

 These statement related to Professor Oak.



1. Hi, I’m Professor Oak, and I study Pokémon.
2. I’m here to help new trainers like you start their journey.
3. In Pallet Town, I give trainers their very first Pokémon partner.
4. I also created the Pokédex to help you record information on all the Pokémon you encounter.
5. There are so many Pokémon in the world, each with unique abilities!
6. Your journey will be full of discovery, adventure, and challenges.
7. But don’t worry, I’ll be here to guide you whenever you need help.
8. Train hard, learn about Pokémon, and become the best trainer you can be.
9. The bond between you and your Pokémon is what makes you strong.
10. So, get ready—your adventure begins now!



 These statements related to the player.



1. I am a player, ready to embark on my Pokémon adventure.  
2. With my first Pokémon by my side, I will explore new places and meet new friends.  
3. I will catch Pokémon, train them, and help them grow stronger.  
4. As a player, my goal is to become the Pokémon Champion by earning Gym Badges.  
5. I’ll face tough challenges and battle skilled trainers along the way.  
6. But it’s not just about winning—building bonds with my Pokémon is my true strength.  
7. I’ll discover new regions, find rare Pokémon, and uncover hidden secrets.  
8. Every decision I make will shape the course of my journey.  
9. I am determined to train hard and become the best Pokémon Trainer.  
10. My adventure is just beginning, and I am ready for whatever comes next!



did you write the code ? 

If yes, then run the code. You will notice all statements printed at once.

This is not understable at all as discussed earlier . so, You can put `cin.get()` function for controlled Interaction.



did you put `cin.get()` in a code?

Now, run the code again.



Now , the further statements will print after the Enter press and so on.



Example Code```cpp
#include <iostream>
 using namespace std;
 int main() {
     
     
     // Professor Oak Messages
     cout << "Hi, I am Professor Oak, and I study Pokémon." << endl;
    
      cin.get();
     cout << "I am here to help new trainers like you start their journey." << endl;
     cin.get();
     cout << "In Pallet Town, I give trainers their very first Pokémon partner." << endl;
     cin.get();
     cout << "I also created the Pokédex to help you record information on all the Pokémon you encounter." << endl;
     cin.get();
     cout << "There are so many Pokémon in the world, each with unique abilities!" << endl;
     cin.get();
     cout << "Your journey will be full of discovery, adventure, and challenges." << endl;
     cin.get();
     cout << "But dont worry, I will be here to guide you whenever you need help." << endl;
     cin.get();
     cout << "Train hard, learn about Pokémon, and become the best trainer you can be." << endl;
     cin.get();
     cout << "The bond between you and your Pokémon is what makes you strong." << endl;
     cin.get();
     cout << "So, get ready—your adventure begins now!" << endl;
     cin.get();
     
     
     // Player Messages 
     
     cout << "I am a player, ready to embark on my Pokémon adventure. " << endl;
     cin.get();
     cout << "With my first Pokémon by my side, I will explore new places and meet new friends.   " << endl;
     cin.get();
     cout << "I will catch Pokémon, train them, and help them grow stronger.  " << endl;
     cin.get();
     cout << "As a player, my goal is to become the Pokémon Champion by earning Gym Badges. " << endl;
     cin.get();
     cout << "I will face tough challenges and battle skilled trainers along the way." << endl;
     cin.get();
     cout << "But it is not just about winning—building bonds with my Pokémon is my true strength.  " << endl;
     cin.get();
     cout << "I will discover new regions, find rare Pokémon, and uncover hidden secrets.   " << endl;
     cin.get();
     cout << "Every decision I make will shape the course of my journey.  " << endl;
     cin.get();
     cout << "I am determined to train hard and become the best Pokémon Trainer. " << endl;
     cin.get();
     cout << "My adventure is just beginning, and I am ready for whatever comes next!" << endl;

  return 0;
}
```



After Printing Professor Oak statements,Your console filled with lot of Information.

And still if you press `Enter `the Player statements also start printing on the same console.



Which we didn't want? 

Beacuse screen is Looking Cluttered which making difficulty to read new messages.

So, You want Player messages will start printing with the fresh screen.



To do this, we must first clear all the professor Oak messages.

How can you clear these messages first?



Lets add this line after Professor Oak messages. 

` system("cls")` - if you have 32-bit machine and

`system("clear") `- if you have 64-bit machine



Now, Run the Code.

And Try to Interact with the code.



 Suddenly, you will notice that the output screen will clear after printing Professor Oak's Messages.

And Start Printing player Messages.



Now, You can Interact with the Player.



So, Now you can guess?

What system("cls) or system("clear") do?



Yes, It just clears the cluttered Output screen.



**Final Code to clear screen :**

```cpp
#ifdef _WIN32
        system("cls");
    #else
        (void)system("clear");
    #endif
```



> Note : Try to Understand this code .



But Wait, instead of directly writing the above code in your Final game code.

You can create a separate function named as `clearConsole() `.

And Call this function where you required to clear your game console at any moment.





# clearConsole() Function


---



Now, it's time to make changes to the code



> **TODO:**
> ✅Create a Function` clearConsole() `in `main.cpp`  just above waitForEnter() Function.
> ✅ Think about Where we Have to call this function to clear output screen.



clearConsole() Function```cpp
// Function to clear the console
void clearConsole() {
// Platform-specific clear console command
#ifdef _WIN32
  system("cls");
#else
  (void)system("clear");
#endif
}
```



Call your Function, Where You feel Information is cluttered and need clear game screen

After adding this Function in your `main.cpp`



Code TillNow```cpp
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



**Great Job!🎉**
