# Initial Instructions


---

> **Make sure you have checked out the **`Feature_7_Inheritance` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_7_Inheritance` **to previous branch **`Feature_6_Battle_Loop `**if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



You’ve come a long way in building your Pokémon game, 

and now it’s time to make your code more secure and maintainable. 



Up until now, 

your Pokémon class and its attributes have been publicly accessible, 

which has been convenient but not ideal for keeping your code safe from unintended changes.



In this assignment, 

you’ll learn how to protect your data using abstraction, 

by adjusting access modifiers and adding getter/setter methods to control access. 



This will help you maintain the integrity of your game, 

while still allowing other classes to interact with your Pokémon in a controlled manner.




---



### Steps to Complete the Assignment:



- **Protect the Core: Update the Pokémon Class**



- - Go to your `Pokemon.hpp` file.
  - Change the attributes `name`, `type`, `health`, `maxHealth`, and `attackPower` to be protected. This will restrict access to these attributes to the Pokémon class and its subclasses, keeping them safe from unintended changes by other classes.



- **Control Access with Getters and Setters: Implement Security Layers**



- - Add public getter and setter methods for attributes that need to be accessed or modified from outside the class. These methods will help manage how other parts of the code interact with the Pokémon’s internal state.



- **Strengthen Your Unique Abilities: Make Special Moves Private**



- - Open the header files for Pikachu, Zubat, Pidgey, and Caterpie (`Pikachu.hpp`, `Zubat.hpp`, `Pidgey.hpp`, `Caterpie.hpp`).
  - Set the unique move methods (`thunderShock()`, `supersonic()`, `wingAttack()`, `bugBite()`) to be private. This will ensure these moves are only callable within their respective classes or through controlled interfaces.





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
