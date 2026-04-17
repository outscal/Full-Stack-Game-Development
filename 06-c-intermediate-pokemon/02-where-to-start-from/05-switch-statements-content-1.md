As a programmer, you should always be careful when writing code. 

It should always be clean and understandable.

A few tasks can be achieved in many ways, so you must always choose the best way.



In the previous lesson, you have written conditional statements (if-else) to process the player's input. 

Suppose there are 50 choices to choose a Pokemon. Would you proceed with the same approach? 

Will you write if and else statements 50 times?



What if I tell you there is a more structured way to handle multiple choices?

FEELING EXCITED?



Hold on tight with me. We are going to learn a new topic today, the ***Switch-Statements***





# Switch Statements


---

Before jumping into the details, let me show you an example.



Example```cpp
#include<iostream>
using namespace std;

int main(){
    int a = 2;

    switch(a){
        case 1:
        cout << "1 time hello" << endl;
        break;

        case 2:
        cout << "2 time hello" << endl;
        break;

        case 3:
        cout << "3 time hello" << endl;
        break;

        default:
        cout << "Invalid" << endl;
    }

    return 0;
}
```


Look at the above code and try to understand what is happening here.

It's output will be.



```plain
2 time hello
```



Now, let's move to the explanation part of switch statements

It is a cleaner and readable way to replace if-else conditions and helps de-cluttering the code.



For the sake of formal definition, let me define switch statements. 

Switch statements are the control flow of statements that allows a variable to be tested for equality against a list of values, each associated with a block of code.



