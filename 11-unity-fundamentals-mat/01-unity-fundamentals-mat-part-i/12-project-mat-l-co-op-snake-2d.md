# **MAT - I → Co-Op Snake 2D**

©️ Game Design by Malhar Devasthali 😜

**[Note]**

- **The deadline for completing this assignment is of 4 days from the day you start.**

**[Assets]**

- Use your own assets from the internet.
- Some of the widely used sites
  1. <a href="https://www.spriters-resource.com/game_boy_advance/pokemonemerald/" target="_blank">Click Here</a>,
  2. <a href="https://assetstore.unity.com/packages/2d/free-2d-mega-pack-177430?aid=1101lPGj&utm_source=aff" target="_blank">Click Here</a>
  3. Please feel free to use any assets you want

**[Visual Reference]**

- <a href="https://www.youtube.com/watch?v=KcpRyIFU7Eg" target="_blank">https://www.youtube.com/watch?v=KcpRyIFU7Eg</a>

**[Task]**

- Core Snake Game Functionality

  1. You might have played our childhood favorite snake game on a keypad phone, if not just watch the video shared in reference 😐
  2. Implement core functionality of a snake where snake should move in all 4 directions
     ⬆️ ⬇️ ⬅️➡️
  3. Implement screen wrapping for all the directions ⬆️ ⬇️ ⬅️➡️

     ![instructions](<https://outscal.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F23b6b61f-0b60-4c33-9f45-ac5e7a270ee8%2FComponent_1_(1).png?table=block&id=29d066b1-1838-4b25-95ed-95ef2e430a3e&spaceId=8c9f7b97-3438-434a-b8ca-0a53eb7262ea&width=1250&userId=&cache=v2>)

  4. Snake should die after biting himself.
  5. Snake should grow after eating food.

- Power-Ups
  1. Implement 3 Power-Ups
     1. Shield → Snake will have a shield and the snake will not die when the shield is active.
     2. Score Boost → Snake will gain 2x Score Points for each mass-gainer food.
     3. Speed Up → Snake should increase the speed after collecting this power-up. (Hard to implement, if stuck continue with other implementations)
  2. Cool Down For power Ups
     1. Have 3 Sec. Cooldown for each powerup, make this cooldown time flexible
  3. Power-Up spawning
     1. Spawn the random power-up at a random time interval of time
- Foods
  1. There will be two types of food in Our game
     1. Mass Gainer → Which will increase the length of sneak.
     2. Mass Burner → Which will decrease the length of sneak.
     3. Make sure to make every implementation flexible, which means by how many units you want to increase/decrease the length.
  2. Food spawning
     1. Every food should automatically get destroyed after some time if not eaten.
     2. Spawn the random foods at a random time interval of time.
     3. If snake size is already low then you should not place Mass Burner as full.
- Co-Op
  1. Here comes spice ©️ Malhar's Game Design 😎
  2. Implement a two-player game where one sneak will move using WASD and another will move using arrow keys. ⬆️ ⬇️ ⬅️➡️
  3. If Snake A bites snake B then snake B will die, and vice versa.
- Scoring
  1. Mass Gainer Food will increase the score.
  2. Mass Burner food will decrease the core.
- UI
  1. Implement Basic UI like death, Win, Score, Lobby UI for the game.
  2. Implement Pause/Resume, Restart and Quit Buttons.

**[Things to note while pushing your code in Github]**

- Add proper readme file in your GitHub repo.
  1. Create a video of the gameplay and add it.
  2. Write 1 line on what your game is about
  3. Write down the features you have implemented in the game.
- Make sure to create branches for all the individual features you have implemented.
- Merge all the feature branches to the main/master branch.
