> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your current branch called → ***Feature_3_Main_Quest***

> Let’s start working on the new feature now!





**Professor Oak :**

Welcome, young Trainer!

The Pokémon world is vast and full of mysteries.

![ProOak](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_28_2024__10_50_19.png)



**Professor Oak :**

But before you begin your journey, you have an important mission.

Your main goal is to collect eight Pokémon Badges.



To earn these, you must defeat the Gym Leaders spread across the region.

Each badge will prove your skill and determination.



![Badges](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_26_2024__11_59_19.png)



**Professor Oak :**

Your journey won’t be easy.

You’ll face many challenges— wild Pokémon to capture, Trainers to battle and tough Gym Leaders.



But each victory brings you closer to your ultimate goal: the Pokémon League.

Only those with all eight badges can challenge the Elite Four and the reigning Champion.



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_28_2024__11_02_44.png)



**Professor Oak :**

To succeed in your quest.  

You must capture and train a strong team of Pokémon.  



Each Gym Leader uses a different type of Pokémon.  

So you’ll need to adapt and plan to win.  



As you travel from town to town. 

Your Pokémon will grow stronger,  and so will you.  



![poketrain](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_28_2024__11_17_14.png)



**Professor Oak :**

It’s not just about winning battles—  it’s about forming a bond with your Pokémon. 

Knowing their strengths and weaknesses,  and becoming a true Pokémon Master.



Your journey is long and full of challenges,  but also victory ahead.  

With determination, strategy, and a bit of luck, you’ll collect all eight badges.

Earn the right to challenge the Pokémon League.  



Defeat the Elite Four,  and you’ll face the Champion in an epic final battle.  

If you succeed,  you will earn the title of Pokémon Champion,  the highest honor a Trainer can achieve.



![Pokemon Champion](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_26_2024__12_52_24.png)



**Professor Oak :**

The world of Pokémon is waiting for you.  

Face each challenge with courage.  



Learn from every battle.  

Remember — the bond between you and your Pokémon is the key to victory.  



![pokemon bond](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_26_2024__12_48_06.png)





**Your adventure begins now!**



# Coding Time


---



**Professor Oak:** 

I have just given you your Main Quest!

A path to travel to reach your destiny. (Every game has one)



But how are the actual players going to learn about this Main Quest?

How are they going to know what their objective is in the game?!



You must update your code to let me tell them about the objective of the game as well.

That way they can also walk the same path as you of becoming the Pokemon Champion





Professor Oak wants to tell the main quest to the players in the game, it looks like another behaviour for Professor Oak in code.

You should create another function in your code to implement this behavior.



You have to create a new function → `**explainMainQuest()**` in `**ProfessorOak**` class.



> **TODO:**
> ✅ Create `**explainMainQuest()**` method in `**ProfessorOak**` Class.
> ✅ Pass the player object as parameter to this method.

> ✅ Print the below given dialogs to interact with the player.



Professor Oak's Dialogs          

```plaintext
1. Professor Oak:		Oak-ay " [player.name], I am about to explain you about your upcoming grand adventure.

2. Professor Oak:   You see, becoming a Pokémon Master is no easy feat. It takes courage, wisdom, and a bit of luck.

3. Professor Oak:  Your mission, should you choose to accept it (and trust me, you really don’t have a choice) is to collect all the Pokémon Badges 
and conquer the Pokémon League. 

4. [player.name]:   Wait... that sounds a lot like every other Pokémon game out there.

5. Professor Oak:  Shhh! Don't break the fourth wall [player.name] ! This is serious business.

6. Professor Oak:  To achieve this, you’ll need to battle wild Pokémon, challenge gym leaders, and of course, keep your Pokémon healthy at the
PokeCenter.

7. Professor Oak:   Along the way, you'll capture new Pokémon to strengthen your team. Just remember—there’s a limit to how many Pokémon you
can carry, so choose wisely!

8. [player.name] : Sounds like a walk in the park... right?

9. Professor Oak: Hah! That’s what they all say! But beware, young Trainer, the path to victory is fraught with challenges. And if you lose a battle... well, let’s just say you'll be starting from square one.

10. Professor Oak: So, what do you say? Are you ready to become the next Pokémon Champion?

11. [player.name]: Ready as I’ll ever be, Professor!

12. Professor Oak: That’s the spirit! Now, your journey begins.

13. Professor Oak: But first... let's just pretend I didn't forget to set up the actual game loop... Ahem, onwards!
```

         

  

