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



You’ve made it this far, 

and it’s time to complete the final touches to make your Pokémon game shine! 



These last few adjustments will help you fix any lingering issues, 

and optimize your code. 



Let’s finish this strong!




---



**Tasks:**



- **Include **`**Pokemon.hpp**`** in **`**Player.hpp**`**:**



- - Since `Player` has a full `Pokemon` object as a member, you need the complete definition of `Pokemon` in `Player.hpp`.
  - Add the include statement:```cpp
    
    #include "Pokemon.hpp"
    
    ```
  - This will ensure that the Player class knows exactly what a `Pokemon` is, allowing you to keep everything functioning correctly.



- **Remove **`**Pokemon.hpp**`** from **`**main.cpp**`**:**



- - You don’t need to include `Pokemon.hpp` directly in `main.cpp` because `Player.hpp` already includes it.
  - Go ahead and remove the line `#include "Pokemon.hpp"` from `main.cpp`. This will help you avoid any redefinition errors and keep your code clean.



- **Update **`**choosePokemon()**`** Function in **`**Player.cpp**`**:**



- - In your `Player.cpp`, you’re using a `switch` statement that operates on integer values but assigns `PokemonType` and `PokemonChoice` values.
  - Typecast `choice` to `PokemonChoice` in the switch statement:```cpp
    
    switch ((PokemonChoice)choice)
    
    ```
  - This small change will make sure your code compiles correctly and the switch statement works as intended.



- **Modify the **`**clearConsole()**`** Function in **`**Utility.cpp**`**:**



- - Let’s make one last minor adjustment to the `clearConsole()` function to ensure it’s working across all platforms.
  - Update the else part of the function to:```cpp
    
    (void)system("clear");
    
    ```
  - This helps suppress any warnings about unused return values, keeping the function nice and tidy.




---



That's it—you've reached the end of your journey with this Pokémon project! 



You’ve debugged, 

refactored, and optimized your code to create a robust and organized game. 



Celebrate your success, 

and enjoy the smooth-running code you’ve worked so hard on! 🎉



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
