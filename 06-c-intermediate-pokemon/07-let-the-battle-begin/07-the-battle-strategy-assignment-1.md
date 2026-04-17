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



As you venture through the forest, 

you stumble upon Cynthia, 

the Champion of the Sinnoh region. 



She’s been observing your battles closely, 

impressed by your progress but sees room for improvement. 



![A scene deep in a forest where a tall, confident woman with long blonde hair stands with a determined look. She wears a black, elegant outfit and looks like a skilled warrior or leader. Across from her stands a young adventurer, surprised but focused, ready for a challenge. The forest is lush, with sunlight filtering through the leaves, casting a peaceful yet intense atmosphere. The woman points forward, as if issuing a challenge, with an air of authority. The scene feels like a critical moment of training and self-improvement for the adventurer, surrounded by the calm but charged forest.](https://files.oaiusercontent.com/file-DfDJbMenUvUqbDcdJGH8gRll?se=2024-09-20T09%3A12%3A07Z&sp=r&sv=2024-08-04&sr=b&rscc=max-age%3D604800%2C%20immutable%2C%20private&rscd=attachment%3B%20filename%3D196e92fb-73a2-4412-a00b-c629689cc6f0.webp&sig=Wc3UopssT6IvGrvOAtU3FCtionpXYv/lghzgBX1AtIw%3D)



“I can see your Pokémon have potential," 

"but a true trainer knows how to control the flow of battle from start to finish." 

"Let’s take your battle skills to the next level,” 

Cynthia says.



She challenges you to refine your battle mechanics with a more structured approach. 

It’s time to create a dedicated system that manages battles efficiently.



**Objectives:**



- **Create the BattleManager Class:** 

Cynthia emphasizes the importance of separating battle logic from other parts of the game. 

“A Champion doesn’t leave battles to chance,” she says. 

“We need a class that handles all aspects of a battle.”



- - **Task:**
  - - Create a header file, `BattleManager.hpp`, and declare three methods: `startBattle()`, `battle()`, and `handleBattleOutcome()`.
    - Pass the `Player` object (`Player &player`) and wild Pokémon object (`Pokemon &wildPokemon`) as parameters for the `startBattle()` method.
    - For the `battle()` method, pass the player’s Pokémon (`Pokemon &playerPokemon`) and wild Pokémon (`Pokemon &wildPokemon`).
    - For the `handleBattleOutcome()` method, pass the `Player` object (`Player &player`) and a boolean variable (`bool playerWon`) to determine the battle outcome.



- **Implement Battle Management Logic:** 

         "Knowing when to strike and when to defend is key,” Cynthia advises. 

You’ll build a system that manages turn-based combat, 

determines when Pokémon faint, 

and handles battle outcomes.



- - **Task:**
  - - Implement the `startBattle()` method to initiate combat between the player's Pokémon and the wild Pokémon. Print a statement indicating that a wild Pokémon has appeared and call the `battle()` method.
    - Implement the `battle()` method to manage the actual battle. This method should ensure that both the player’s Pokémon and the wild Pokémon take turns attacking until one of them faints.
    - Implement the `handleBattleOutcome()` method to determine and display the result of the battle. Use conditional statements to check if the player won or lost, and print the appropriate message.



- **Integrate BattleManager into the Game Loop:** 

“A true trainer controls every moment,” Cynthia explains." 

“You need to integrate this system into your main game loop," 

"so, every encounter feels intense and meaningful.”



- - **Task:**
  - - Update the `gameLoop` in the `Game` class to use the `BattleManager` for handling wild Pokémon battles.
    - In case 1 of the switch statement, create an instance of `WildEncounterManager` to generate a random wild Pokémon and use the `BattleManager` to start the battle.
    - For case 2, implement the healing process when visiting the PokéCenter using `player.chosenPokemon.heal()`.
    - Ensure that quitting the game (case 5) works correctly, allowing the player to exit gracefully.




---



With Cynthia’s guidance, 

you’ve successfully implemented a structured battle system. 

“Impressive work,” Cynthia smiles. 



“With this kind of control, you’re well on your way to becoming a master trainer. 

Keep refining your skills, and never lose sight of the strategy that makes each battle unique.”





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