Little confused? (even I don't like formal definitions. HAHA)

For now, just understand that switch statements are used for multiple if-else conditions. 



Let's see the syntax to understand it more clearly.





# Syntax


---

```cpp
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```



**Expression:** It refers to the variable that we want to equate in each condition.

You can relate it to the 'choice' variable in the previous lesson.



**Cases:** Focus on 'case x' and 'case y'. Here, it equates the value of 'expression' with 'x' and 'y'.

Like in the previous lesson, you were equating the value of 'choice' to 1, 2 and 3



**Default:** It refers to the code we want to execute if the value of 'expression' does not match any of the above cases.

It is similar to the 'else' case we used at the end of 'if-else statements' in the previous lesson.



**Break:** Before going to learn the importance of break, let's first see the below example

In the example of the switch case mentioned above, try to remove all the ***break*** keyword from it



Example```cpp
#include<iostream>
using namespace std;

int main(){

    int a = 1;

    switch(a){
        case 1:
            cout << "1 time hello" << endl;

        case 2:
            cout << "2 time hello" << endl;

        case 3:
            cout << "3 time hello" << endl;

        default:
            cout << "Invalid" << endl;
    }

    return 0;
}
```



It's output will be

```plain
1 time hello
2 time hello
3 time hello
Invalid
```



WHAT IS THIS? 

It should have been just "1 time hello" because 'a' is equal to 1. But why is it printing everything?

I think my laptop did not get enough sleep, still having last night hangover 😂



Let me change the value of 'a' to 2. Now, I am getting

```plain
2 time hello
3 time hello
Invalid
```



AHH WHAT???

Still having the same issue.



OHHKAYY.

That means if the condition gets hit, the code will continue to execute until it finds the 'break' keyword.

So today, we have seen why we should never forget to apply 'break' in switch statements.





# Coding Time


---

Remove all the if-else conditions and try using switch statements instead. 

Give yourself some time to implement it.



Do one more thing.

In the earlier code, if the players had given invalid input, we asked them to restart the game. 



So, let's change this a bit.

Write the code so that if the player enters something, a random Pokémon will be assigned to him, and he can continue the game.



> **TODO: Apply Switch Statements**
> ✅Create a switch statement for the ***choice*** of the player
> ✅Keep 3 cases for 3 choices, and a default case
> ✅Add cout statement for each choice that the player has made
> ✅Store the choosen pokemon type in a variable named ***chosen_pokemon***
> ✅Assign ***Pikachu*** in the default case



I think you have tried doing the code.

If your code runs without any error, it's perfect. Otherwise, I am always here to help you out. 

I have provided the code snippet below. Try to match it with your code and see what you have missed.



Example```cpp
switch (choice) {

case 1:
    chosen_pokemon = "Charmander";
    cout << "Professor Oak: A fiery choice! Charmander is yours!\n";
    break;

case 2:
    chosen_pokemon = "Bulbasaur";
    cout << "Professor Oak: A fine choice! Bulbasaur is always ready to grow on you!\n";
    break;

case 3:
    chosen_pokemon = "Squirtle";
    cout << "Professor Oak: Splendid! Squirtle will keep you cool under pressure!\n";
    break;

default:
    cout << "Professor Oak: Hmm, that doesn't seem right. Let me choose for you...\n";
    chosen_pokemon = "Pikachu"; // Default if no valid choice is made
    cout << "Professor Oak: Just kidding! Let's go with Pikachu, the surprise guest!\n";
    break;

}
```



# Final Code


---

I think you are ready with your final code. 



I have made a few minor changes to the code. 

You did not ask for the player's name in the previous lesson's final code, so I recommend implementing it.



I have also added some more cout statements from Professor Oak.

You can change these statements as you like according to your design and preferences.



It is your game after all!



Code until this point```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
  // Variables to store player name and chosen Pokemon
  string player_name;
  string chosen_pokemon;

  // Introduction by the Professor
  cout << "Professor Oak: Hello there! Welcome to the world of Pokemon!\n";
  cout << "Professor Oak: My name is Oak. People call me the Pokemon "
               "Professor!\n";
  cout << "Professor Oak: But enough about me. Let's talk about you!\n";

  // Taking player name as input
  cout << "Professor Oak: First, tell me, what’s your name?\n";
  cin >> player_name;

  cout << "Professor Oak: Ah, " << player_name
            << "! What a fantastic name!\n";
  cout << "Professor Oak: You must be eager to start your adventure. But "
               "first, you’ll need a Pokemon of your own!\n";

  // Presenting Pokemon choices
  cout << "Professor Oak: I have three Pokemon here with me. They’re all "
               "quite feisty!\n";
  cout << "Professor Oak: Choose wisely...\n";
  cout << "1. Charmander - The fire type. A real hothead!\n";
  cout << "2. Bulbasaur - The grass type. Calm and collected!\n";
  cout << "3. Squirtle - The water type. Cool as a cucumber!\n";

  int choice;
  cout << "Professor Oak: So, which one will it be? Enter the number of "
               "your choice: ";
  cin >> choice;

  // Store the chosen Pokemon based on user input
  switch (choice) {
  case 1:
    chosen_pokemon = "Charmander";
    cout << "Professor Oak: A fiery choice! Charmander is yours!\n";
    break;

  case 2:
    chosen_pokemon = "Bulbasaur";
    cout << "Professor Oak: A fine choice! Bulbasaur is always ready to "
                 "grow on you!\n";
    break;

  case 3:
    chosen_pokemon = "Squirtle";
    cout << "Professor Oak: Splendid! Squirtle will keep you cool under "
                 "pressure!\n";
    break;
    
  default:
    cout << "Professor Oak: Hmm, that doesn't seem right. Let me choose "
                 "for you...\n";
    chosen_pokemon = "Pikachu"; // Default if no valid choice is made
    cout << "Professor Oak: Just kidding! Let's go with Pikachu, the "
                 "surprise guest!\n";
    break;
  }

  // Concluding the first chapter
  cout << "Professor Oak: " << chosen_pokemon << " and you, "
            << player_name << ", are going to be the best of friends!\n";
  cout << "Professor Oak: Your journey begins now! Get ready to explore "
               "the vast world of Pokemon!\n";

  return 0;
}
```
