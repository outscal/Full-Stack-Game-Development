Before starting today's topic, first, answer my simple question.



```cpp
switch(colour){
        case 1:
        cout << "I am red" << endl;

        case 2:
        cout << "I am green" << endl;

        default:
        cout << "I am Black" << endl;
    }
```



The above switch case represents the value of colour.

If the colour is 1, that means it is red.



In the above example, there are only 3 colours.

But suppose you are developing a project with 100 different colours,

would it be feasible to represent all the colours with integers?

In that case, you would have to keep the mapping of numbers to the colours in a notepad.



And If I had used something like colour = "red", directly in place of colour = 1,

do you think that will be much more neat and readable?



Let me show you an example of this for a better understanding

```cpp
switch(colour){
    case red:
    cout << "I am red" << endl;

    case green:
    cout << "I am green" << endl;

    default:
    cout << "I am Black" << endl;
}
```



> **NOTE:** The above code is not meant to be copy-pasted and run. It is just an example for now.





But how can you achieve this?



As far as I know, in C++, you can't use string type in switch statements.

But don't worry, guys. You still have an option left.



There is a topic known as ***Enums*** that can help you do this.





# Enums


---

An enum is a user-defined data type.



> 💡**PRO TIP:**
> Using the multiple inbuilt data types like int, string, bool..., You can make your own data type which are known as user-defined



If you go to buy a new car, you will be given a booklet with the colour options.

You can consider that booklet as an enum.

It will have multiple colours with the constant names.



In a similar way, the values inside enums are constant.

Those values can be later used to assign to the variables.



> **NOTE:** Values inside enums are nothing but just ***integers*** with some name assigned to them.





```cpp
enum menu{
        pizza,
        burger,
        fries
    };
```



A restaurant only serves three items that are listed above.

If a customer arrives and wants a burger, then the code will look like



```cpp
order_1 = burger;
```



> **TODO: Enum**
> **✅**Go to the following Link:** Online Compiler**
> **✅**Create an enum with name `**menu**` before the `main()` function just like above.
> **✅**Add `**PIZZA**`, `**BURGER**`, `**FRIES**` inside it
> **✅**Inside `**main()**` function, create a variable of type `**menu**`
> **✅**assign each enum value one by one and print out the variable in the console



*What is the answer? the name of the enum value or an integer?*



## why enums are useful


---

As I mentioned above, 

enum helps programmers to keep the related data together.





Enum also serves one another functionality.

If the variable is defined of some enum type,

only the values that are present in the enum can be assigned to it.



This means that if a customer chooses to eat pasta in the above example of ***menu***, 

the code will not allow him to do so.

The customer is only allowed to choose from the given options.





This protects the chances of errors in the code. Wonder HOW?

Let's consider an example of subway suffers.



There can be only 2 states in this game.

Either the player will be running, or the player will be standing still.

```plain
// Running = 1
// Standing = 2
```



Suppose, by some mistake, the programmer writes `*state*` = 3 or 4 or something else.

It will definitely throw an error during the run time.



But If the programmer had used enum to keep the state of the game,

code won't even allow him to assign some random value in the variable.





# Coding Time


---

> **TODO: Enum**
> **✅**Create an enum with name **PokemonChoice** before the `main()` function
> **✅**Add Charmander, Bulbasaur and Squirtle inside it
> **✅**Also add 'InvalidChoice' value, this will be used to initiate the variable
> **✅**Create a variable **chosen_pokemon** of **PokemonChoice** enum type inside the `main()` function
> **✅**Assign 'InvalidChoice' value to this variable





Solution```cpp
#include<iostream>
#include<string>
using namespace std;

enum PokemonChoice {
    Charmander,
    Bulbasaur,
    Squirtle,
    InvalidChoice
};

int main(){

    PokemonChoice chosen_pokemon = InvalidChoice;
    // Some more code here
    return 0;
}
```





# Internal working of Enums


---

Ever wonder how enums work at the backend?

