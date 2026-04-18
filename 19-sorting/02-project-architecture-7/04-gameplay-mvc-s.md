![ ](/Full-Stack-Game-Development/images/05be013777ee2fd5.png)



The Gameplay MVC architecture manages game logic, user input, and visualization.

The `GameplayController` updates the game based on input, and the views display these changes using the data managed by the `StickCollectionController`.



## **Gameplay & **Stick Collection**:**

- **Gameplay**: This is the main controller that manages the game’s background and creates the `StickCollectionController`. It orchestrates the overall gameplay experience.
- **Stick Collection**: This component manages a collection of sticks. It’s responsible for operations like adding, removing, or sorting sticks within the game.
- **Stick**: Each stick represents an individual data element, encapsulated as a rectangle shape view. These sticks are what you see drawn on the screen and are used to visualize sorting algorithms.



This Gameplay MVC architecture has been used in the previous Searching modules, so we hope this was easy to grasp. 

Now we know the foundation and it's time to do the interesting stuff!
