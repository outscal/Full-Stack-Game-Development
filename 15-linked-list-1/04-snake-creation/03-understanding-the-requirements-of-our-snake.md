**DRINK WATER 🥛!! LOTS OF BRAINSTROMING AHEAD 🤯🧠!!**

Before we talk about your digital snake, let's talk about real snakes. 

You must know how they move, eat, grow and die.



Now, let's pause for a moment and imagine how your digital Snake will move, eat food, grow its size, and meet its end, while also considering how real snakes behave.



Brainstorm thoroughly before starting to create. Gathering requirements constitutes 80% of the work, while coding is just 20%. 

Once you have a clear roadmap, the actual implementation becomes very easy.



Ready to brainstorm?


Hint Inside. 🙃

![Solving Problems: Snake Game | Rodrigo de Oliveira](https://d33wubrfki0l68.cloudfront.net/e68b91955407f19cded1eca7e6f04c0bf7447418/3c13d/assets/img/posts/solving-problems-snake-game/gameplay.gif)




The snake in your game starts with some limited body parts, with the front one as its **head**. 

As it eats food, it can grow or shrink by adding or decreasing body parts according to the food it eats. 

This dynamic growth and shrinking mechanism adds an exciting layer to the gameplay experience.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__06_01_27.jpg)

***Kind of your Snake***


## understanding key features of the snake game


---

1. **Snake's movement occurs on a grid-based screen:**
  
  **What does it mean?🤨**

- - Think of your game like a big board game. The snake's body parts are like game pieces on this board, each with their spot marked by coordinates (x, y).
  - In each frame of the game, the snake moves based on its current direction. This movement is achieved by updating the coordinates (x, y) of each part of the snake's body.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__06_01_58.png)

***Snake and Food in Grid***



1. **Player will score points by feeding the snake different types of food:**
  
  Have a look at this video:

![Image](https://media.discordapp.net/attachments/823251706044481619/1236226021724782664/7fa34ff0-8d60-4eab-9087-2543e3cb9b86.png?ex=66373cb3&is=6635eb33&hm=c5f72bd6d4606ecdc319399a746e64aa9ddb84a88f6c96b2b0c056499496d48d&=&format=webp&quality=lossless&width=717&height=374)

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__18_03_49.gif)



**Noticed something? 🤔**

- - ***Snake's score increases when it eats food***, so you need to keep a record of points and update it whenever the snake eats food.



1. **Players control the snake's movement using the keyboard**. The snake can move in four directions: *UP, DOWN, LEFT, and RIGHT. *
  
  **Track your player 🕵️‍♂️**

- - You keep track of the player's keyboard inputs to see if they've pressed *UP, DOWN, LEFT, or RIGHT*. Based on that, you adjust the snake's direction because, let's face it, the snake won't turn on its own! 
  - It's all about giving the player control in steering the snake through its tasty adventure.

![Image](https://media.discordapp.net/attachments/823251706044481619/1236226021724782664/7fa34ff0-8d60-4eab-9087-2543e3cb9b86.png?ex=66373cb3&is=6635eb33&hm=c5f72bd6d4606ecdc319399a746e64aa9ddb84a88f6c96b2b0c056499496d48d&=&format=webp&quality=lossless&width=717&height=374)

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__18_04_49.gif)

***Snake moving in different directions***



- **If the snake ends up eating itself, it's game over.**
- - You've to store the positions of the snake's body parts so that you can check if the collision point matches any body part of the snake.



![Image](https://media.discordapp.net/attachments/823251706044481619/1236226021724782664/7fa34ff0-8d60-4eab-9087-2543e3cb9b86.png?ex=66373cb3&is=6635eb33&hm=c5f72bd6d4606ecdc319399a746e64aa9ddb84a88f6c96b2b0c056499496d48d&=&format=webp&quality=lossless&width=717&height=374)

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__18_22_10.gif)

***Snake eats itself and gets dead***



- **The snake can move through walls but must wrap around to stay within the visible game area.**
  
  **Mathematician Snake🐍👨‍🏫**
- - When your snake reaches the edge of the screen, it does some math with its coordinates (x, y) to stay within the visible game area and ensure smooth movement. You will learn it in detail later.



![Image](https://media.discordapp.net/attachments/823251706044481619/1236226021724782664/7fa34ff0-8d60-4eab-9087-2543e3cb9b86.png?ex=66373cb3&is=6635eb33&hm=c5f72bd6d4606ecdc319399a746e64aa9ddb84a88f6c96b2b0c056499496d48d&=&format=webp&quality=lossless&width=717&height=374)

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__18_06_20.gif)

***Snake movement through the wall***



## UNDERSTANDING FOOD


---



**Different types of food bring unique effects to the snake:**

- **Junk Food:**
- 1. *Pizza, Cheese & Burger* are the junk food for Snake. 
  2. When the snake eats these food items, its size increases. This increases the chances of the snake dying by collision with itself!
- **Healthy Food:**
- 1. *Apple, Mango & Orange* are the healthy food in the snake game.
  2. Eating these food items decreases the snake's size. This makes it easy to play the game.
- **Alcohol:**
- 1. Changes the snake's direction to the opposite.
- **Poison:**
- 1. The snake shrinks to half its size.
  2. The second half disappears and is removed from the snake's body.



![Image](https://media.discordapp.net/attachments/823251706044481619/1236226021724782664/7fa34ff0-8d60-4eab-9087-2543e3cb9b86.png?ex=66373cb3&is=6635eb33&hm=c5f72bd6d4606ecdc319399a746e64aa9ddb84a88f6c96b2b0c056499496d48d&=&format=webp&quality=lossless&width=717&height=374)

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__18_06_58.gif)

***Snake changing its size***



Don't worry if there's a lot to grasp about your snake game right now. You'll explore each detail later on.

Adding new features to your game or snake will be an exciting journey, and you'll go through important lessons along the way.


**See you in the next section!👋🏼**
