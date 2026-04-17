# Initial Instructions


---

> **Make sure you have checked out the **`Feature_6_Battle_Loop` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_6_Battle_Loop` **to previous branch **`Feature_5_Wild_Pokemons` **if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**
> 
> **Since, this is a guided assignment, code reviews will not happen, instead the solution code is present in the content itself.**
> 
> **But, before checking the solution code, first try your best to solve it on your own.**
> 
> **Move to the solution only if you get stuck for a long time.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



Awesome work on organizing your code into folders! 

Your project is now much more structured, 

but there’s one more step that will help keep everything cleaner and more organized—adding namespaces.




---



### **Tasks to Complete**



- **Player Files:**
- - **Namespace Name:** `N_Player`
  - Bind both `Player.hpp` and `Player.cpp` under the `N_Player` namespace.



- **ProfessorOak Files:**
- - **Namespace Name:** `N_Character`
  - Bind `ProfessorOak.hpp` and `ProfessorOak.cpp` under the `N_Character` namespace.



- **Game Files:**
- - **Namespace Name:** `N_Main`
  - Bind `Game.hpp` and `Game.cpp` under the `N_Main` namespace.



- **Battle Files:**
- - **Namespace Name:** `N_Battle`
  - Bind `BattleManager`, `BattleState`, and `WildEncounterManager` (`.hpp` and `.cpp` files) under the `N_Battle` namespace.



- **Pokemon Files:**
- - **Namespace Name:** `N_Pokemon`
  - Bind `Pokemon.hpp`, `Pokemon.cpp`, `Grass`, `PokemonChoice`, and `PokemonType` files under the `N_Pokemon` namespace.



- **Utility Files:**
- - **Namespace Name:** `N_Utility`
  - Bind the `Utility.hpp` and `Utility.cpp` files under the `N_Utility` namespace.




---



### **Steps to Complete the Assignment**



- **Edit Header Files (**`**.hpp**`**):**
- - Add the appropriate namespace around the class and function declarations.



- **Edit Source Files (**`**.cpp**`**):**
- - Add the same namespace around the function definitions to match the header files.



- **Update Code Usage:**
- - Wherever these namespaces are needed, add `using namespace N_<FolderName>;` at the top of the relevant files to access the classes and functions easily.
  - Alternatively, you can use the fully qualified name with the scope resolution operator (`N_<FolderName>::`) where required.



- **Update All #include Statements:**
- - Ensure all include statements are correctly aligned with the new folder and namespace structure.



- **Integrate Namespaces in Existing Code:**
- - Review all your existing code and integrate the namespaces where required, ensuring the correct usage of classes and methods according to their namespace.



## **Why This Matters**


---



Using namespaces will make your code cleaner, 

and help prevent conflicts as your project grows. 



By implementing this step, 

your project will be more organized, easier to navigate, 

and overall more professional.



Go ahead and start adding namespaces to your code, 

and make sure they are used correctly throughout your project!



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
