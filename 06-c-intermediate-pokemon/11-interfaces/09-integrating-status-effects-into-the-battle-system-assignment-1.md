# Initial Instructions


---

> **Make sure you have checked out the  **`Feature_10_Interfaces`**  branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_10_Interfaces``** **`**to previous branch **`Feature_9_Polymorphism`**if not already created previously.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



Hey there! 

By now, you’ve created the ParalyzedEffect class, 

and we’ve discussed how status effects can impact Pokémon battles. 



Now, it's time to put it all together, 

and integrate these effects directly into your battle loop. 

Ready? 

Let’s go step by step!




---



### Step 1: Creating the StatusEffectType Enum



First, let's define how we'll keep track of different status effects in your game. 



For this, we’ll create a file, 

that will contain an enumeration of all the status effects your Pokémon can experience.



**Tasks:**

- - Create a header file called `StatusEffectType.hpp`.
  - Inside this file, add an enum class called `StatusEffectType` with values like `PARALYZED`, `SLEEPING`, `BURNED`, and `POISONED`.
  - Make sure to encapsulate everything within the appropriate namespaces.



This will give you a structured way to manage and reference different status effects.




---



### Step 2: Modifying the Battle Loop



Now, let's update your battle loop so that Pokémon can be influenced by the status effects. 

Think about how status effects like paralysis can prevent a Pokémon from attacking. 



You’ll need to adjust the logic of your battle loop to account for whether a Pokémon can move or not.



**Tasks:**

- - Locate your battle loop in `BattleManager.cpp`.
  - Before a Pokémon takes its turn, add a check to see if it can attack using a `canAttack()` function from the Pokémon class.
  - If a Pokémon is paralyzed or affected by another status effect, adjust the loop so that the Pokémon's turn is skipped accordingly.



This will ensure that status effects have a tangible impact on the battle.




---



### Step 3: Updating the Pokémon Class



Now, it’s time to add the required methods and variables, 

inside the Pokémon class to handle status effects. 

You’ll need to introduce some new properties and methods to manage these effects properly.



**Tasks:**

- - Add a member variable to track the current status effect on the Pokémon. This should be a pointer to the `IStatusEffect` interface.
  - Create the `canAttack()` function that checks if the Pokémon is allowed to move based on the applied effect.
  - Add methods `applyEffect()`, `clearEffect()`, and `canApplyEffect()` to handle the application, removal, and checking of status effects.



These changes will allow the Pokémon class to recognize and manage status effects during battles.




---



### Step 4: Implementing Status Effect Logic



With the new functions declared in the Pokémon class, 

it’s time to implement the logic behind them. 



Make sure each function does what it's supposed to, 

like applying the effect when necessary or clearing it when the effect wears off.



**Tasks:**

- - Implement the `canAttack()` method to determine if the Pokémon can act based on its current status effect.
  - Define the logic for `canApplyEffect()` to check if a new status effect can be added.
  - Code the `applyEffect()` method to assign a specific status effect like paralysis when triggered.
  - Lastly, make sure `clearEffect()` resets the status when the effect ends.



This will make sure status effects operate correctly in your game.




---



### Step 5: Applying Status Effects through Moves



Finally, to actually apply effects like paralysis during battles, 

you need to connect these effects to specific moves. 

For example, Pikachu’s Thunder Shock should have the ability to paralyze its target.



**Tasks:**

- - Update Pokémon-specific classes, like Pikachu, to include the logic for applying status effects when certain moves are used.
  - Make sure that when a move is used, the target Pokémon checks if it can receive the status effect and then applies it if possible.



This is where the status effects become fully functional in your game, 

making battles more strategic and engaging!




---



### Wrap-Up



Congratulations! 

You’ve integrated status effects into your battle system, 

making your Pokémon game much closer to the real battles. 



The addition of these effects introduces new challenges and strategies, 

making every turn more exciting. Keep up the great work—your game is evolving beautifully! 🎉



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
