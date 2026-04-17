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



As you wander deeper into the forest, 

you encounter a mysterious figure shrouded in shadows. 



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_21_2024__06_46_43.JPG)



It’s Lance, 

the legendary Dragon Master and Champion of the Pokémon League. 

Lance is known for his strategic battles and flawless command over his Pokémon. 

He steps forward, his eyes sharp and determined.



“You’ve come far, 

but you’re missing one crucial aspect in your battles—tracking the state of the battle itself,” Lance says. 

“Without a proper strategy, you’re just swinging wildly. 

Let me teach you how to control every moment of your Pokémon battles.”



Your challenge is to track the current state of your battles, 

ensuring that every move is accounted for, 

and each turn is managed with precision.



**Objectives:**


---



- **Create the BattleState Structure:** 

Lance instructs you on how to keep track of the ongoing battle. 

“You need to know exactly where your Pokémon stand in the heat of battle,” 

he explains. 

“Track every detail, from health to whose turn it is.”



- - **Task:**
  - - Create a header file named `BattleState.hpp`.
    - Inside this file, create a struct named `BattleState` to encapsulate the battle’s key aspects.
    - Include pointers for the player’s Pokémon (`playerPokemon`) and the wild Pokémon (`wildPokemon`).
    - Add two boolean variables: `playerTurn` to track whose turn it is, and `battleOngoing` to monitor if the battle is still active.



- **Integrate BattleState into BattleManager:** 

Lance nods approvingly. 

“Good, but now you need to put that structure into action." 

"Integrate it with your battle manager to bring your battles to life.”



- - **Task:**
  - - Include `BattleState.hpp` in the `BattleManager.hpp` file.
    - Initialize a `BattleState` object inside the `BattleManager` class to keep track of the battle’s progress.
    - Update the `startBattle()` function in `BattleManager.cpp` to use this object, setting the initial states: assign the current Pokémon to the battle state, set `playerTurn` to true, and `battleOngoing` to true.



- **Implement Battle Turns and Update Logic:** 

“Every turn counts,” Lance emphasizes. 

“You must manage each attack, 

check if a Pokémon has fainted, 

and adjust the battle state accordingly.”



- - **Task:**
  - - Modify the `battle()` method in `BattleManager` to alternate turns between the player and the wild Pokémon using the `playerTurn` boolean.
    - After each turn, call the `updateBattleState()` method to check if either Pokémon has fainted, and adjust `battleOngoing` accordingly.
    - Ensure that turns switch correctly by toggling `playerTurn` at the end of each iteration.



- **Handle Battle Outcomes:** 

Lance smirks, “Victory or defeat, every battle must have a clear outcome. Ensure your game reflects this reality.”



- - **Task:**
  - - Create the `handleBattleOutcome()` method in `BattleManager` to determine the battle’s result.
    - Use conditional statements to check if the player’s Pokémon has fainted or if the wild Pokémon has been defeated.
    - Display the appropriate outcome message: congratulate the player if they win, or prompt them to visit the PokéCenter if they lose.




---



With Lance’s guidance, you’ve learned to master the flow of battle. 



“Remember,” 

Lance says as he steps back into the shadows, 

“a true trainer knows not just how to fight, but how to control the battlefield itself.”



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
