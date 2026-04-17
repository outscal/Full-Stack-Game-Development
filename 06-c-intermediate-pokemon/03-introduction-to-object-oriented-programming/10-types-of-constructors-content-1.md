You have already studied in the previous chapter that constructors are special member function which initializes an object of a class and is automatically called when an object is created. 



But wait there is more!! You can use different types of constructors to initializes objects differently according to the need. Let's see what they are



## Default Constructor


---

What you have studied so far is default constructor. Default constructors takes no arguments, and it initializes all the Object with the same default value.



See the default constructor you have created in the pokemon class:



```cpp
 // Default constructor
    Pokemon() {
        name = "Unknown";
        type = PokemonType::FIRE; // Default type
        health = 50; // Default health
    }
```



Here, the default constructor provides the value "Unknown" to the name, FIRE as the type and 20 as health to any Pokémon object which is created using default constructor.



If no constructor is defined, C++ automatically provides a default constructor. 



However, if you define any constructor, the automatic default constructor is no longer provided unless explicitly defined.



> **TODO:**
> ✅ Create a default constructor for the Player class that initializes the player’s name to "Trainer" and the chosen Pokemon to a default Pokemon.

> ✅ Print a statement " A new player named name_of_the_player has been created "





Click here to see default Player constructor



```cpp
Player() { 
		name = "Trainer"; 
		chosenPokemon = Pokemon(); // Using the default Pokemon constructor 
		cout << "A new player named " << name << " has been created!\n"; 
}
```



## PARAmeterized Constructor


---



But what if you want to create object with specific values and not with the default values. 



We can simply pass arguments into the default constructor and assign their values to the attributes. 



These are called **parametrized constructors. **



Below is how you will create a parameterized constructor for the pokemon class:



```cpp
// Parameterized constructor 
Pokemon(string p_name, PokemonType p_type, int p_health) { 
		name = p_name; 
		type = p_type; 
		health = p_health; 
}
```



> **TODO:**

> ✅ Go to [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp) and Create a Trainer, which represents NPC trainers in the game, using both default and parameterized constructors.

> ✅ Inside the default constructor print "This is default constructor" and inside parameterized constructor print "This is Parameterized constructor"

> ✅ In the main function create Objects of Trainer class: NPC1 using default constructor and NPC2 using parameterized constructor.
> ✅ Run the code and check if NPC1 and NPC2 are being created.





## COPY CONSTRUCTORS


---



Do you remember ditto from Pokemon cartoon? (If you don't then WHY DON'T YOU?? go and watch one episode of pokemon where ditto is there)



Ditto is a type of Pokémon that rearranges its cell structure to transform itself. 



In Pokémon battles, it uses this power to copy the exact appearance and abilities of the Pokémon it is fighting. 

![gif](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_30_2024__04_40_41.gif)



If I ask you to create ditto in your pokemon game, how will you?



The answer is creating a Pokemon Object (ditto) that copies exactly the attributes of the other pokemon which ditto wants to imitates. 



But how will you copy the attributes of one object to other?



The answer is that we also have a constructor for this.



You can create new object as a copy of an existing object with the help of a constructor called copy constructor. 



There are two ways to copy the data of one object to other while creating, see the code below:



```cpp
Pokemon pokemon1("pikachu", PokemonType::Fire, 40);
Pokemon pokemon2;

//assignment operator is doing the copy
pokemon2  = pokemon1;

//Copy Constructor is doing the copy
Pokemon pokemon3 = pokemon1;
```



                      ![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_30_2024__05_08_27.png)



The answer is NO! we don't!!



## shallow copy


---



*When the compiler ****implicitly**** creates a copy constructor for us, then this is known as**** shallow copy***



In shallow copy we create a new object that stores the reference to the original elements. 



The original and the copy will point to the same objects, if one changes, the other will reflect those changes.



## DEEEP COPY


---



*When you ****explicitly**** write the code for copy constructor, then it is going to be ****deep copy.***



```cpp
// Copy constructor 
Pokemon(const Pokemon &other) { 
	name = other.name; 
	type = other.type; 
	health = other.health;
}
```



In deep copy we create object by copying all the data of the variables and assigning them to the variables of this new object. 



Both the objects are independent of each other and changes made in the new object will not be visible in the original object.



You can also see the use of const keyword when the Pokemon object is passed to copy constructor.

But why?



The `const` keyword is used in the copy constructor to ensure that the object being passed as an argument (`other`) cannot be modified inside the constructor.

Without `const`, you could unintentionally modify the object passed as the argument, which could lead to unexpected behavior.



Now, do you know how will you create ditto for your pokemon game? 



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_30_2024__05_11_51.gif)





> **TODO:**
> ✅ Copy paste the default, Parameterized and copy constructor that we have written for the Pokemon class in the Pokemon class
> ✅ Create a destructor for the pokemon class and include the statement `std::cout << name << " has been released.\n";` inside it.

> ✅ Create default and Parameterized constructor for the Player class.

> ✅ Create Parameterized constructor for the Professor class





