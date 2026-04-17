Imagine your player moving through the game when suddenly two different types of food spawn on the screen. 

Which one should they eat?



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_27_2024__19_04_17.gif)

**The Thrill of Choice: Gainer vs Burner**



This dilemma adds a whole new layer of strategy and fun to the game!



## The Fun of Player Dilemma


---



**Your Task: **Implement a dual food spawning algorithm where Gainer and Burner food items appear simultaneously. Also, spawn Alcohol and Poison after every five regular food spawns.



You will categorise your food items into two main types: **Gainers** and **Burners**.

Plus, for an extra twist, **Alcohol** and **Poison** will spawn after every five regular food items. 



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_28_2024__06_15_37.png)



**Types of Food**

1. **Gainer (Insertion)**: These are the traditional food items that increase the size of the snake. 
2. **Burner (Deletion)**: These food items decrease the size of the snake. (Note: These foods won't spawn if the snake is at its minimum size until it grows larger.)
3. **Special Items: **Alcohol and Poison



Think of it like this:

Your snake is approaching two food items. One will make it bigger, and the other might shrink it. 

Which one to choose? This decision-making process adds an exciting strategic element to the game!



How can you approach it?

- Implement a function to randomly spawn food items & ensure that both a Gainer and a Burner spawn simultaneously at random positions.
- Track the number of food items spawned & after every five regular food items spawn Alcohol and Poison.
- Categorize your existing food items into **Gainers** and **Burners**.



> **TODO:**
> ✅Spawn Gainer & Burner food items simultaneously.
> ✅Spawn Alcohol and Poison after every five regular food spawns.



## *With great power comes great responsibility*
*- SPiderman*



> **💡Tips:**
> **Balance the Game**: Ensure a fair mix of Gainers and Burners for a challenging experience.
> **Document Your Work**: Keep notes on your implementation and challenges for troubleshooting.
> **Test, test, and test again.** To make sure they are fun, challenging, and bug-free.



This is your chance to add an exciting new twist to your snake game. 

Implement this different food spawning algorithm and watch your game become more engaging and fun!

**Go For It! 🏎️**



## BONUS ASSIGNMENT SUBMISSION INSTRUCTIONS


---



1. **Branch Creation:** If you haven't already, create a branch named `**Bonus-Gainer-Burner**` from your main branch in your forked repository.
2. **Bonus Implementation:** Work on your bonus assignment within the `**Bonus-Gainer-Burner**` branch. Ensure all changes and implementations related to the bonus assignment are committed to this branch.
3. **Creating a Pull Request (PR):** Once you've completed the bonus assignment, create a Pull Request (PR) from your `**Bonus-Gainer-Burner**` branch to your main branch. This is done within your forked repository, not the upstream repository.
4. **Submission Link:** Submit the link to your Pull Request as the submission link for the bonus assignment.



**This PR will be shared with Code Reviewers who will share the feedback in the PR itself.**



**Important Reminders:**

Ensure all bonus work is confined to your forked repository. The parent repository, also known as the upstream repository, should not be modified or used for bonus assignment submissions. Avoid pushing or merging commits directly to any branches in the upstream repository. By following these steps, your bonus assignment will be neatly organized, easily reviewable, and ready for submission
