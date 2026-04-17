Let’s make every bite your snake take an event to remember!

Sounds cute, right? 



**Can You Visualize Food Consumption in Your Snake Game?**



In the classic Snake Game, when the snake eats food, you can watch it travel through its body until a new segment pops up at the tail.

![gif]()

![gif](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_02_2024__12_08_28.gif)



## **Watch the Food Travel Through the Snake**


---

In this assignment, you will add a cool feature where you can see the food travelling through the snake’s body!  

When your snake eats a piece of food, it will move through the snake's body parts until it reaches the end, where a new segment will be added.



**How does It Work?**

- **Step 1:** When the snake eats something that increases its size, start an animation to show the food moving through each segment.
- **Step 2:** The food moves one segment at a time with a slight delay, creating a smooth visual effect.
- **Step 3:** Once the food reaches the end, a new segment is added to the snake’s body.



**What are the Visual Approaches?**

- **Change Size of Node**: Temporarily enlarge the node to show the food passing through.
- **Change Color**: Change the node's colour to indicate the presence of food.
- **Create a New Sprite**: Use a distinct sprite to represent the food moving through the snake.



**Brainstorm the implementation for the animation logic.**

- **Update Visuals of One Node at a Time:** Implement a delay between each node update to create the effect of movement.
- **Sequential Animation:** As the food moves through each segment, update the visuals to reflect the temporary changes (size, color, or sprite).
- **Add the new segment:** Once the food reaches the position where the new segment should be added, make it happen!



**Your Task:** Implement this feature and make your snake game even more dynamic and fun to play. 🎨



> **TODO:**
> ✅Create animation when snake eats food.
> ✅Use `TimeService` for delay between each node update to show movement.



Time to make your Snake Gobble-Gobble!!


![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_27_2024__14_24_55.gif)





## BONUS ASSIGNMENT SUBMISSION INSTRUCTIONS


---



1. **Branch Creation:** If you haven't already, create a branch named `**Bonus-Snake-Eat-Animation**` from your main branch in your forked repository.
2. **Bonus Implementation:** Work on your bonus assignment within the `**Bonus-Snake-Eat-Animation**` branch. Ensure all changes and implementations related to the bonus assignment are committed to this branch.
3. **Creating a Pull Request (PR):** Once you've completed the bonus assignment, create a Pull Request (PR) from your `**Bonus-Snake-Eat-Animation**` branch to your main branch. This is done within your forked repository, not the upstream repository.
4. **Submission Link:** Submit the link to your Pull Request as the submission link for the bonus assignment.



**This PR will be shared with Code Reviewers who will share the feedback in the PR itself.**



**Important Reminders:**

Ensure all bonus work is confined to your forked repository. The parent repository, also known as the upstream repository, should not be modified or used for bonus assignment submissions. Avoid pushing or merging commits directly to any branches in the upstream repository. By following these steps, your bonus assignment will be neatly organized, easily reviewable, and ready for submission
