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



To make the necessary updates to your game code, 

based on the content you just learned, follow these steps. 



This assignment will guide you through the changes without directly providing the code, 

allowing you to practice implementing the concepts.



#### Step 1: Update Pokémon Class Object Creation



Since the Pokemon class is now an abstract class, 

you can no longer create objects of this class directly. 

You need to update your code to create objects of specific Pokémon classes instead.



**Tasks:**

- - Locate any lines in your code where a `Pokemon` object is being created (e.g., `new Pokemon("Charmander", `
  
  `PokemonType::FIRE, 100, 10)`).- Replace these with the appropriate specific Pokémon class (e.g., `new Charmander()`).
  - Ensure that each Pokémon type is instantiated with its specific class.



#### Step 2: Update the Player Class



The Player class currently uses a Pokemon class object in the constructor. 

You need to revise these constructors to align with the changes.



**Tasks:**

- - Open `Player.cpp`.
  - In the default constructor, remove any lines that create a default `Pokemon` object.
  - In the parameterized constructor, update the code to no longer require a `Pokemon` pointer as a parameter. Adjust the constructor to initialize only the player’s name.



#### Step 3: Update the Game Class



The Game class manages wild Pokémon encounters. 

Update the class to properly, 

handle Pokémon objects using pointers without directly instantiating Pokemon class objects.



**Tasks:**

- - Open `Game.hpp` and add a `Pokemon* wildPokemon` pointer as a private member.
  - Declare a destructor in the `Game` class to handle the deletion of `wildPokemon`.
  - Open `Game.cpp` and remove any lines that create `Pokemon` objects directly. Instead, manage the `wildPokemon` pointer using the updated `Game` class methods.
  - Define the destructor in `Game.cpp` to delete `wildPokemon` when it is no longer needed.



#### Step 4: Testing the Changes



- Once you’ve made the changes, run your code.
- Verify that no errors related to abstract classes or object creation occur.
- Test all Pokémon behaviors to ensure the `attack()` functions work as expected.



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
