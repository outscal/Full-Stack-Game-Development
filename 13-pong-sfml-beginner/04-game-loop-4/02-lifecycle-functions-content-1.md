In this lesson, you'll learn about lifecycle functions - the key steps that keep your game running smoothly.



> 📖 🎮 **GAME DEV DICTIONARY **
> ***Lifecycle Functions***: "A sequence of functions that execute during each frame of your game loop"



Different functions handle these tasks

How do you think a game processes everything happening on screen? Let's break it down!



## Understanding Lifecycle Functions


---



Each frame of your game needs to handle different tasks. Different functions handle these tasks.

Each function has a distinct responsibility:

**Initialize**

- Sets up the environment (e.g., game window, event manager)

**Poll Events**

- Captures every player action
- Processes keyboard and mouse inputs

**Update**

- Updates object positions
- Checks for collisions
- Processes game logic

**Render**

- Clears the previous frame
- Redraws all game elements
- Displays the updated screen



> TODO: 
> ✅Create `GameLoop.h` file in `Core/Header` folder 
> ✅Create `GameLoop.cpp` file in `Core/Source` folder 
> ✅Create all the Lifecycle functions



In the next lesson, you'll implement a game loop with a structured lifecycle that:

- Initializes the game environment
- Processes inputs
- Renders visuals
