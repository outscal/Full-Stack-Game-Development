![pro](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_29_2024__10_53_24.png)





Do you remember that nostalgic moment when the player meets Professor Oak?

I'm sure that moment is in the hearts of those who have played this game.



That feeling of excitement of playing a new game. 

That curiosity about what you will be doing inside it. 

That feeling is everything that makes us all play such games.



So now it's time to think about how you would like to start your game.



Would you like to recreate that nostalgic moment for players?

Where Professor Oak meets you and presents you with three options to choose your first Pokémon?

I guess that will be a fantastic start for your game.



> **NOTE:** Just a glimpse of the game for those who have never played it.
> 
> 🟡 At the beginning of the game, there is a person named Professor Oak and there is a player
> 🟡 Both of them meet and professor offers 3 options of Pokémon to the player, and then he needs to choose one of them



![c++](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_29_2024__11_21_02.png)



Can you think of any way to implement it? 

You need to provide the player with a few options of Pokémon, and then he would select one of them.



Think a little bit on this.

How would you implement this in your code?





I guess you will be able to do so easily using `cin` and `cout`. 

Your game will store all the inputs by the player and act accordingly.



Also, your game will print the `cout` statements in such a way,

so that it looks like the Player is interacting with Professor Oak.





So first, you need to print an introductory message from the professor's side.

Then, give them a list of Pokémon and ask them to choose one of them.

Once the player inputs some choice, capture that and make your game behave accordingly.



Now, It's time for you to do some code and implement above mentioned task.



Example```cpp
#include <iostream>
using namespace std;

int main() {
		cout << "Welcome to the world of Pokémon! I am Professor Oak.\n";
		cout << "You can choose one of the following Pokémon:\n";
		cout << "1. Bulbasaur\n2. Charmander\n3. Squirtle\n";
		cout << "Which Pokémon would you like to choose? Enter the number: ";

		int choice;
		cin >> choice;

    return 0;
}
```





Since you have completed this task, let's move further to process the player's input.



First, Let's give the player a confirmation message that his input has been recognized.

We can do so by printing the Pokemon name which he has chosen.



In the above example, let's say the player chooses 2nd type of Pokémon.

And now you want to print on the screen, "You chose Charmander! A fiery choice".



How would you do this? 

By just writing a `cout` statement as you did above? I guess NO



Because if you do that, "Charmander" will be printed even when the player chooses Pokemon 1 or 3.





So, how would you tackle this?

Hmmmm, remember those conditional statements?





![shocked](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_27_2024__11_05_23.png)





YES, you are guessing it right. We are going to use that here. 



In the above example, there were 3 choices, meaning you must have 4 conditions here.

Three for the choices and one for some invalid input.



> **TODO:**
> ✅Take the input from the player and store it in ***choice*** variable
> ✅Create a sequence of if-else statements
> ✅For *choice* = 1, print "You chose Bulbasaur! A wise choice.\n"
> ✅For *choice* = 2, print "You chose Charmander! A fiery choice.\n"
> ✅For *choice* = 3, print, "You chose Squirtle! A cool choice.\n"
> ✅For some other *choice*, print "Invalid choice. Please restart the game.\n"



Solution```cpp
		int choice;
		cin >> choice;
		
		if (choice == 1) {
        cout << "You chose Bulbasaur! A wise choice.\n";
    } 
    else if (choice == 2) {
        cout << "You chose Charmander! A fiery choice.\n";
    } 
    else if (choice == 3) {
        cout << "You chose Squirtle! A cool choice.\n";
    } 
    else {
        cout << "Invalid choice. Please restart the game.\n";
    }
```





Now, your task is to merge both the code, the introductory code and this processing of the choice.



Code until this point```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "Welcome to the world of Pokémon! I am Professor Oak.\n";
	cout << "You can choose one of the following Pokémon:\n";
	cout << "1. Bulbasaur\n2. Charmander\n3. Squirtle\n";
	cout << "Which Pokémon would you like to choose? Enter the number: ";

	int choice;
	cin >> choice;
    
    if (choice == 1) {
        cout << "You chose Bulbasaur! A wise choice.\n";
    } 
    else if (choice == 2) {
        cout << "You chose Charmander! A fiery choice.\n";
    } 
    else if (choice == 3) {
        cout << "You chose Squirtle! A cool choice.\n";
    } 
    else {
        cout << "Invalid choice. Please restart the game.\n";
    }
    
    return 0;
}
```
