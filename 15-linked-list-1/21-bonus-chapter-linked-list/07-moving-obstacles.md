**Congrats, you've made it this far!! 🎉**



It’s time to level up the challenge with your final assignment! 

Aren't you bored with those static obstacles and thought of making these obstacles move? 

Moving obstacles are a more bigger threat than static ones, but they're still easier to handle than the unpredictable Hunter Snake! 😭



![gif](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_02_2024__12_20_42.gif)

***Moving Obstacles***



## Moving Obstacles: The Final Thrill! 🚧✨


---



Do you know why moving obstacles are so challenging? 

Because they require constant attention and quick reflexes. 🫨



**How can you make your obstacles move?**

You've already done something similar in Space Invaders when you moved your enemies left, right & down. 

Now, bring that movement to your snake game!



For the classic movement:

1. **Spawn** the obstacle at its starting point.
2. Move it to the **right** side of the screen.
3. Move it **down** a bit.
4. Move it to the **left** side of the screen.
5. Move it **up** a bit.
6. **Repeat** the cycle.



> To get help, refer to your previous material: [Classic Enemy Movement in Space Invaders](https://outscal.com/course/space-invaders/c-intermediate/enemies-1/classic-enemy-movement).



Let's explore two approaches to implement moving obstacles in your snake game.

1. **Point-Based Movement:** Define a looping path for each moving obstacle by creating a list (array/vector/STL::list/custom Linked List) of specific points or coordinates. This method offers diverse movement patterns but requires more memory. For example, imagine a single obstacle with four points: 

- - Point A: (x1, y1)
  - Point B: (x2, y2)
  - Point C: (x3, y3)
  - Point D: (x4, y4)

The movement logic would move the obstacle from A to B, then B to C, then C to D, and finally back to A, creating a loop.



1. **Bounded Movement:** Set a range or bounds within which the obstacle moves back and forth. It is simple and memory-efficient but restrictive in movement. To achieve this movement, you need the following:

- - **Variables** to set the left and right bounds for obstacles.
  - An **Enum** for the directions that the obstacles can move in.
  - A variable for the **distance** that the obstacle should move when going up & down.

(Note: You used this same method in Space Invaders)



Choose your approach based on your design and how you want the obstacles to behave.

Whether it's complex looping paths or simple back-and-forth motions, you have the creative freedom to bring your obstacles to life!



> **TODO:**
> ✅Implement moving obstacles using movement patterns.
> ✅Create properties such as speed etc for movement.



## *"I'm not afraid of dying. I'm afraid of not trying." *
*- John Wick*



**Ready for some action?**

![gif](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_27_2024__19_48_18.gif)



## BONUS ASSIGNMENT SUBMISSION INSTRUCTIONS


---



1. **Branch Creation:** If you haven't already, create a branch named `**Bonus-Moving-Obstacles**`** **from your main branch in your forked repository.
2. **Bonus Implementation:** Work on your bonus assignment within the `**Bonus-Moving-Obstacles**` branch. Ensure all changes and implementations related to the bonus assignment are committed to this branch.
3. **Creating a Pull Request (PR):** Once you've completed the bonus assignment, create a Pull Request (PR) from your `**Bonus-Moving-Obstacles**` branch to your main branch. This is done within your forked repository, not the upstream repository.
4. **Submission Link:** Submit the link to your Pull Request as the submission link for the bonus assignment.



**This PR will be shared with Code Reviewers who will share the feedback in the PR itself.**



**Important Reminders:**

Ensure all bonus work is confined to your forked repository. The parent repository, also known as the upstream repository, should not be modified or used for bonus assignment submissions. Avoid pushing or merging commits directly to any branches in the upstream repository. By following these steps, your bonus assignment will be neatly organized, easily reviewable, and ready for submission
