Let's break down the UI (User Interface) in Mr. Blocks.

We've got two main UI screens:

1. Main Menu UI
2. Level UI
3. Game Over UI

Let's break these down and see how they work together!



## Main Menu UI


---

This is what players will see first when they open the game.
It's simple but effective.



![Main Menu](/Full-Stack-Game-Development/images/3734876ba4a1a469.png)

**Main Menu**



It has two options:

- Play: Starts the first level
- Quit: Quits the game



Now, let’s see the UI when the player starts the game.



## Level UI


---

This appears during gameplay and includes:



![Level UI](/Full-Stack-Game-Development/images/467dc8db4c254aae.png)

**Level UI**

- Level Number Display



It shows the current level number in the top left corner.



## Game Over UI


---

![Game Over UI](/Full-Stack-Game-Development/images/71d41ea75ac9a63d.png)

**Game Over UI**



It appears when you lose a level or complete the game. It shows:

- "Game Over!" (if you lose a level)
- "Game Complete!" (if you complete all levels)
- Two buttons:
- - Restart: Restarts the current level
  - Home: Returns to Main Menu



## How It Works


---

Here’s how these UI screens will make the game interactable:

1. Game starts → Main Menu UI
2. Press Play → Level 1 starts (Level UI)
3. Complete a level → Next level loads
4. Die in a level → Game Over Screen appears
5. Complete all levels → Game Over Screen (with win message)



That's it! You now know how Mr. Block's UI works.

Next, you'll start building the Level UI.
