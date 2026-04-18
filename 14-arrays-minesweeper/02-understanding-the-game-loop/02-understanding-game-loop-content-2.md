In this lesson, you'll learn about game states in games.

Let's start with understanding: 

*What exactly is a state?*



## Understanding Game States


---

In ***PONG****,* there were no states, it just had a single Gameplay screen.

But what if you wanted to add a Main Menu in the game or a Game Over screen after a certain score like 50.

This is when you can segregate the game into different game states like: Main Menu or Game Over.

While all games use a game loop, the states within the game loop can be totally different for each game!

Let's see this with ***Flappy Bird’s*** example.



## Flappy Bird


---

![Flappy Bird](/Full-Stack-Game-Development/images/4e4740d94a61e86f.gif)

**Flappy Bird Gameplay**

Let's break down how Flappy Bird flows:

1. **Splash Screen & Loading** 🎨
2. - That iconic bird logo appears
  - Game loads all those pipes and backgrounds
3. **Main Menu** 📋
4. - Simple "Start" button waiting for your tap
5. **Gameplay** 🐦
6. - Bird flaps, pipes move
  - Physics engine works its magic
  - Score keeps counting
7. **Game Over** 💫
8. - Oops! Hit a pipe?
  - Try again or head back to menu.



## Minesweeper: A Different Take on States


---

Now, let's see how Minesweeper uses these same concepts differently!

1. **Splash Screen** 💫
2. - Shows the branding.
3. **Main Menu** 🎮
4. - Clean menu with "Play" and "Quit" buttons.
5. **Gameplay** 💣
6. - Clicking cells, placing flags, timer ticking, everything related to the gameplay.
7. **Exit** 🚪
8. - One press of ESC and you're out

We have already setup a Game Loop, you don’t need to create it again.

Other than the Game States, nothing is different in the game loop than the previous game loops that you have created in other projects.



> **TODO:** 
> ✅ Go through the `GameLoop.cpp` file.



Now that you've explored the Game Loop and Game States, 
you'll transition to a different state in the next lesson!

**Get ready to bring your games to life! 💪**
