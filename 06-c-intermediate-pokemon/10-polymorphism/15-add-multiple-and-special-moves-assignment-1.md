# Initial Instructions


---

> **Make sure you have checked out the **`Feature_9_Polymorphism` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_9_Polymorphism` **to previous branch **`Feature_8_Pointers `**if not already created previously.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



Great work so far! 



Now, it’s time to bring more depth to your Pokémon battles, 

by adding multiple moves and special effects. 



This assignment will guide you through making these changes step-by-step, 

enhancing the gameplay experience.



## **1. Structuring Moves: Creating a Move System**


---

We want to give each Pokémon multiple moves. 

To achieve this, 

you'll need to create a `Move` structure that will store the move's name and power.



**Tasks:**

- - Create a `Move` struct in `Move.hpp` to store each move’s details.
  - Declare the `Move` struct in the `Pokemon.hpp` file.
  - Under the `Pokemon` class, declare a vector to hold all the moves a Pokémon can perform.
  - Declare a new function, `selectAndUseMove()`, which will handle move selection during battles.



## **2. Implementing Move Functions**


---

Define the functions to handle the move selection and execution process, 

allowing the player to interact with their Pokémon’s moves during battles.



**Tasks:**

- - **Print Available Moves**: 
  - - Implement a function that displays all moves a Pokémon can use.
  - **Select a Move**: 
  - - Create a function that allows the player to choose a move from the list.
  - **Use the Selected Move**: 
  - - Implement the logic to execute the chosen move and display the appropriate battle dialogues.



## **3. Removing Repetitive Code and Updating Pokémon Classes**


---

Consolidate the repetitive battle dialogues into the `Pokemon` class, 

and update each individual Pokémon class to use the new system.



**Tasks:**

- - Update each Pokémon class to use the new `selectAndUseMove()` function.
  - Pass a vector of moves to each Pokémon's constructor from the child classes.
  - Update the `attack()` function in each Pokémon class to handle the move selection process correctly.



## **4. Implement Special Moves for Each Pokémon**


---

Now that basic moves are set up, 

let’s add special moves with unique effects to make each Pokémon stand out.



**Tasks:**

- - Implement special moves for each Pokémon by defining the unique effects in their `attack()` function.
  - Ensure each special move has distinct behavior, like additional damage, healing effects, or other unique battle conditions.



**Special Moves Details:**



- **Caterpie**: 
- - Special Move - "STICKY WEB" reduces the target's attack power.
- **Charmander**: 
- - Special Move - "BLAZING CHARGE" causes recoil damage to itself.
- **Pidgey**: 
- - Special Move - "GUST" has a chance to end the battle by blowing away the opponent.
- **Pikachu**: 
- - Special Move - "THUNDER BOLT" has a chance to miss.
- **Squirtle**: 
- - Special Move - "RAPID SPIN" hits the opponent multiple times.
- **Zubat**: 
- - Special Move - "LEECH LIFE" restores health based on the damage dealt.





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
