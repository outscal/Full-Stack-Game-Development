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



You're almost there! 

Just a few more tweaks to get your code running smoothly.




---



**Tasks to Resolve Redefinition Errors:**



1. **Fix Redefinition Issues:**
2. - Let’s clean up those pesky redefinition errors by shifting the `#include` statements of `PokemonChoice.hpp`, `PokemonType.hpp`, and `Utility.hpp`.
3. **Move Includes to Player.cpp:**> Note: Remember, Player.cpp isn’t directly included in main.cpp, so this will help resolve the redefinition issues without causing new ones.
4. - Move these `#include` statements from `Player.hpp` to `Player.cpp`. This way, you won’t end up including them twice indirectly in `main.cpp`.




---



By doing this, 

you’re keeping your code neat and organized, 

avoiding unnecessary errors. Keep it up—you’re doing great!





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