In the above code, you wrote `PokemonChoice chosen_pokemon = InvalidChoice;`



On the LHS, a variable is declared of type PokemonChoice with the name 'chosen_pokemon',

but what is there on the RHS?



Is it a string? I guess not, as strings are declared between quotation marks.

Is it an integer? Obviously not.



Then what are these values inside the enums?

Let's try to understand by some hit and try method.



Example```cpp
#include<iostream>
using namespace std;

enum PokemonChoice {
    Charmander,
    Bulbasaur,
    Squirtle,
    InvalidChoice
};

int main(){

    PokemonChoice chosen_pokemon = InvalidChoice;
    cout << chosen_pokemon << endl;

    return 0;
}
```


Output - 

```plaintext
3
```



What? 3?

I think there is some problem. 

Let’s change chosen_pokemon to Bulbasaur and then see





Example```cpp
#include<iostream>
using namespace std;

enum PokemonChoice {
    Charmander,
    Bulbasaur,
    Squirtle,
    InvalidChoice
};

int main(){

    PokemonChoice chosen_pokemon = Bulbasaur;
    cout << chosen_pokemon << endl;

    return 0;
}
```



Output -

```plain
1
```



Now 1? But HOW?



So, the internal working of enums is a little different than what you see.



You are using naming conventions to make the code more readable.

But the computer considers those values as integers.



That means, 

```plain
Charmander = 0
Bulbasaur = 1
Squirtle = 2
InvalidChoice = 3
```





# Final Code


---

> NOTE: Ternary operator has been used in the below code, if you don't remember it, revise it [here](https://outscal.com/course/full-stack-game-development/text-based-adventure-game/conditionals-and-operators-in-c/ternary-operator)



There can be a few lines of code that are different from the previous codes.

Hence, look at the code below carefully and sync with it.





Code till now```cpp
#include <iostream>
#include <string>
using namespace std;

// Define an enum for Pokemon choices
enum PokemonChoice {
    Charmander,
    Bulbasaur,
    Squirtle,
    InvalidChoice
};

int main() {
    // Variables to store player name and chosen Pokemon
    string player_name;
    PokemonChoice chosen_pokemon = InvalidChoice; // Default to an invalid choice

    // Introduction by the Professor
    cout << "Professor Oak: Hello there! Welcome to the world of Pokemon!\n";
    cout << "Professor Oak: My name is Oak. People call me the Pokemon Professor!\n";
    cout << "Professor Oak: But enough about me. Let's talk about you!\n";

    // Taking player name as input
    cout << "Professor Oak: First, tell me, what’s your name?\n";
    cin >> player_name;

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
            chosen_pokemon = Charmander;
            break;
        case 2:
            chosen_pokemon = Bulbasaur;
            break;
        case 3:
            chosen_pokemon = Squirtle;
            break;
        default:
            chosen_pokemon = InvalidChoice;
            break;
    }

    // Respond based on the chosen Pokemon
    switch(chosen_pokemon) {
        case Charmander:
            cout << "Professor Oak: A fiery choice! Charmander is yours!\n";
            break;
        case Bulbasaur:
            cout << "Professor Oak: A fine choice! Bulbasaur is always ready to grow on you!\n";
            break;
        case Squirtle:
            cout << "Professor Oak: Splendid! Squirtle will keep you cool under pressure!\n";
            break;
        default:
            cout << "Professor Oak: Hmm, that doesn't seem right. Let me choose for you...\n";
            chosen_pokemon = Charmander; // Default to Charmander if invalid choice
            cout << "Professor Oak: Just kidding! Let's go with Charmander, the fiery dragon in the making!\n";
            break;
    }

    // Concluding the first chapter
    cout << "Professor Oak: " << (chosen_pokemon == Charmander ? "Charmander" : chosen_pokemon == Bulbasaur ? "Bulbasaur" : "Squirtle")
              << " and you, " << player_name << ", are going to be the best of friends!\n";
    cout << "Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokemon!\n";

    return 0;
}
```
