In the previous lesson,

you have declared the structure,

to implement multiple moves of Pokemon.



Now, in this lesson, 
you will define that structure.



But before this,

first, answer the question that I asked you,

at the end of the *Creating Battle Dialogues* lesson.



Did you find any structural issues in your code?

Let me give you a hint.



There is a basic rule of programming,

that you should not write any repetitive code.

In the programming world,

it is known as **DRY principle (Do Not Repeat Yourself)**



Remember those repetitive dialogues, 

that you implement for each type of Pokemon?



Let me show you an example of it.



Charmander```cpp
cout << name << " used FLAME THROWER!\n";
N_Utility::Utility::waitForEnter();

cout << "...\n"; 
N_Utility::Utility::waitForEnter();

target->takeDamage(attackPower);

if (target->isFainted())
    cout << target->name << " fainted!\n";
else
    cout << target->name << " has " << target->health << " HP left.\n";
N_Utility::Utility::waitForEnter();
```



All the types of Pokemon have the same code.

So, making a single code for all of them will be a better approach.



Now, let's move to the coding part.





# Coding Time


---

First of all, bring the battle dialogues in `Pokemon` Class.

But not like the way it is written in the above example of Charmander.



You should create a separate function for each individual task.



Let me show you, how you can do it.



```cpp
void Pokemon::selectAndUseMove(Pokemon* target){
    // Show all the available moves

    // Input player's choice

    // Execute the move
}
```



First, you need to print a list of all the moves on the screen.

Then, the Player would select one of the moves,

then you need to execute that selected move.



## Show Available Moves


---

Below is the example of a function,

which will print all available moves.



```cpp
void Pokemon::printAvailableMoves(){
    cout << name << "'s available moves:\n";
    
    // List out all moves for the player to choose from
    for (size_t i = 0; i < moves.size(); ++i) {
      cout << i + 1 << ": " << moves[i].name << " (Power: " << moves[i].power << ")\n";
    }
}
```



## Input Player's Choice


---

Now, it's time to take the Player's input.



```cpp
int Pokemon::selectMove(){
    // Ask the player to select a move
    int choice;
    cout << "Choose a move: ";
    cin >> choice;

    // Validate the choice
    while (choice < 1 || choice > static_cast<int>(moves.size())) {
      cout << "Invalid choice. Try again: ";
      cin >> choice;
    }

    return choice;
}
```





Since the Player has chosen the move,

now it's time to execute it.



## Execute the Move


---



```cpp
void Pokemon::useMove(Move selectedMove, Pokemon* target){
    cout << name << " used " << selectedMove.name << "!\n";
    attack(selectedMove, target);
    
    N_Utility::Utility::waitForEnter();

    cout << "...\n"; 
    N_Utility::Utility::waitForEnter();
    
    if (target->isFainted())
      cout << target->name << " fainted!\n";
    else
      cout << target->name << " has " << target->health << " HP left.\n";
}
```



Now, you need to update the `selectAndUseMove` method.

```cpp
void Pokemon::selectAndUseMove(Pokemon* target){
    // Show all the available moves
    printAvailableMoves();

		 // Input player's choice
    int choice = selectMove();
    Move selectedMove = moves[choice-1];

    // Execute the move
    useMove(selectedMove, target);
}
```

At the end, your `Pokemon.cpp` should look like something similar to the given below.



Pokemon.cpp```cpp
........
void Pokemon::selectAndUseMove(Pokemon* target){
    printAvailableMoves();

    int choice = selectMove();
    Move selectedMove = moves[choice-1];
    
    useMove(selectedMove, target);
}

.....

void Pokemon::printAvailableMoves(){
    cout << name << "'s available moves:\n";
    
    // List out all moves for the player to choose from
    for (size_t i = 0; i < moves.size(); ++i) {
      cout << i + 1 << ": " << moves[i].name << " (Power: " << moves[i].power << ")\n";
    }
}

.......

int Pokemon::selectMove(){
    // Ask the player to select a move
    int choice;
    cout << "Choose a move: ";
    cin >> choice;

    // Validate the choice
    while (choice < 1 || choice > static_cast<int>(moves.size())) {
      cout << "Invalid choice. Try again: ";
      cin >> choice;
    }

    return choice;
}

......

void Pokemon::useMove(Move selectedMove, Pokemon* target){
    cout << name << " used " << selectedMove.name << "!\n";
    attack(selectedMove, target);
    
    N_Utility::Utility::waitForEnter();

    cout << "...\n"; 
    N_Utility::Utility::waitForEnter();
    
    if (target->isFainted())
      cout << target->name << " fainted!\n";
    else
      cout << target->name << " has " << target->health << " HP left.\n";
}

.......
```





Since you have implemented battle dialogues logic in the base class `Pokemon,`

now, it's time to remove the repetitive part,

from individual classes of different types of **Pokemon**.



I will show you an example of Balbasaur,

and for the rest of the Pokemon,

I am sure you will be able to do it independently.



Things that should be considered here

- Send a vector of `moves` in the `Pokemon` constructor from the child class
- Update the `attack()` function in the child class





Bulbasaur.hpp```cpp
....
class Bulbasaur : public Pokemon {
public:
    Bulbasaur();
    void attack(Pokemon* target) override; 
};
......
```



Bulbasaur.cpp```cpp
.......
Bulbasaur::Bulbasaur()
: Pokemon("Bulbasaur", PokemonType::GRASS, 110, {
    Move("VINE WHIP", 25),
    Move("TACKLE", 10)
}) {}

void Bulbasaur::attack(Pokemon* target){
    selectAndUseMove(target);
}
.....
```



Now, it's your job to remove the repetitive code,

from the rest of the `Pokemon` child classes.



Congratulations! 🥳

You have successfully improved the structure of your code,

removed the repetitive part.
