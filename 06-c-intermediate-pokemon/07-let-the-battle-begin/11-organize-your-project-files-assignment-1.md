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



You've been working hard on your Pokémon game, 

but as your project grows, 

you might notice that navigating through all the files is becoming a bit overwhelming. 



Right now, 

everything is in one place, 

making it harder to manage and find what you need.



## **Why Organize Your Files?**


---

As your game continues to develop, 

the number of files will keep increasing. 



To keep your project manageable and your workflow smooth, 

it’s essential to keep your files organized. 



A well-structured project not only makes it easier to find files, 

but also helps in understanding how everything fits together.



Let’s start by separating your source files (`.cpp`) from your header files (`.hpp`). 

This will make your project cleaner and more maintainable.




---



### **Step 1: Separate Source and Header Files**



- **Create Main Folders:**



- - Create a folder named `src` to hold all the source files (`.cpp` files).
  - Create another folder named `include` to hold all the header files (`.hpp` files).



- **Move Files:**



- - Move all `.cpp` files into the `src` folder.
  - Move all `.hpp` files into the `include` folder.



- **Adjust Include Statements:**



- - Since the locations of these files have changed, you'll need to update the `#include` statements in your code.
  - For example, if `Pokemon.hpp` is now inside the `include` folder, update the include statement in `Pokemon.cpp` to:```cpp
    
    #include "../include/Pokemon.hpp"
    
    ```



### **Step 2: Create Subfolders for Specific Functionalities**



Now that you have your source and header files separated, 

it’s time to take it a step further by organizing them into subfolders based on their functionalities.



- **Create Subfolders:**



- - Inside both the `src` and `include` folders, create the following subfolders:
  - - **Battle**
    - **Character**
    - **Main**
    - **Pokemon**
    - **Utility**
  - Inside the **Character** folder, create another subfolder called **Player**.



- **Move Files into Subfolders:**



- - Move files into their respective subfolders:
  - - **Battle Folder**: Move `BattleManager`, `BattleState`, and `WildEncounterManager` files.
    - **Character Folder**: Move `ProfessorOak` files.
    - **Player Subfolder (inside Character)**: Move `Player` files.
    - **Main Folder**: Move `Game` files.
    - **Pokemon Folder**: Move `Grass`, `Pokemon`, `PokemonChoice`, and `PokemonType` files.
    - **Utility Folder**: Move `Utility` files.
  - Keep `main.cpp` in the main directory as it is the entry point of the program.



### **Step 3: Update Include Paths in Your Code**



Since you’ve moved all the files into subfolders, you’ll need to update the paths in the `#include` statements accordingly. For example:

- For a file moved to the `Battle` subfolder, update the include statement like this:```cpp
  
  #include "../../include/Battle/WildEncounterManager.hpp"
  
  ```



Ensure you update the paths in all files to reflect their new locations.



## **Why This Matters**


---

Organizing your files will not only make your project look cleaner, 

but also help you and anyone else working on your project to understand the structure quickly. 



This separation of concerns makes maintenance easier and improves the overall workflow.




---



### **Tasks to Complete:**



1. Create `src` and `include` folders to separate source and header files.
2. Create subfolders (`Battle`, `Character`, `Main`, `Pokemon`, `Utility`) in both `src` and `include`.
3. Create a `Player` subfolder inside the `Character` folder.
4. Move the appropriate files into their respective folders and subfolders.
5. Update all `#include` statements to reflect the new file paths.



Let’s get started on organizing your project to keep it clean and easy to manage!





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
