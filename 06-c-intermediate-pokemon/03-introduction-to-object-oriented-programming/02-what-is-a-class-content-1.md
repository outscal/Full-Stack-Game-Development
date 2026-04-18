We ended the previous chapter with "**What is a class??**". 

You have already created few classes in your previous modules. 

But let's try to understand Class better and in a bit more depth by answering this question.



What comes to your mind when you think of a class?

No, it's not the class that you used to have in school



![Image result for meme saying NO](/Full-Stack-Game-Development/images/9fe59e5004feca6e.jpg)





In programing, a **Class** is a definition or a blueprint from which individual objects are created. 



**Professor Oak:** What do you mean its a blueprint?

Think about a blueprint for a car:





![c++](/Full-Stack-Game-Development/images/d9fb72cbb0b41d11.png)

***Blueprint of a Car***





This blueprint will tell us what a car has 
(**Data - **properties of the car**) **
Like:

- `**Body**`
- `**Color**`
- `**Wheels**`
- `**Engine**`



The same Blueprint will also tell you what this car is supposed to do if you ever create one!
(**Functionality - **The actions that the Car perform**) **

- `**Drive()**`
- `**Brake()**`
- `**Turn()**`
- `**PlayRadio()**`



![Blueprint](/Full-Stack-Game-Development/images/2a4f45609e9e6088.jpg)

*Equating blueprint and a class :*
*Properties of the Car (data) are present on the left*
*Methods of the Car (functions) are present on the right*



But the blueprint itself is not a car, right? 

It's just the definition of one car.



If you create a car of your own using this blueprint, then you will have an object with you. 

You can use this blueprint to make many more identical objects in a car factory. 

Each one will look and behave the same



![Cars](/Full-Stack-Game-Development/images/8652fb7673f818b7.jpg)



The cool part is that once the object is created you can modify each one without changing the rest.

Now you can change the color of your family car from red to rainbow without changing your Neighbor's  (*NOT RECOMMENED 😛)



In other words, **an Object is an actual representation of a class.**

We have discussed in the earlier chapter about the Objects that will be there in your Pokemon game (Do you remember?).



Now that you have got the basics out of the way. 

Let’s finally start writing some code for the classes and Objects in your game as we discussed earlier!



You should start by building an empty Pokemon class in your current Main.cpp file that will represent your Pokemon in the game 

Create the Pokemon class before and outside the main function `int main()`



```cpp
#include <iostream>

class Pokemon 
{
		// Empty Class
};

int main()
{
    //For now, keep whatever is inside the main() function as it is.
}
```



## PROPERTIES NEEDED


---



The Pokémon should have

- A **name**
- The **Type of Pokemon** it is: Fire, Electric, Water, Earth etc.
- **Health**: When the Pokémon will fight battles it's health will be reduce



```cpp
#include <iostream>
using namespace std;

class Pokemon
{
public:
    string name;
    PokemonType type;
    int health;
};

int main()
{
    //For now, keep whatever is inside the main() function as it is.
}

```



## Functions Needed


---



What will the Pokémon do?

It will **attack**. So, we will have a function for it.

For now, just print a statement "attacks with a powerful move!" when the function is called



```cpp
#include <iostream>
using namespace std;

class Pokemon {
public:
  string name;
  PokemonType type;
  int health;
  
  // Created 2 constructors
    Pokemon(){

    }

    Pokemon(string p_name, PokemonType p_type, int p_health){
        name = p_name;
        type = p_type;
        health = p_health;
    }


  void attack() { cout << name << "attacks with a powerful move!\n"; }
};

int main()
{
    //For now, keep whatever is inside the main() function as it is.
}
```

Congratulations!! You have created your first class, for the Pokémon :)



Now similarly, Create classes for Player and Professor Oak



> **TODO: Player Class**
> ✅ Create an empty class in your current `**Main.cpp**` file for the Player after the `Pokemon` class and before the `int main()` function
> ✅ In the Player class add the Properties for the Player: `**string p_name; **`and`** Pokemon p_chosenPokemon;**`

> ✅ Now create a function `**void choosePokemon()**` inside the Player class. The function will take an integer `**int choice**` as an argument

> ✅ Copy paste the switch statement that you have written earlier to choose pokemon inside the function `**void choosePokemon()**`



Click here to see the Player class```cpp
class Player {
public:
    // Attributes
    string name;
    Pokemon chosenPokemon;

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
```



While creating Professor Oak's class you will need to pass Player Object by reference and for that you have to use a special operator** &**. 

You will learn how to create Objects later in this section and why you have to use this symbol in the next section, but the code won’t work properly if you don’t use it here. So go along with it and we will discuss in depth about it in the next content.



For now, wherever you will be told to pass player object by reference just use `**Player &player**`** **



> **TODO: Professor Oak Class**
> ✅ Create an empty class in the `**Main.cpp**` file for ProfessorOak after the Player class and before the main function.
> ✅ In the ProfessorOak class add the Properties that ProfessorOak will have: name - `**std::string p_name**`

> ✅ Create functions `**void greetPlayer()**` and `**void offerPokemonChoices()**`inside the Player class. Both the functions will take reference to Player object `**Player &player**`as an argument.

