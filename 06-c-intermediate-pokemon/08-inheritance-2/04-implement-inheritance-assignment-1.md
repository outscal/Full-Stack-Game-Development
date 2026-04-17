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


In this assignment, 

you will implement inheritance to create new Pokémon classes with unique abilities. 



This will help you extend the existing Pokémon class, 

adding variety and depth to your game by introducing Pokémon like Pikachu, Pidgey, Caterpie, and Zubat with their own unique moves.



### **Objectives:**



- **Create Pikachu Class:**



- - Create a separate header file named `Pikachu.hpp` in the path `include/Pokemon/Pokemons/`.
  - Include the necessary headers (`Pokemon.hpp`) and add `#pragma once`.
  - Define the `Pikachu` class that inherits from the `Pokemon` class.
  - Add a private data member `thunderShockDamage` to define Pikachu's unique attack power.
  - Declare a public constructor and the method `thunderShock()` that takes a reference to another `Pokemon` object.



- **Implement Pikachu Class:**



- - Create a separate source file named `Pikachu.cpp` in the path `src/Pokemon/Pokemons/`.
  - Include the required headers (`Pikachu.hpp`, `PokemonType.hpp`, and `<iostream>`).
  - Implement the constructor and define the `thunderShock()` method, which prints a statement about Pikachu's attack and applies damage to the target Pokémon.



- **Create Pidgey Class:**



- - Create a header file named `Pidgey.hpp` in `include/Pokemon/Pokemons/`.
  - Include `Pokemon.hpp` and `#pragma once`.
  - Define the `Pidgey` class, inheriting from `Pokemon`.
  - Declare a constructor and a `wingAttack()` method.



- **Implement Pidgey Class:**



- - Create the source file `Pidgey.cpp` in `src/Pokemon/Pokemons/`.
  - Include `Pidgey.hpp` and the necessary headers.
  - Implement the `wingAttack()` method, printing the attack action and dealing damage.



- **Create Caterpie Class:**



- - Create a header file named `Caterpie.hpp` in `include/Pokemon/Pokemons/`.
  - Include `Pokemon.hpp` and `#pragma once`.
  - Define the `Caterpie` class, inheriting from `Pokemon`.
  - Declare a constructor and a `bugBite()` method.



- **Implement Caterpie Class:**



- - Create the source file `Caterpie.cpp` in `src/Pokemon/Pokemons/`.
  - Include `Caterpie.hpp` and the required headers.
  - Define the `bugBite()` method that displays the attack and deals damage.



- **Create Zubat Class:**



- - Create a header file named `Zubat.hpp` in `include/Pokemon/Pokemons/`.
  - Include `Pokemon.hpp` and `#pragma once`.
  - Define the `Zubat` class, inheriting from `Pokemon`.
  - Declare a constructor and a `supersonic()` method.



- **Implement Zubat Class:**



- - Create the source file `Zubat.cpp` in `src/Pokemon/Pokemons/`.
  - Include `Zubat.hpp` and the necessary headers.
  - Implement the `supersonic()` method to print the attack action and apply damage.





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
