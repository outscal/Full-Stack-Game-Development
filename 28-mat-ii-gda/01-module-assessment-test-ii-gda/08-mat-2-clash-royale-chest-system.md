# **Create a Chest system like Clash Royale**

**(Assets can be placeholders)**

![](//outscal.github.io/Full-Stack-Game-Development/images/c288f55b376f6cde.png)



## **Currencies**!


---

1. **Coins**
2. **Gems**

![](//outscal.github.io/Full-Stack-Game-Development/images/59d3af59a4d8db04.png)



## **Chest Types**


---

- Every number here should be flexible to change by the designers and should not be hard coded!

![](//outscal.github.io/Full-Stack-Game-Development/images/4714c61d9df79040.png)



## **Chest Slots (for storing chests)**


---

- There will be a scrollable dynamic list of slots for chests with a minimum of 4 slots where we can place chests.
- Create a Button, which will generate random chests in the empty slot after click. (there will be different types of chests, read further to get a better idea)
- When the chest is getting added, the timer of the chest will not start. So you need to click on the chest then one pop-up will come, and on that pop up there will be two buttons on the pop-up.

1. - **Start Timer button** → Which will start the respective time for the chest depending upon the time. For starting the timer to unlock there won't be any cost.
  - **Unlock with Gems button** → Which will directly unlock the chest without the timer spending particular gems cost, for understanding more about cost read further.

- If slots are full → Pop up saying slots are full will appear.!

![](//outscal.github.io/Full-Stack-Game-Development/images/603fc3fdd3fc0989.png)



## **Chest Structure**!


---

## ![](//outscal.github.io/Full-Stack-Game-Development/images/989e2dabf9a3ab35.png)

- Chests can be

1. 1. Locked (Timer Haven't started)
  2. Unlocking (Timer is running on the Chest)
  3. Unlocked but not collected (Timer is finished → Tap to collect reward state)
  4. Collected (rewards have been collected and the chest leaves the slot that it was occupying)

- Rewards will be received depending upon the type of the chest
- We can start unlocking only one chest at max, which means if the timer is on for any of the chests, we can't start unlocking other chests
- Just like the below image, we can open any unlocking chest by spending gems. The cost for that will be → 1 Gem for every 10 mins, which means suppose on the chest we have 30 mins left then cost should be 3 Gems, if 1 Hour is remaining then cost should be 6 gems, likewise. This cost of gems should also reduce as time is reduced.
- Always take a ceil while calculating the cost , e.g. minutes are 11 ⇒ 1.1 Gem then consider the cost as 2 Gem. if minutes are 29 , then gems will be 2.9 , take cost as 3 Gems , always take a ceil.
- If gems are not enough to skip the timer then there should be one pop up saying that.
- Implement an **undo** option if you want to revert your decision of spending gems for unlocking a chest through gems.



## **Queueing of Chest Opening**


---

1. Chests will be added in a queue to start unlocking after the current chest's timer runs down to 0 (that is unlocking)



## **Focus/Evaluation**


---

1. Code quality
2. Architecture
3. System design (make things flexible, modular and scalable)
4. Use of Design Patterns



## **Submission**


---

1. Commit your code frequently (every ~30mins with meaningful commits)
2. Push your code to GitHub at the end of every 3hr session
3. At the end of day, record small 2 min video just telling your progress.
4. Submit your final project repository + readme file + small video showing the gameplay working and explaining your code architecture implementation in a 5min loom video




---



## **[Note]**

- The deadline for completing this assignment is of 4 days from the day you start.



## [Things to note while pushing your code in Github]

- Add proper readme file in your GitHub repo.
- 1. Create a video of the gameplay and add it.
  2. Explain what your game is about.
  3. Give an architectural overview of scripts being used in your game (You can create a block diagram on ***miro*** or any similar platform)
  4. Mention all the Design Patterns and Programming Principles you have used in the game and also mention where you have used them.
  5. The hierarchy of your scripts and assets should be properly maintained.
- Make sure to create branches for all the individual features you have implemented.
- Merge all the feature branches to the main/master branch.



## Assets & Resources


---

- **Outscal Asset Library** → [Click Here](https://drive.google.com/drive/folders/1XyofqfzoSdIE5coDiYUnrMW7Tj3Fwq8z?usp=sharing)
- Feel free to use your own assets from the internet and make your game look unique.
- Some of the widely used sites
- 1. [Click Here](https://www.spriters-resource.com/game_boy_advance/pokemonemerald/), [Click Here](https://assetstore.unity.com/packages/2d/free-2d-mega-pack-177430?aid=1101lPGj&utm_source=aff), [Click Here](https://itch.io/game-assets)
  2. Please feel free to use any assets you want.
