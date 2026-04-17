# Initial Instructions


---

> **Make sure you have checked out the **`Feature_2_OOP` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_2_OOP` **to previous branch **`Feature_1_Pokemon_Selection`**  if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



## **Side Quest: The Great PokéLab Challenge**


---

**Quest Briefing:**


---



Professor Oak’s lab is in chaos! 

Some mischievous Pokémon (we suspect a wild Rotom) have scrambled the systems, 

and now the Professor’s database for managing Pokémon and trainers is acting up. 



The classes for Pokémon, players, and even the Professor himself have lost their data and functions! 

Professor Oak needs your help to restore order.



Your mission, which if you choose to accept, is to rebuild the classes for Pokémon, Player, and Professor Oak. 



But that’s not all—Professor Oak has a special request: 

he wants his lab’s data system to be more organized this time around, 

with each class having its own distinct role and clear responsibilities.



**Quest Details:**


---



Professor Oak turns to you and says, 

"I need you to help me put everything back together. Here's what you need to do:"



1. **Rebuild the Pokémon Class**:
2. - Create a class called `Pokemon` that has the following properties:
  - - `name` (e.g., Pikachu, Charmander)
    - `type` (e.g., Fire, Water, Electric)
    - `health` (the amount of health points)
  - Add a method called `attack()` that prints a message like: `<Pokemon> attacks with a powerful move!`
3. **Rebuild the Player Class**:
4. - Create a class called `Player` that represents the Pokémon trainer.
  - Add the following properties:
  - - `name` (trainer’s name)
    - `chosenPokemon` (the Pokémon chosen by the trainer)
  - Add a method called `choosePokemon()` that allows the player to select their Pokémon. Use a switch statement to handle the choices (you’ll need to copy over the switch code from earlier).
5. **Help Professor Oak:**
6. - Create a class called `ProfessorOak` and add the following properties:
  - - `name` (the Professor's name, which should be "Professor Oak")
  - Add the methods `greetPlayer()` and `offerPokemonChoices()`, which handle interactions with the player. These methods will take a reference to a `Player` object.
7. **Create the Main Game Objects:**
8. - Inside the `main()` function, create objects for the `Pokemon`, `Player`, and `ProfessorOak` classes.
  - Set up their initial properties and make sure to call the Professor’s methods so he can greet the player and present Pokémon choices.



**Objective:** 


---



Your task is to restore the Pokémon lab's database system by correctly organizing the code into these classes. 



Once complete, Professor Oak will be able to greet the player, 

offer Pokémon, and get his lab running smoothly once more!



**Expected Output:** 


---



When you run your code, the following should happen in your console:

1. Professor Oak greets the player and asks for their name.
2. The player chooses a Pokémon from the given options.
3. The chosen Pokémon is acknowledged by Professor Oak.
4. The player and their Pokémon are ready to start their journey.



Console Output Example:

```cpp
Professor Oak: Hello there! Welcome to the world of Pokémon!

Professor Oak: My name is Oak. People call me the Pokémon Professor!

Professor Oak: But enough about me. Let's talk about you!

Professor Oak: First, tell me, what’s your name?

[Ash]

Professor Oak: Ah, Ash! What a fantastic name!

Professor Oak: I have three Pokémon here with me. They’re all quite feisty!

1. Charmander - The fire type. A real hothead!
2. Bulbasaur - The grass type. Calm and collected!
3. Squirtle - The water type. Cool as a cucumber!

[Player chooses 1]

Professor Oak: A fiery choice! Charmander is yours!

Professor Oak: Charmander and you, Ash, are going to be the best of friends!

Professor Oak: Your journey begins now! Get ready to explore the vast world of Pokémon!

```



This version turns the assignment into a meaningful side quest that feels connected to the Pokémon world, 

giving students a more engaging and story-driven reason to complete their coding tasks.





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
