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



The next chapter of your journey as a Pokémon Trainer awaits! 

But before you can fully dive into the action, 

Professor Oak needs to brief you on your main quest, 

which is crucial to becoming the ultimate Pokémon Champion. 



The objective is not just to battle and win, 

but to understand the very heart of being a Pokémon Trainer.

The first step is, to ensure that Professor Oak properly introduces the players to their main mission. 



Let’s code this interaction as a side quest in the Pokémon world! 

Professor Oak is known for his lengthy explanations, but this time, 

he’s prepared a special briefing just for you.



**Scenario:** 



Imagine the player standing in Professor Oak’s lab, 

surrounded by books, Poké Balls, and various research equipment. 



Professor Oak turns to you with a determined look, 

ready to give you a pep talk about the challenges ahead. 

You can almost feel the excitement in the air!




---





### **Task 1: Making Professor Oak Explain the Main Quest**



To guide players like a true mentor, 

Professor Oak needs to explain the main quest. 

Let’s add a new method to his class that allows him to do just that.



1. **Create the **`**explainMainQuest()**`** Method:**
2. - Inside the `ProfessorOak` class, create a new method called `explainMainQuest()`.
  - This method should take a reference to the `Player` object as its parameter.
3. **Interact with the Player:**
4. - Use the following dialogues to script out the interaction between Professor Oak and the player. Remember to make each line feel personal and engaging!



**Professor Oak’s Dialogues:**```cpp
Professor Oak: "Ah, [player.name], let me tell you about your grand adventure that's about to unfold!"

Professor Oak: "Becoming a Pokémon Master is no easy task. It demands courage, strategy, and sometimes a little bit of luck."

Professor Oak: "Your main mission is to collect all the Pokémon Badges and defeat the Pokémon League. Only then can you challenge the Elite Four   and aim for the    title of Champion."[player.name]: "Wait, isn’t that just like every other Pokémon game?"

Professor Oak: "No breaking the fourth wall, [player.name]! This is serious business."

Professor Oak: "To achieve this, you must capture new Pokémon, battle wild creatures, challenge gym leaders, and keep your Pokémon healthy at the PokeCenter."

Professor Oak: "Remember, you can only carry a limited number of Pokémon. Choose wisely who you want on your team!"[player.name]: "Piece of cake, right?"

Professor Oak: "Ha! That’s what everyone thinks. But the path to becoming a Champion is filled with obstacles. Lose a battle, and it’s back to the start!"

Professor Oak: "So, what do you say? Are you ready to embark on this epic journey to become the next Pokémon Champion?"[player.name]: "Ready as I’ll ever be, Professor!"

Professor Oak: "That’s the spirit! Now, your journey begins. Remember, it’s not just about battling—it’s about forming bonds with your Pokémon. Go, Trainer, the world of Pokémon awaits you!"

Professor Oak: "Oh, and about the actual game loop… let’s just pretend I didn’t forget to set it up. Onwards!"
```






---





### **Task 2: Adding Controlled Interaction with **`**waitForEnter()**`

Dialogs should feel like real conversations where the player has time to read each line. 



To achieve this, 

you will add a function that pauses the game, 

allowing players to press Enter before moving on to the next line.



1. **Create **`**waitForEnter()**`**:**
2. - Just below `using namespace std;`, create a function called `waitForEnter()`.
  - This function will use `cin.get()` to pause the execution and wait for the player to press Enter.
3. **Implement **`**waitForEnter()**`** Throughout the Code:**
4. - Call `waitForEnter()` after each important line of dialogue. This will ensure the player can read everything at their own pace and keep the conversation immersive.






---





### **Task 3: Clearing the Console with **`**clearConsole()**`

During intense conversations and battles, 

the screen can become cluttered with text. 



To keep the game visually clear, 

you need a function to clean the screen whenever necessary.



1. **Create the **`**clearConsole()**`** Function:**
2. - Just above `waitForEnter()`, create a new function called `clearConsole()`.
3. **Call **`**clearConsole()**`** Where Needed:**
4. - Use `clearConsole()` before displaying new, significant blocks of text or whenever the screen starts feeling cluttered. For example, call it before the main quest explanation to clear any prior clutter.




---





### **Expected Output**



As you implement these changes, 

the gameplay will flow much more smoothly. 



The player will receive information in a paced manner, 

allowing for a deeper, more engaging experience. 



Here's an example of how the interaction might look:



```cpp
Professor Oak: Ah, Ash, let me tell you about your grand adventure that's about to unfold!

(Press Enter to continue...)

Professor Oak: Becoming a Pokémon Master is no easy task. It demands courage, strategy, and sometimes a little bit of luck.

(Press Enter to continue...)

Professor Oak: Your main mission is to collect all the Pokémon Badges and defeat the Pokémon League. Only then can you challenge the Elite Four and aim for the title of Champion.

(Press Enter to continue...)

Ash: Wait, isn’t that just like every other Pokémon game?

(Press Enter to continue...)

Professor Oak: No breaking the fourth wall, Ash! This is serious business.
...
```





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
