# Initial Instructions


---

> **Make sure you have checked out the **`Feature_6_Battle_Loop` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_6_Battle_Loop` **to previous branch **`Feature_5_Wild_Pokemons` **if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



**Introduction:**

While exploring deeper into the forest, 

you come across Ash and his Charizard, 

looking exhausted from their recent battles. 



Ash approaches you with a request. 

“Charizard’s taken some heavy hits." 

"I need to find a way to manage his health between battles and ensure his attacks are stronger." 

"Can you help me?”



Ash’s challenge is a perfect opportunity to enhance your game’s mechanics. 

Your task is to implement a system that manages Pokémon health and damage more effectively, 

ensuring that every battle carries weight.




---



**Quest Objectives:**



- **Restore Health Between Battles:Your Task:**



- - Pokémon need to recover after battles, just like Charizard does. Implement a method to fully restore a Pokémon’s health, simulating a visit to the PokéCenter.
- - Add a `heal()` method in the `Pokemon` class that restores the Pokémon’s health to its maximum value (`maxHealth`).
  - Implement the `heal()` method in `Pokemon.cpp`.



- **Enhance Attack Capabilities:Your Task:**



- - Different Pokémon have varying strengths. Introduce an attribute to determine the damage a Pokémon can inflict in battle.
- - Introduce an `attackPower` attribute in the `Pokemon` class to represent attack strength.
  - Update the `attack()` method to use `attackPower` for damage calculation.




---



**Steps to Complete the Quest:**



- **Add the Healing Mechanic:**



- - In `Pokemon.hpp`, add a `heal()` method that sets the current health of the Pokémon to its maximum (`maxHealth`).



- **Introduce Attack Power:**
- - Add the `attackPower` attribute in the `Pokemon` class in `Pokemon.hpp`.
  - Modify the `attack()` method in `Pokemon.cpp` to use `attackPower` when calculating damage dealt to the opponent.



- **Integrate Healing into the Game:**
- - Update the game loop to allow players to heal their Pokémon at the PokéCenter, ensuring they are ready for the next battle.




---



With Charizard back at full strength, 

Ash thanks you. 

“This is exactly what Charizard needed." 

"Now we can keep pushing forward without worrying about every battle taking its toll." 

"You’ve really made a difference!”





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
