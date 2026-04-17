# Initial Instructions


---

> **Make sure you have checked out the **`Feature_10_Interfaces `**branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_10_Interfaces `**to previous branch **`Feature_9_Polymorphism`**if not already created previously.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



Great job on understanding the importance of interfaces, 

and how they can streamline your code, 

by creating a unified structure for status effects like Poison and Burn. 



Now, let’s put that knowledge into practice!



### Step 1: Setting Up the IStatusEffect Interface



**Task:** 

Your job is to create an interface called `IStatusEffect` ,

that will act as the blueprint for all status effects in your Pokémon game.



**What You Need to Do:**



1. Create a new header file named `IStatusEffect.hpp`.
2. Define the `IStatusEffect` interface with the methods that every status effect must implement:
3. - `applyEffect()` - for applying the status effect to a Pokémon.
  - `getEffectName()` - for getting the name of the effect to display in the game.
  - `turnEndEffect()` - for applying changes due to the effect at the end of each turn and determining if the Pokémon can still move.
  - `clearEffect()` - for removing the status effect once it’s over.



**Think About:** 

How this interface will help you standardize different status effects, making your code cleaner and easier to manage.





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
