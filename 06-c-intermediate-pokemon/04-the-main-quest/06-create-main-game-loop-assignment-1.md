# Initial Instructions


---

> **Make sure you have checked out the **`Feature_3_Main_Quest `**branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_3_Main_Quest` **to previous branch **`Feature_2_OOP`** if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



As you leave Professor Oak behind, 

the world of Pokémon opens up before you. 



But this world isn't just about battles—it's about choices, strategy, 

and making your mark as a Pokémon Trainer. 



To bring this world to life, 

you need to give your game its "heartbeat"—a Game Loop that keeps the action flowing and your adventure alive.



**Your mission, should you choose to accept it:**

Professor Oak is no longer there to guide every step. 

It’s up to you to build the system that will keep the game moving.



### **Task 1: Creating the Game Loop—The Heartbeat of Your Adventure**



- Create a new function called `gameLoop` just below the `explainMainQuest()` function. This function will be the heart of your game, taking in the `Player` object as a parameter.



- The function should have a `void` return type since it’s only managing the game flow.



- Inside `gameLoop`, create a `bool` variable called `keepPlaying` and set it to `true`. This will keep the loop going as long as the player is exploring the Pokémon world.



- Set up a `while` loop with `keepPlaying` as the condition. This loop will keep running, keeping your game alive until the player decides to exit.



### **Task 2: Presenting Choices—The Crossroads of Your Journey**



Every great journey is filled with choices. 

In the Pokémon world, your decisions determine your path to becoming a champion. 

It’s time to present these choices to the player and let them steer their adventure.



- Inside your `gameLoop`, display the options available to the player. These choices are the various actions they can take in their journey.



- Create a variable called `choice` to store the player’s input.



- Display a message prompting the player to choose their next action, reinforcing that their decisions shape their adventure.



```cpp
What would you like to do next - [Player.name]

 Battle Wild Pokémon
Visit PokeCenter
Challenge Gyms
Enter Pokémon League
Quit
```



### **Task 3: Handling Choices—Adventure Awaits!**



Now that the player can make choices, 

it’s time to handle their input and respond with some fun, engaging messages. 

These responses set the tone for each action and keep the player immersed in the Pokémon world.



- Implement a `switch` statement inside your `while` loop to handle each possible player action.



- For now, print out the funny messages provided for each choice, hinting at the adventures yet to come. These are placeholders for the real features you’ll implement later.



```cpp
1. Battle Wild Pokémon

"You look around... but all the wild Pokemon are on vacation. Maybe try again later?\\n";


2. Visit PokeCenter

"You head to the PokeCenter, but Nurse Joy is out on a coffee break. Guess your Pokemon will have to tough it out for now!\\n";


3. Challenge Gyms

"You march up to the Gym, but it's closed for renovations. Seems like even Gym Leaders need a break!\\n";


4. Enter Pokemon League

"You boldly step towards the Pokemon League... but the gatekeeper laughs and says, 'Maybe next time, champ!'\\n";


5. Quit

"You try to quit, but Professor Oak's voice echoes: 'There's no quitting in Pokemon training!'\\n";

```



**Final Step:** 

After handling the player’s choice, 

wait for them to press Enter using `waitForEnter()`, 

allowing them to digest the response before the screen refreshes with new options.



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
