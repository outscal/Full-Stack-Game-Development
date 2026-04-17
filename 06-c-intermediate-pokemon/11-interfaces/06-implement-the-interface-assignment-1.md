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


Great job setting up the `IStatusEffect` interface! 



Now, it's time to make your battles more dynamic by adding the Paralyzed effect to your game. 



Let's bring the Paralyzed status effect to life!



### Step 1: Setting Up the Paralyzed Effect



**Task:** 

You will create the Paralyzed effect by implementing the methods from the `IStatusEffect` interface.



**What You Need to Do:**



- **Create the Header File:** Start by creating a new header file named `ParalyzedEffect.hpp`.



- **Inheritance Setup:** Make sure the `ParalyzedEffect` class inherits from the `IStatusEffect` interface using public inheritance.



- **Declare the Variables and Methods:**



- - Add a private member variable `int turnsLeft` to keep track of the remaining turns of the effect.
  - Declare the following methods that override the functions in the `IStatusEffect` interface:
  - - `applyEffect(Pokemon* target)`
    - `getEffectName()`
    - `turnEndEffect(Pokemon* target)`
    - `clearEffect(Pokemon* target)`



Take a moment to set up your `ParalyzedEffect.hpp` file with these requirements. 

This will form the backbone of your Paralyzed effect!



### Step 2: Implement the applyEffect() Method



**Task:** 

Now, let's implement the `applyEffect()` method to apply the Paralyzed effect on a Pokémon.

**What You Need to Do:**



- **Print a Message:** Inform the player that their Pokémon is paralyzed and may not be able to move.



- **Set Duration:** Randomly set the effect duration between 1 to 3 turns.



This step will ensure that the player is aware of the effect, and the game knows how long it will last.



### Step 3: Implement the getEffectName() Method



**Task:** 

Next, you need to implement the `getEffectName()` method, 

which will return the name of the effect to be displayed during the battle.



**What You Need to Do:**



- Simply return the name of the effect—this will help the player see what status is affecting their Pokémon during the game.



### Step 4: Implement the turnEndEffect() Method



**Task:** 

This method handles the effect at the end of each turn. 

It will check if the effect should continue or be cleared, 

and determine if the Pokémon can move.



**What You Need to Do:**



- **Check the Turns Left:** If `turnsLeft` is less than or equal to 0, call `clearEffect()` to remove the paralysis.



- **Decrease Duration:** Reduce the remaining turns by 1.



- **Determine Movement:** Randomly decide if the Pokémon can move using a 25% chance of being unable to act.



This will keep the Paralyzed effect dynamic and make each turn feel unpredictable!



### Step 5: Implement the clearEffect() Method



**Task:** 

Finally, implement the `clearEffect()` method, 

which will remove the Paralyzed effect from the Pokémon once it wears off.



**What You Need to Do:**



- **Print a Message:** Notify the player that the Pokémon is no longer paralyzed.



- **Clear the Effect:** Make sure the status effect is properly cleared from the Pokémon.




---



Once you’ve completed these steps, 

you’ll have successfully implemented the Paralyzed effect in your game! 



Test it out to see how it changes the flow of battles. 

After this, try applying similar logic to other status effects like Burn or Poison.



Keep up the fantastic work, 

and get ready to see your Pokémon battles become even more engaging!



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
