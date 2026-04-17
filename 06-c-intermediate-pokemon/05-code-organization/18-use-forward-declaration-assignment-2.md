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



Now that we’ve discussed the concept of forward declarations, 

it's time to clean up our code a bit more. 



We need to reduce the number of multiple includes that are creating unnecessary instances of the same header files.

Let’s work through it together!




---



**Tasks:**



- **Forward Declare Pokémon Type in Pokémon Class:**



- - First, let’s start by looking at the `Pokemon.hpp` file.
  - Instead of including `PokemonType.hpp`, we can forward declare the enum. Replace the `#include "PokemonType.hpp"` line with:
  - `enum PokemonType;`
  - This tells the compiler that `PokemonType` exists, without bringing in the entire file.



- **Forward Declare Pokémon in Player Class:**



- - Now, let’s move to `Player.hpp`. Here, instead of including `Pokemon.hpp`, you can simply forward declare the class.
  - Replace `#include "Pokemon.hpp"` with:
  - `class Pokemon;`
  - This will inform the Player class that a `Pokemon` class exists without pulling in all its code.



- **Forward Declare in Main.cpp:**



- - Finally, let’s clean up the `main.cpp`. You’ve included `PokemonType.hpp`, `Pokemon.hpp`, and `Player.hpp` here.
  - Replace these includes with their respective forward declarations:
  - `class Player;`
    `class Pokemon;`
    `enum PokemonType;`
  - This reduces the multiple instances issue and keeps our code much cleaner.






---



That’s it! 

By using forward declarations, 

you’re minimizing unnecessary code duplication and keeping your program lean. 



Check your code to ensure it runs without redefinition errors, 

and everything still works as expected.



Keep up the great work—you're mastering these advanced concepts!





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
