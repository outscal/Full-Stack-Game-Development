look at the time in your phone now. Now, read the main function below. 



```cpp
int main() { 
// Initialize Professor Oak and Player with default placeholder values 

ProfessorOak professor("Professor Oak"); 

Pokemon placeholderPokemon("Placeholder", FIRE, 0);  // Placeholder Pokemon until chosen 

Player player("", placeholderPokemon); 

// Greet the player and offer Pokemon choices

professor.greetPlayer(player); 
professor.offerPokemonChoices(player); 
// Conclude the first chapter 

cout << "Professor Oak: " << player.chosenPokemon.name << " and you, " << player.name << ", are going to be the best of friends!\\n"; std::cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\\n"; 

return 0; 

}
```



See the time, again.



How long did it take you to read the main function? 



Didn't it take comparatively less time to read the same main function that previously required at least five minutes when you weren't using a class for Player, Professor Oak and the Pokémon?

YES!!!



The main function has become comparatively shorter, more readable, and easier to manage now. Did you notice how cleaner the code is becoming?



![Image](//outscal.github.io/Full-Stack-Game-Development/images/3eecbeeca1fbccff.png)



## ENcapsulation


---



What you did now is something known as encapsulation. It is one of the key principles of OOP.



Encapsulation is the process of gathering related data (attributes) and functionalities (methods) and grouping them together into a single unit, which in this case, is a class.



Look into the main function code below where we have not used any class. 



If I ask you to change how Professor Oak greets the player from "Hello there! Welcome to the world of Pokemon!" to "Hello Young Pokemon trainer! Welcome to the world of Pokemon!" how will you do it?



`main function before using classes````cpp
#include <iostream>
#include <string>
using namespace std;

// Define an enum for Pokemon choices
enum class PokemonChoice {
    Charmander,
    Bulbasaur,
    Squirtle,
    Pikachu // Added Pikachu as the default choice
};

int main() {
    // Variables to store player name and chosen Pokemon
    string player_name;
    PokemonChoice chosen_pokemon;

    // Introduction by the Professor
    cout << "Professor Oak: Hello there! Welcome to the world of Pokemon!\n";
    cout << "Professor Oak: My name is Oak. People call me the Pokemon Professor!\n";
    cout << "Professor Oak: But enough about me. Let's talk about you!\n";
    
    // Taking player name as input
    cout << "Professor Oak: First, tell me, what’s your name?\n";
    getline(std::cin, player_name);
    
    cout << "Professor Oak: Ah, " << player_name << "! What a fantastic name!\n";
    cout << "Professor Oak: You must be eager to start your adventure. But first, you’ll need a Pokemon of your own!\n";
    
    // Presenting Pokemon choices
    cout << "Professor Oak: I have three Pokemon here with me. They’re all quite feisty!\n";
    cout << "Professor Oak: Choose wisely...\n";
    cout << "1. Charmander - The fire type. A real hothead!\n";
    cout << "2. Bulbasaur - The grass type. Calm and collected!\n";
    cout << "3. Squirtle - The water type. Cool as a cucumber!\n";
    
    int choice;
    cout << "Professor Oak: So, which one will it be? Enter the number of your choice: ";
    cin >> choice;

    // Map the integer choice to the corresponding enum value
    switch(choice) {
        case 1:
            chosen_pokemon = PokemonChoice::Charmander;
            break;
        case 2:
            chosen_pokemon = PokemonChoice::Bulbasaur;
            break;
        case 3:
            chosen_pokemon = PokemonChoice::Squirtle;
            break;
        default:
            chosen_pokemon = PokemonChoice::Pikachu; // Default to Pikachu if invalid choice
            break;
    }

    // Respond based on the chosen Pokemon
    switch(chosen_pokemon) {
        case PokemonChoice::Charmander:
            cout << "Professor Oak: A fiery choice! Charmander is yours!\n";
            break;
        case PokemonChoice::Bulbasaur:
            cout << "Professor Oak: A fine choice! Bulbasaur is always ready to grow on you!\n";
            break;
        case PokemonChoice::Squirtle:
            cout << "Professor Oak: Splendid! Squirtle will keep you cool under pressure!\n";
            break;
        case PokemonChoice::Pikachu:
            cout << "Professor Oak: Ah, a surprise! Pikachu has decided to join you on your journey!\n";
            break;
    }

    // Concluding the first chapter
    cout << "Professor Oak: " << (chosen_pokemon == PokemonChoice::Charmander ? "Charmander" :
                                         chosen_pokemon == PokemonChoice::Bulbasaur ? "Bulbasaur" :
                                         chosen_pokemon == PokemonChoice::Squirtle ? "Squirtle" : "Pikachu")
              << " and you, " << player_name << ", are going to be the best of friends!\n";
    cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\n";

    return 0;
}
```



Did you go through each line of the main function just to find where Professor Oak greets the player?



Isn't this painful to read the entire code every time you want to make some changes?



Now do the same thing for the code below



`main function after using classes````cpp
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
 ELECTRIC 
 };
 
 // Pokemon class definition 
 class Pokemon { 
 public: 

 // Attributes 
    string name; 
    PokemonType type; 
    int health; 
    // Constructor 

    Pokemon(string p_name, PokemonType p_type, int p_health) { 
        name = p_name; 
        type = p_type; 
        health = p_health; 
    } 

    Pokemon(){

    }

 // Method to simulate attacking (just for demonstration) 
    void attack() { 
    cout << name << "attacks with a powerful move!\n"; } 
 };
 
 
 // Player class definition 
class Player { 
 public: 
 
 // Attributes 
    string name; 
    Pokemon chosenPokemon; 

    Player(){
        chosenPokemon = Pokemon();
    }
 
 // Constructor 
    Player(std::string p_name, Pokemon p_chosenPokemon) { 
        name = p_name;
        chosenPokemon = p_chosenPokemon; 
    }
 
 // Method to choose a Pokemon 
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
            chosenPokemon = Pokemon("Pikachu", PokemonType::ELECTRIC, 100); break; 
        } 

        cout << "Player " << name << " chose " << chosenPokemon.name << "!\n"; 
    } 
};
    
    
// ProfessorOak class definition 
class ProfessorOak { 
public: 

    // Attributes 
    string name; 

    // Constructor 
    ProfessorOak(string p_name) { 
    name = p_name; 
    } 

    // Method to greet the player 
    void greetPlayer(Player& player) { 
    cout << name << ": Hello there! Welcome to the world of Pokemon!\n"; 
    cout << name << ": My name is Oak. People call me the Pokemon Professor!\n"; 
    cout << name << ": But enough about me. Let's talk about you!\n"; 
}

// Method to ask the player to choose a Pokemon 
void offerPokemonChoices(Player& player) { 
        cout << name << ": First, tell me, what’s your name?\n"; 
        getline(cin, player.name); 
        cout << name << ": Ah, " << player.name << "! What a fantastic name!\n"; 
        cout << name << ": You must be eager to start your adventure. But first, you’ll need a Pokemon of your own!\n"; 
        // Presenting Pokemon choices 
        cout << name << ": I have three Pokemon here with me. They’re all quite feisty!\n"; 
        cout << name << ": Choose wisely...\n"; cout << "1. Charmander - The fire type. A real hothead!\n"; 
        cout << "2. Bulbasaur - The grass type. Calm and collected!\n"; 
        cout << "3. Squirtle - The water type. Cool as a cucumber!\n"; 
        int choice; 
        cout << name << ": So, which one will it be? Enter the number of your choice: "; 
        cin >> choice;
        player.choosePokemon(choice); 
   } 
}; 


int main() { 
    // Initialize Professor Oak and Player with default placeholder values 
    ProfessorOak professor("Professor Oak"); 
    Pokemon placeholderPokemon("Placeholder", PokemonType::FIRE, 0); 

    // Placeholder Pokemon until chosen 
    Player player("", placeholderPokemon); 

    // Greet the player and offer Pokemon choices 
    professor.greetPlayer(player); 
    professor.offerPokemonChoices(player); 

    // Conclude the first chapter 
    cout << "Professor Oak: " << player.chosenPokemon.name << " and you, " << player.name << ", are going to be the best of friends!\n"; 
    cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\n"; 
    return 0; 
}
```



What did you do?



You directly went to the function where ProfessorOak is greeting the player in ProfessorOak class and made the changes



See how easy and quick it was making the changes :)