> ✅ Write the part [ // Introduction by the Professor] inside the function `**void greetPlayer()**`

> ✅ Write the part [ // Taking player name as input] and [ // Presenting Pokemon choices] inside the function `**void offerPokemonChoices()**`



Click here to see ProfessorOak class```cpp
class ProfessorOak {
// Attributes
public:
string name;

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
cout << name << ": Choose wisely...\n"; std::cout << "1. Charmander - The fire type. A real hothead!\n"; 
cout << "2. Bulbasaur - The grass type. Calm and collected!\n"; 
cout << "3. Squirtle - The water type. Cool as a cucumber!\n"; 

int choice; 
cout << name << ": So, which one will it be? Enter the number of your choice: "; 
cin >> choice; 
player.choosePokemon(choice);
     }
};
```





Nice you are doing good

![Image](/Full-Stack-Game-Development/images/53f94ff259bdfa5a.gif)



Now that you have created individual classes for each of the objects in your pokemon game 

The next step is creating Objects for each of the classes and use their data members and methods to run the game.



> 💡**PRO-TIP: **

> 

> Data member: Data members of a class are the attributes that you declare within the class. For example, in the Pokemon class `name`, `type` and `health` are the data members of the Pokemon class

> 

> Methods: Methods of a class are the functions that you declare inside the class. For example, `attack()` is the method of the Pokemon class.



But how will you create the objects?

It's very easy. 

The syntax for creating Objects is `name_of_class name_of_object;`



For example, if you create an Object of Pokemon named Pikachu, you will create it like this

```cpp
//You don't need to write it anywhere. 
//This is Just for reference so that when you have to create Objects below in the main function TODO, You will be able to
Pokemon Pikachu;
```



How will you access the data members and methods of an Objects?

Using the `.` operator

The syntax for accessing data members and methods is `name_of_objects.name_of_members/methods`



If you want to access the name of the Pikachu object created above and assign Pikachu to it, you have to do it like this:

```cpp
//You don't need to write it anywhere. 
//This is Just for reference so that when you have to create Objects below in the main function TODO, You will be able to
Pikachu.name = "Pikachu"
```



> **TODO: Creating Objects**

> ✅ Remove everything that you have written till now in the main function.
> ✅ Create Objects for the Player, ProfessorOak and Pokemon as player, professor and placeholderPokemon in the main function

> ✅ Assign values to the data members of `PlaceholderPokemon `using `.` operator. Give name = Pikachu, type = ELECTRIC and health = 40` `

> ✅ Assign values to the data members of `Player `using `.` operator. Give name =Trainer

> ✅ Assign values to the data members of `ProfessorOak `using `.` operator. Give name = Professor Oak

> ✅ Call the methods `greetPlayer()` and `offerPokemonChoices()` of professor by passing the player into the function

> ✅ Print the name of the player and the name of the pokemon he chooses



Click here to see the Objects```cpp
int main() {

    // Creating Objects of ProfessorOak, Pokemon and Player class
    ProfessorOak professor; 
    Pokemon placeholderPokemon;
    Player player;

    //Assigning Values to placeholderPokemon attributes
    placeholderPokemon.name = "Pikachu";
    placeholderPokemon.type = PokemonType::ELECTRIC;
    placeholderPokemon.health = 40;

    //Assigning Values to player attributes
    player.name = "Trainer";

    //Assigning Values to ProfessorOak attributes
    professor.name = "Professor Oak";

    // Greet the player and offer Pokemon choices 
    professor.greetPlayer(player); 
    professor.offerPokemonChoices(player); 

    // Conclude the first chapter 
    cout << "Professor Oak: " << player.chosenPokemon.name << " and you, " << player.name << ", are going to be the best of friends!\n"; 
    cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\n";


return 0;

}
```



**Click here to see the entire code**```cpp
#include<iostream>
#include<string>
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

    // Created 2 constructors
    Pokemon(){

    }

    Pokemon(string p_name, PokemonType p_type, int p_health){
        name = p_name;
        type = p_type;
        health = p_health;
    }

    // Method to simulate attacking (just for demonstration)
    void attack() { std::cout << name << "attacks with a powerful move!\n"; }
};

// Player class definition
class Player {
public:
    // Attributes
    string name;
    Pokemon chosenPokemon;

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
    // Attributes
    public:
    string name;

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

    // Creating Objects of ProfessorOak, Pokemon and Player class
    ProfessorOak professor; 
    Pokemon placeholderPokemon;
    Player player;

    //Assigning Values to placeholderPokemon attributes
    placeholderPokemon.name = "Pikachu";
    placeholderPokemon.type = PokemonType::ELECTRIC;
    placeholderPokemon.health = 40;

    //Assigning Values to player attributes
    player.name = "Trainer";

    //Assigning Values to ProfessorOak attributes
    professor.name = "Professor Oak";

    // Greet the player and offer Pokemon choices 
    professor.greetPlayer(player); 
    professor.offerPokemonChoices(player); 

    // Conclude the first chapter 
    cout << "Professor Oak: " << player.chosenPokemon.name << " and you, " << player.name << ", are going to be the best of friends!\n"; 
    cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\n";


return 0;

}
```