click here to see the solution

```cpp
void explainMainQuest(Player& player) {
   

    cout << "Professor Oak: Oak-ay" << player.name << "!, I am about to explain you about your upcoming grand adventure.\n";
    
    cout << "Professor Oak: You see, becoming a Pokémon Master is no easy feat. It takes courage, wisdom, and a bit of luck!\n";
   
    cout << "Professor Oak: Your mission, should you choose to accept it—and trust me, you really don’t have a choice—is to collect all the Pokémon Badges and conquer the Pokémon League.\n";
    

    cout << "\n" << player.name << ": Wait... that sounds a lot like every other Pokémon game out there...\n";
    
    cout << "Professor Oak: Shhh! Don't break the fourth wall, " << player.name << "! This is serious business!\n";
    

    cout << "\nProfessor Oak: To achieve this, you’ll need to battle wild Pokémon, challenge gym leaders, and of course, keep your Pokémon healthy at the PokeCenter.\n";
    
    cout << "Professor Oak: Along the way, you'll capture new Pokémon to strengthen your team. Just remember—there’s a limit to how many Pokémon you can carry, so choose wisely!\n";
    

    cout << "\n" << player.name << ": Sounds like a walk in the park... right?\n";
    
    cout << "Professor Oak: Hah! That’s what they all say! But beware, young Trainer, the path to victory is fraught with challenges. And if you lose a battle... well, let’s just say you'll be starting from square one.\n";
    

    cout << "\nProfessor Oak: So, what do you say? Are you ready to become the next Pokémon Champion?\n";
  
    cout << "\n" << player.name << ": Ready as I’ll ever be, Professor!\n";
    

    cout << "\nProfessor Oak: That’s the spirit! Now, your journey begins...\n";
   
    cout << "Professor Oak: But first... let's just pretend I didn't forget to set up the actual game loop... Ahem, onwards!\n";
   
}
```

         

Before you start working on the game loop, let's clean up some of the old code. 

You used `cout` statements earlier in the constructor assignment to check either your constructors were working or not.



Check out how the main function looks like because of that

```cpp
int main() {
    // Task 1: Test default and parameterized constructors
    Pokemon defaultPokemon; // Using default constructor
    Pokemon charmander("Charmander", PokemonType::FIRE, 100); // Using parameterized constructor
    cout << "Pokemon Details:\n";
    cout << "Name: " << defaultPokemon.name << "\nType: " << (int)defaultPokemon.type << "\nHealth: " << defaultPokemon.health << "\n";
    cout << "Name: " << charmander.name << "\nType: " << (int)charmander.type << "\nHealth: " << charmander.health << "\n";

    // Task 2: Test the copy constructor
    Pokemon bulbasaur("Bulbasaur", PokemonType::GRASS, 100); // Create a Pokemon
    Pokemon bulbasaurCopy = PokemonChoice::bulbasaur; // Copy the Pokemon
    cout << "Original Pokemon Health: " << bulbasaur.health << "\n";
    cout << "Copied Pokemon Health: " << bulbasaurCopy.health << "\n";

    // Modify the copy
    bulbasaurCopy.health = 80;
    cout << "After Modification:\n";
    cout << "Original Pokemon Health: " << bulbasaur.health << "\n";
    cout << "Copied Pokemon Health: " << bulbasaurCopy.health << "\n";

    // Task 3: Test the destructor
    {
        Pokemon squirtle("Squirtle", PokemonType::WATER, 100); // Pokemon will be destroyed at the end of this scope
    } // Destructor will be called here

    // Continue with the main flow of the game
    ProfessorOak professor("Professor Oak");
    Player player("Ash", PokemonChoice::charmander);

    // Greet the player and offer Pokemon choices
    professor.greetPlayer(player);
    professor.offerPokemonChoices(player);

    // Conclude the first chapter
     cout << "Professor Oak: " << player.chosenPokemon.name << " and you, " << player.name << ", are going to be the best of friends!\n";
     cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\n";

    return 0;
}
```





