**How would you like your food served? 🍽️**



In this section, you'll find the details of the food spawning system. 

Your mission is to make food items appear in regular intervals, so your snake has a fair chance to eat them and grow!

Ready to make your game more exciting? **Let’s get cooking! 🍲**



![gif](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_20_2024__10_55_24.gif)



Food items appear at regular intervals in your game, much like a continuous buffet. 

Unlike static obstacles, these food items act differently as they appear and disappear to appear again.🐍✨



But how do you control when these food items appear?

Why not just set up an infinite while loop with a delay that keeps spawning the food item. We just want the food right.



Here's where the fun begins! 

The issue with an infinite loop is the lack of control. It will keep on spawning food even when the snake is dead.

That's why you need a system that gives you complete control over the spawning process.



Here’s what your food spawning system needs to do:

1. Food should spawn after a regular interval.
2. When new food spawns, the old food should be destroyed.
3. Food should start spawning when the level begins.
4. Food should stop spawning when the game player is dead.
5. You should have control over when to start and stop food-spawning.



Sounds easy, right? 

Think of the `**FoodService**` class as the master chef in your game’s kitchen, planning when and where each delicious food item appears.

This service ensures that food items pop up just in time for your player.



**See you in the next section!👋🏼**
