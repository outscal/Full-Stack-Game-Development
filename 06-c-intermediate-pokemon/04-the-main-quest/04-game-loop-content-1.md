Imagine the heart of a human body. 

It beats steadily, pumping blood and keeping the body alive and functioning. 

Without the heartbeat, the body wouldn’t know what to do, and everything would stop.



![c++](https://media1.tenor.com/m/OCutoOD37dwAAAAC/heart-heartbeat.gif)



Now think about a game. 

The game also has a "heartbeat" that keeps everything alive and responsive. 

This heartbeat is called the **game loop**.



Just like how your heart beats regularly.

The game loop runs continuously, making sure the game updates, responds to your input.

And displays what's happening on the screen.





# Game Loop as a Turn in a Board Game


---



Another way to look at the game loop is to compare it to a board game. 

Imagine playing a game where each player takes turns. 

During your turn, you make decisions, move your pieces, and then wait for the other players to take their turns.



![chess](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_28_2024__03_35_03.png)



In a video game, it works similarly, except the game is constantly taking "turns" through the game loop. 

During each turn (or cycle of the loop), the game updates the world, checks for input, and redraws the screen. 

This happens over and over at a fast pace, keeping the game running smoothly.



# What is Game Loop ?


---



A **game loop** is a core part of any video game. 

It’s a sequence that runs repeatedly to keep the game going.

Its job is to keep the game alive and interactive, checking for player input, updating the game’s state, and rendering the game to the screen.



Without the game loop, your game would not respond to input or display changes. 

Everything would just freeze, like a board game where no one ever takes their turn.





## Why Every Game Needs a Game Loop



Every game, from the simplest mobile app to the most complex console game.

Needs a game loop to function. 



Without it, there would be no movement, no interaction.

And no way for the game to know when something happens. 



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_13_2024__11_45_32.png)



The game loop keeps everything flowing smoothly.

Making sure the game responds to the player and updates the world continuously.





# Breaking Down the Game Loop


---



Let’s take a look at the main parts of a game loop and what each one does:



Initialization : Setting the stage

When you start a game, it first needs to set everything up. 

This is called the **Initialization** phase. 



In this part, the game prepares all the characters, objects, and settings. 

It’s like setting up a chessboard before the game begins. 

All the pieces need to be in the right place.



Update : The Brain of the Game   

Once the game is set up, the **Update** phase takes over. 

This is the part where the game checks if anything has changed. 



Did the player press a button? 

Did an enemy move closer? 

Are the physics working correctly?



The update handles things like:

- **Player Input**: What buttons or keys did the player press?
- **AI Behavior**: How do enemies move or react?
- **Physics**: How do objects move or collide?
- **Game State**: Has the player won or lost, or did something new happen in the game?

This phase is the brain of the game, making sure everything is in order.



Render : Showing the Game

After the game updates, it needs to show the new state of the game on the screen. 

This is where the **Render** phase comes in. 

It’s like drawing the game on a blank canvas.



In this phase, the game displays everything on the screen based on what has changed:

- If the player moved, the character’s position is updated.
- If an enemy was defeated, it disappears.
- If the score changed, it shows the new score.



The render phase is what makes the game look alive and interactive.



Wait/Sleep : Keeping the Game Smooth

If the game loop runs too fast, everything will move too quickly to follow. 

If it’s too slow, the game will feel sluggish. That’s why there’s a **Wait/Sleep** phase.



This phase controls how fast the game loop runs, making sure the game runs at a steady and smooth pace. 

It keeps the game from speeding up too much or slowing down.



And then, it starts all over again. 

This cycle continues, keeping the game alive, just like a heartbeat or taking turns in a board game.



Whether you’re battling Pokémon or exploring new worlds.

The game loop makes sure your game responds to every action.  



In the next chapter, we’ll bring this game loop to life.

And start turning your ideas into a real game.  



Stay tuned—your journey is just beginning!



**Great Job🎉!**
