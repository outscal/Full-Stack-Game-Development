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



You’re deep in the heart of Viridian Forest, 

an eerie silence surrounds you, 

only broken by the rustling leaves. 



Misty, your fierce but loyal companion, nudges you. 

“Hey, you can’t just waltz into a battle unprepared!" 

"It’s time to get those battle mechanics right. Are you up for it?”



![An intense scene on an open battlefield where the same young woman with short orange hair, wearing a yellow top with red straps and blue shorts, is confidently standing with determination. She faces an opponent across the field, ready for battle. The atmosphere is charged with energy, and the battleground is surrounded by trees and hills. The sky is slightly cloudy, adding to the tension, as both sides prepare for a tactical and important fight. The moment feels crucial, and the adventurer looks fully prepared, matching the earlier depiction of Misty.](https://files.oaiusercontent.com/file-Fuo0FAYARUgU3wH3QOkHqd39?se=2024-09-20T08%3A52%3A17Z&sp=r&sv=2024-08-04&sr=b&rscc=max-age%3D604800%2C%20immutable%2C%20private&rscd=attachment%3B%20filename%3D982dac32-0ef1-400a-a63c-31a2c803ca84.webp&sig=AvdML5bYXwR65dinAMbes0CgB5XnBib/3%2BAlsYpceRY%3D)






---



**Tasks 1: Setting Up Your Pokémon’s Vitality**



**Misty:** “First, let’s make sure our Pokémon have some life in them." 

  "We need to give them Health Points so they can take a hit and keep going.”



1. - **Add Vitality to Your Pokémon:**
  - - In `pokemon.hpp`, add `health` and `maxHealth` to represent your Pokémon’s current and maximum HP.



1. - **Health Control Methods:**
  - - Create a method `takeDamage()` to subtract health points when your Pokémon takes a hit.
    - Make another method `isFainted()` to check if your Pokémon is still standing.




---



**Tasks 2: Inflict Damage and Keep the Fight Going!**



**Misty:** “We can’t just stand there!" 

  "When we get attacked, our Pokémon should lose health." 

            "We’ll code that now.”



1. - **Define Damage Logic in Pokémon’s File:**
  - - Inside `pokemon.cpp`, define how the `takeDamage()` function will work. Make sure to keep your health above zero!
    - Also, finalize `isFainted()` to see when your Pokémon bites the dust.




---



**Tasks 3: Get Ready to Strike Back!**



**Misty:** “Time to hit back!" 

"We can’t let those wild Pokémon think they can mess with us.”



1. - **Add Attack Power:**
  - - Implement the `attack()` function in your Pokémon class. Set a fixed damage, and make your Pokémon shout its move with a line like “Pikachu attacks Bulbasaur for 10 damage!”




---



**Tasks 4: Battle Until the Last Pokémon Stands**



**Misty:** “We’ll keep fighting until one of us is knocked out." 

   "Let’s set the stage for our first battle!”



1. - **Set Up the Battle:**
  - - Write a battle sequence in the `battle()` method. The player Pokémon strikes first, but don’t celebrate too soon—if the wild Pokémon is still up, it’s coming for you.





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