All these statements were for testing purposes and I hope that you have clearly understood how constructors work!

But now that you know what they are, It's time to clean up the code.

Remove all these cout statements from the `**main()**` function



Final Code should look like this

```cpp
#include <iostream>
#include <string>
using namespace std;


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
       
        cout << name << ": My name is Oak. People call me the Pokemon Professor!\n";
       
        cout << name << ": But enough about me. Let's talk about you!\n";
        
    }

    void offerPokemonChoices(Player& player) {
        cout << name << ": First, tell me, what’s your name? \t [Please Enter Your Name]\n";
        getline(cin, player.name);
        cout << name << ": Ah, " << player.name << "! What a fantastic name!\n";
       
        cout << name << ": You must be eager to start your adventure. But first, you’ll need a Pokemon of your own!\n";
        

        // Presenting Pokemon choices
        cout << name << ": I have three Pokemon here with me. They’re all quite feisty!\n";
       
        cout << name << ": Choose wisely...\n";
        cout << "1. Charmander - The fire type. A real hothead!\n";
        cout << "2. Bulbasaur - The grass type. Calm and collected!\n";
        cout << "3. Squirtle - The water type. Cool as a cucumber!\n";

        int choice;
        cout << name << ": So, which one will it be? Enter the number of your choice: ";
        cin >> choice;

        player.choosePokemon(choice);
       
    }

    // New method for the main quest conversation
    void explainMainQuest(Player& player) {
        

        cout << "Professor Oak: Oak-ay" << player.name << "!, I am about to explain you about your upcoming grand adventure.\n";
       
        cout << "Professor Oak: You see, becoming a Pokémon Master is no easy feat. It takes courage, wisdom, and a bit of luck!\n";
       
        cout << "Professor Oak: Your mission, should you choose to accept it—and trust me, you really don’t have a choice—is to collect all the Pokémon Badges and conquer the Pokémon League.\n";
        

        cout << "\n" << player.name << ": Wait... that sounds a lot like every other Pokémon game out there...\n";
        
        cout << "Professor Oak: Shhh! Don't break the fourth wall, " << player.name << "! This is serious business!\n";
        

        cout << "\nProfessor Oak: To achieve this, you’ll need to battle wild Pokémon, challenge gym leaders, and of course, keep your Pokémon healthy at the PokeCenter.\n";
        
        cout << "Professor Oak: Along the way, you'll capture new Pokémon to strengthen your team. Just remember—there’s a limit to how many Pokémon you can carry, so choose wisely!\n";
        

        cout << "\n" << player.name << ": Sounds like a walk in the park... right?\n";
        
        cout << "Professor Oak: Hah! That’s what they all say! But beware, young Trainer, the path to victory is fraught with challenges. And if you lose a battle... well, let’s just say you'll be starting from square one.\n";
       

        cout << "\nProfessor Oak: So, what do you say? Are you ready to become the next Pokémon Champion?\n";
        
        cout << "\n" << player.name << ": Ready as I’ll ever be, Professor!\n";
       

        cout << "\nProfessor Oak: That’s the spirit! Now, your journey begins...\n";
       
        cout << "Professor Oak: But first... let's just pretend I didn't forget to set up the actual game loop... Ahem, onwards!\n";
        
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



Now, run this code and see what the output is....? look on the terminal



Output Till Now```cpp
Professor Oak: Hello there! Welcome to the world of Pokemon!
Professor Oak: My name is Oak. People call me the Pokemon Professor!
Professor Oak: But enough about me. Let's talk about you!
Professor Oak: First, tell me, what’s your name?  [Please Enter Your Name]
```



4  Lines will print in the Console at once and also ask for your name.

Now, Enter the player name and Few more lines will print in the output screen.



Output Till Now - cont !```cpp
Professor Oak: Hello there! Welcome to the world of Pokemon!
Professor Oak: My name is Oak. People call me the Pokemon Professor!
Professor Oak: But enough about me. Let's talk about you!
Professor Oak: First, tell me, what’s your name?   [Please Enter Your Name]
Aman
Professor Oak: Ah, Aman! What a fantastic name!
Professor Oak: You must be eager to start your adventure. But first, you’ll need a Pokemon of your own!
Professor Oak: I have three Pokemon here with me. They’re all quite feisty!
Professor Oak: Choose wisely...
1. Charmander - The fire type. A real hothead!
2. Bulbasaur - The grass type. Calm and collected!
3. Squirtle - The water type. Cool as a cucumber!
Professor Oak: So, which one will it be? Enter the number of your choice: 
```



And also asks for a choice of Pokemon. Choose one Pokemon out of three.

It will print More number lines at once.



Output Till Now - Cont !```cpp
Professor Oak: Hello there! Welcome to the world of Pokemon!
Professor Oak: My name is Oak. People call me the Pokemon Professor!
Professor Oak: But enough about me. Let's talk about you!
Professor Oak: First, tell me, what’s your name?         [Please Enter Your Name]
Aman
Professor Oak: Ah, Aman! What a fantastic name!
Professor Oak: You must be eager to start your adventure. But first, you’ll need a Pokemon of your own!
Professor Oak: I have three Pokemon here with me. They’re all quite feisty!
Professor Oak: Choose wisely...
1. Charmander - The fire type. A real hothead!
2. Bulbasaur - The grass type. Calm and collected!
3. Squirtle - The water type. Cool as a cucumber!
Professor Oak: So, which one will it be? Enter the number of your choice: 2
Player Aman chose Bulbasaur!
Professor Oak: Oak-ayAman!, I am about to explain you about your upcoming grand adventure.
Professor Oak: You see, becoming a Pokémon Master is no easy feat. It takes courage, wisdom, and a bit of luck!
Professor Oak: Your mission, should you choose to accept it—and trust me, you really don’t have a choice—is to collect all the Pokémon Badges and conquer the Pokémon League.

