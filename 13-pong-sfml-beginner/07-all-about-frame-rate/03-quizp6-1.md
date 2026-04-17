# ⏳Quiz

quiz


## Questions


### Q1. What happens if your game is frame rate dependent?
- The game logic executes at the same speed regardless of the frame rate.
- The frame rate dynamically adjusts to the game’s logic.
- The game logic is tied to the frame rate, meaning faster frame rates cause the game to run faster. **(correct)**
- The game's visuals degrade if the frame rate exceeds a certain threshold.

### Q2. Delta time refers to the amount of time that has passed between the rendering of the ____ and the ____.
- previous frame; current frame **(correct)**
- game start; current frame
- first frame; last frame
- current frame; next frame

### Q3. Why is delta time important in game development?
- It ensures smooth rendering of visuals by synchronizing them with the GPU.
- It fixes performance issues by automatically adjusting the game logic to match the player's hardware.
- It helps synchronize animations but is unnecessary for other parts of the game.
- It allows game logic and movement to be independent of the frame rate, ensuring consistent gameplay across different systems. **(correct)**

### Q4. What would happen if you implemented delta time incorrectly, such as failing to reset it every frame?
- Objects would move at a constant speed, regardless of the frame rate.
- Objects would stop moving because delta time would remain stuck at zero.
- Delta time would accumulate, becoming increasingly large, causing objects to move erratically or unrealistically fast. **(correct)**
- Delta time would remain consistent, but game physics would be inaccurate.

### Q5. A game is running at an average frame rate of 60 frames per second (FPS). The player’s character moves at a speed of 300 units per second. Using delta time to make the movement frame rate independent, calculate how far the character moves in one frame.
- 10 units
- 5 units **(correct)**
- 50 units
- 20 units
