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



### Assignment:



Great job making it this far! 

We’re almost done with refactoring our main.cpp file. 



It’s time to take the final steps,

and move your classes into separate files to make your code more organized and manageable. 



Let’s break it down into smaller tasks to get you through this!




---



**Tasks: Separating Enums into Header Files**



1. **Update Main.cpp with Utility Class:**
2. - Include `Utility.hpp`, `PokemonType.hpp`, and `PokemonChoice.hpp` at the top of your main.cpp.
  - Whenever you use methods from the Utility class, make sure to prefix them with `Utility::` so the main file knows where to find them.
3. **Creating Header and Source Files for the Player Class:**
4. - Create `Player.hpp` and `Player.cpp` for the Player class.
  - In `Player.hpp`, include the necessary header files such as `#include "PokemonType.hpp"`, 
    `#include "PokemonChoice.hpp"`, and `#include "Utility.hpp"`.
  - Declare an empty `Player` class and copy the declarations of all data members and methods from main.cpp.
  - Include `Player.hpp` in `Player.cpp` and move the definitions of the Player class methods from the main file into `Player.cpp`.
5. **Handling Errors in Main.cpp and Player.cpp:**
6. - After these changes, you’ll notice some errors pop up in both Player.cpp and main.cpp. Don’t worry—these are expected. You’ll resolve these in the next lesson, so stay tuned!




---



Keep up the great work! 

You’re organizing your code step-by-step, 

and it’s going to pay off big time when everything runs smoothly. 



Let’s keep going!



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