Aman: Wait... that sounds a lot like every other Pokémon game out there...
Professor Oak: Shhh! Don't break the fourth wall, Aman! This is serious business!

Professor Oak: To achieve this, you’ll need to battle wild Pokémon, challenge gym leaders, and of course, keep your Pokémon healthy at the PokeCenter.
Professor Oak: Along the way, you'll capture new Pokémon to strengthen your team. Just remember—there’s a limit to how many Pokémon you can carry, so choose wisely!

Aman: Sounds like a walk in the park... right?
Professor Oak: Hah! That’s what they all say! But beware, young Trainer, the path to victory is fraught with challenges. And if you lose a battle... well, let’s just say you'll be starting from square one.

Professor Oak: So, what do you say? Are you ready to become the next Pokémon Champion?

Aman: Ready as I’ll ever be, Professor!

Professor Oak: That’s the spirit! Now, your journey begins...
Professor Oak: But first... let's just pretend I didn't forget to set up the actual game loop... Ahem, onwards!
```



When Professor Oak explains the game challenges and goals all at once.

Some of his words are getting skipped.

Why does this happen?



The problem is that everything is shown too quickly. 

The player doesn't have enough time to read each line before the next one appears.

What’s the ideal way?



The information should be shown bit by bit, line by line. 

This way, the player can follow along and understand what Professor Oak is saying.



In the next section, we’ll talk about how to control the output.

So that every lesson Professor Oak teaches is clear and easy to understand by the player.
