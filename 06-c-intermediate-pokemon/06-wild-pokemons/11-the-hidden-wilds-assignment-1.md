# Initial Instructions


---

> **Make sure you have checked out the **`Feature_5_Wild_Pokemons `**branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_5_Wild_Pokemons `**to previous branch **`Feature_4_Code_Organization `**if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



**Misty:** "Hey there!"

  "I heard you’re on a journey to become the ultimate Pokémon Trainer." 

  "But you’re missing something..." 

  "the thrill of encountering wild Pokémon!" 

  "Let’s spice things up a bit," 

  "shall we?"



**Misty's Challenge: The Hidden Wilds**



Wild Pokémon can be unpredictable. 

Imagine wandering through dense forests or mysterious caves, 

never knowing what might pop up next! 

It's time to add that excitement to your game.



![An adventurous scene set in a dense forest, where a traveler is walking cautiously through the thick woods. The forest is filled with towering trees, thick vines, and low-lying bushes, creating an atmosphere of mystery. Sunlight filters through the dense canopy, casting shadows on the ground. In the background, mysterious caves can be seen, and there is a sense of tension as if something unexpected might appear. The traveler is on edge, aware of the unpredictability of the wilderness, making the scene feel suspenseful and full of adventure.](https://files.oaiusercontent.com/file-fJYwUktyiLc3Ko4N1LiQ0uiP?se=2024-09-20T08%3A40%3A28Z&sp=r&sv=2024-08-04&sr=b&rscc=max-age%3D604800%2C%20immutable%2C%20private&rscd=attachment%3B%20filename%3D1734cda4-9de4-4ff2-9fc9-a31d1aa08cd2.webp&sig=oxXvXcSZWZKmKZL%2Bm9fQxDqwzFM8t4uWsbAqN8dEltc%3D)




---



### **Step 1: Creating the Wild Encounter Manager**



**Misty:** "We need a specialist who manages all those wild encounters." 

  "Let’s make this happen!"



**Task 1: Create **`**WildEncounterManager.hpp**`



- - - Create a new header file named `WildEncounterManager.hpp`.
    - Include the header file `Grass.hpp` and `<vector>`.
    - Define the class `WildEncounterManager`. This class has one job: to decide which wild Pokémon you’ll encounter.
    - Create a public method `getRandomPokemonFromGrass()` that picks a Pokémon from the grass you’re exploring.



**Task 2: Create **`**WildEncounterManager.cpp**`



- - - Create a source file named `WildEncounterManager.cpp`.
    - Include the header `WildEncounterManager.hpp` along with `<cstdlib>` for `rand()` and `<ctime>` for `time()`.
    - Misty whispers, "Seed the randomness with the current time so each encounter feels fresh and new."
    - Implement the `getRandomPokemonFromGrass()` method to grab a random Pokémon from the list within the grass.



### **Step 2: Integrating the Encounter Manager into the Game**



**Misty:** "Now, it’s time to let the wild Pokémon roam!" 

  "We’ll set up their environment and see who pops up during your journey."



**Task 1: Initialize the Wild Grass in **`**Game.hpp**`** and **`**Game.cpp**`



- - - Add the grass to your game environment. Include `Grass.hpp` in `Game.hpp`.
    - Create a private member `forestGrass` of type `Grass`.
    - Initialize it with some wild Pokémon like Pidgey, Caterpie, and Zubat in the game’s constructor.



**Task 2: Encounter Wild Pokémon in the Game Loop**

- - - Include `WildEncounterManager.hpp` in `Game.cpp`.
    - When the player chooses to "Battle Wild Pokémon," let’s make it thrilling!
    - Create an object `encounterManager` and let it decide which Pokémon the player will encounter.




---



**Misty:** "Now, each step through the grass is an adventure of its own. 

 "Who knows what you’ll find next? 

 "Get ready to encounter the wild and unpredictable world of Pokémon!"





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