---



- The code was clean and modular improving the readability
- you didn't have to go through each line of the code to make the changes and no other object in the code are affected by the change making the code more flexible 
- Another benefit of encapsulation is that it reduces the complexity and makes the code more manageable. For example, think of a class as a Pokeball. Inside the Pokeball, you have all the complex details about a Pokemon, but when you want to use it, you just throw the Pokeball—you don’t need to know what’s happening inside. 




---





`Encapsulation makes our codebase more:`- **Reusable - **Encapsulated code like a class defines certain functionalities and properties, allowing it to be reused in the future.
- **modular - **Encapsulating code divides big chunks of code into smaller pieces that are easier to move around.
- **flexible - **One outcome of encapsulating code is that it enables you to change something inside the encapsulated unit without that change affecting outside code that depends on the unit.



> A rule of thumb for when to encapsulate a part of your code is that if the code starts to vary, then it might be better to separate it.



Did you now understand the difference what classes and Objects can make to our codebase and what is the importance of encapsulation in OOP



![](https://cdn.discordapp.com/attachments/1269892230274089043/1278300905296494592/file-fWitnS3ae2SOwPy0EHS9W37S.png?ex=66d2483d&is=66d0f6bd&hm=68127b4e3eefa595ac3501d444a7eca8ab0277b9c7e19be385f5cab9d6627b21&=)



*Professor Oak: "Yes I see, understanding encapsulation will be crucial as we move forward and start exploring more advanced topics like constructors and destructors."*
