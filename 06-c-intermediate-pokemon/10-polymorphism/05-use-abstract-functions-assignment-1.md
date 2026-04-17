# Initial Instructions


---

> **Make sure you have checked out the **`Feature_9_Polymorphism` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_9_Polymorphism` **to previous branch **`Feature_8_Pointers `**if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



You need to make some important updates, 

to your game code, 

to better organize how each Pokémon type handles its attacks. 



This will involve converting the `attack()` function in the `Pokemon` class into an abstract function and ensuring all child classes implement their unique versions.



### Step 1: Update the Base Class with an Abstract Function



Currently, the `attack()` function in the `Pokemon` class serves no purpose as a common function. 

Convert it into an abstract function to enforce that each Pokémon must define its unique attack.



**Tasks:**

- - - Open `Pokemon.hpp`.
    - Change the `attack()` function declaration to an abstract function.



### Step 2: Remove the Function Definition from the Base Class



Since you have made `attack()` an abstract function, it no longer needs a definition in the base class file.



**Tasks:**

- - - Open `Pokemon.cpp`.
    - Remove the existing definition of the `attack()` function from the code.



### Step 3: Implement `attack()` in Each Child Class

With `attack()` now being an abstract function, each Pokémon class must provide its implementation of the function.



**Tasks for Each Pokémon (e.g., Caterpie, Charmander, etc.):**



- Open the respective header file (e.g., `Caterpie.hpp`, `Charmander.hpp`).
- Ensure the `attack()` function is declared and marked to override the base class function.
- Open the respective source file (e.g., `Caterpie.cpp`, `Charmander.cpp`).
- Define the `attack()` function to call the unique move of that Pokémon.



### Step 4: Repeat for All Pokémon Classes



Ensure each Pokémon class defines its `attack()` function correctly, 

reflecting the unique behavior of that Pokémon.




---



> **YOUR CODE IS NOT SUPPOSED TO RUN AFTER THIS ASSIGNMENT. IT WILL GET FIXED IN THE NEXT CONTENT.**





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