Click here to see ```cpp
// Pokemon class definition
class Pokemon {
public:
    // Attributes
    string name;
    PokemonType type;
    int health;

    // Default constructor
    Pokemon() {
        name = "Unknown";
        type = PokemonType::NORMAL;
        health = 50;
        cout << "A new Pokemon has been created with the default constructor!\n";
    }

    // Parameterized constructor
    Pokemon(string p_name, PokemonType p_type, int p_health) {
        name = p_name;
        type = p_type;
        health = p_health;
        cout << "A new Pokemon named " << name << " has been created!\n";
    }

    // Copy constructor
    Pokemon(const Pokemon &other) {
        name = other.name;
        type = other.type;
        health = other.health;
        cout << "A new Pokemon has been copied from " << other.name << "!\n";
    }

    // Destructor
    ~Pokemon() {
        cout << name << " has been released.\n";
    }

    // Method to simulate attacking (just for demonstration)
    void attack() {
        cout << name << " attacks with a powerful move!\n";
    }
};

// Player class definition
class Player {
public:
    // Attributes
    string name;
    Pokemon chosenPokemon;

    // Default constructor
    Player() {
        name = "Trainer";
        chosenPokemon = Pokemon(); // Using the default Pokemon constructor
        cout << "A new player named " << name << " has been created!\n";
    }

    // Parameterized constructor
    Player(std::string p_name, Pokemon p_chosenPokemon) {
        name = p_name;
        chosenPokemon = p_chosenPokemon;
        cout << "Player " << name << " has been created!\n";
    }

    // Method to choose a Pokemon
    void choosePokemon(int choice) {
        switch (choice) {
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
    // Attributes
    string name;

    // Parameterized constructor
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
        getline(std::cin, player.name);
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
};
```





> **TODO:**
> ✅ In main function create a Pokemon Object `defaultPokemon` using default constructor
> ✅ Create another Pokemon Object `charmander` with values "Charmander", FIRE, 100

> ✅ Print the details of both the Pokemon

> ✅ Create a Pokemon bulbasaur with values "Bulbasaur", GRASS, 100

> ✅ Create another Pokemon bulbasaurCopy using copy constructor

> ✅ Print the details of both the Pokemon

> ✅ Modify the health of bulbasaurCopy to 80 and print its details again to see the changes

> ✅ Create a Pokemon inside curly braces to test if the destructor is working fine





Click here to see the entire code ```cpp
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
    // Attributes
    string name;
    PokemonType type;
    int health;

    // Default constructor
    Pokemon() {
        name = "Unknown";
        type = PokemonType::NORMAL;
        health = 50;
        cout << "A new Pokemon has been created with the default constructor!\n";
    }

    // Parameterized constructor
    Pokemon(string p_name, PokemonType p_type, int p_health) {
        name = p_name;
        type = p_type;
        health = p_health;
        cout << "A new Pokemon named " << name << " has been created!\n";
    }

    // Copy constructor
    Pokemon(const Pokemon &other) {
        name = other.name;
        type = other.type;
        health = other.health;
        cout << "A new Pokemon has been copied from " << other.name << "!\n";
    }

    // Destructor
    ~Pokemon() {
        cout << name << " has been released.\n";
    }

    // Method to simulate attacking (just for demonstration)
    void attack() {
        cout << name << " attacks with a powerful move!\n";
    }
};

// Player class definition
class Player {
public:
    // Attributes
    string name;
    Pokemon chosenPokemon;

    // Default constructor
    Player() {
        name = "Trainer";
        chosenPokemon = Pokemon(); // Using the default Pokemon constructor
         cout << "A new player named " << name << " has been created!\n";
    }

    // Parameterized constructor
    Player(std::string p_name, Pokemon p_chosenPokemon) {
        name = p_name;
        chosenPokemon = p_chosenPokemon;
        cout << "Player " << name << " has been created!\n";
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
                chosenPokemon = Pokemon("Pikachu", PokemonType::ELECTRIC, 100);
                break;
        }
        
        cout << "Player " << name << " chose " << chosenPokemon.name << "!\n";
    }
};

// ProfessorOak class definition
class ProfessorOak {
public:
    // Attributes
    string name;

    // Parameterized constructor
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
        getline(std::cin, player.name);
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
};

int main() {
    // Task 1: Test default and parameterized constructors
    Pokemon defaultPokemon; // Using default constructor
    Pokemon charmander("Charmander", PokemonType::FIRE, 100); // Using parameterized constructor
    
    cout << "Pokemon Details:\n";
    cout << "Name: " << defaultPokemon.name << "\nType: " << (int)defaultPokemon.type << "\nHealth: " << defaultPokemon.health << "\n";
    cout << "Name: " << charmander.name << "\nType: " << (int)charmander.type << "\nHealth: " << charmander.health << "\n";

    // Task 2: Test the copy constructor
    Pokemon bulbasaur("Bulbasaur", PokemonType::GRASS, 100); // Create a Pokemon
    Pokemon bulbasaurCopy = bulbasaur; // Copy the Pokemon
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
    Player player("Ash", charmander);

    // Greet the player and offer Pokemon choices
    professor.greetPlayer(player);
    professor.offerPokemonChoices(player);

    // Conclude the first chapter
    cout << "Professor Oak: " << player.chosenPokemon.name << " and you, " << player.name << ", are going to be the best of friends!\n";
    cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\n";

    return 0;
}
```
