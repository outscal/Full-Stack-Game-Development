# Initial Instructions


---

> **Make sure you have checked out the **`Feature_4_Code_Organization` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_4_Code_Organization` **to previous branch **`Feature_3_Main_Quest` **if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!




Now that we’ve separated the Player class, 

it’s time to handle the Pokémon class. 

Let’s break it down step by step:




---



**Tasks**

1. **Create a Header File for Pokémon Class:**
2. - Let’s start by creating a new header file. Name it `Pokemon.hpp`.
  - In this file, declare the Pokémon class and its members. This is where you outline what the Pokémon class can do.
3. **Create a Source File for Pokémon Class:**
4. - Next, create a new source file named `Pokemon.cpp`.
  - Include the `Pokemon.hpp` header file inside this source file.
  - Define all the methods of the Pokémon class here. Use the `::` operator to connect each method to the Pokémon class.
5. **Include Pokémon in Player Class:**
6. - Now, make sure that your Player class knows about the Pokémon class.
  - In `Player.hpp`, include the Pokémon header file by adding `#include "Pokemon.hpp"` at the top.




---



This will help Player class to recognize Pokémon and keep the code organized. 

Check if everything runs smoothly—your game should now be free of errors related to Pokémon and Player classes!



Keep pushing forward, 

you’re doing awesome!





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
