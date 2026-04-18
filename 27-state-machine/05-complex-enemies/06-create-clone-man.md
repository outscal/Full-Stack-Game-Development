> In your ***Complex-Enemies-Setup**** *branch complete the following tasks, commit all these changes and submit the link of your branch for this assignment.



**Tasks:**

- Create a new Enemy called "**Clone Man**".
- He should be having the following states:- **Idle**
  - **Patrolling**
  - **Chasing**
  - **Shooting**
  - **Teleporting**
  - **Cloning**
- When this enemy is killed by the player, **it creates 2 clones of itself with full health**.
- the 2 new cloned enemies will be teleported to some random place upon creation and enter the chasing state.
- The cloned enemies should be visibly different in the game, **highlight them with a different color**.
- Each original Clone Man will be able to clone **twice** **only**. The code should be flexible enough to increase or decrease this number as per requirements.
- Here is a preview of how the gameplay should look like:

 


<iframe src="https://www.loom.com/embed/2831b39990ef48c9ba6424b5219ef4ce" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





![](//outscal.github.io/Full-Stack-Game-Development/images/e83d4943f1c08bb8.png)



- When the enemies which are clone twice killed by the player, they should not replicate themselves further and shall remain dead.

![](//outscal.github.io/Full-Stack-Game-Development/images/97821ab8d4c4b406.gif)



- Create a `**CloneManStateMachine**`. Use the generic state machine for handling state management for Clone Man.
- Create a `**CloneManController**` to represent your new enemy.
- Create a new Level and add multiple Clone Man in this Level. 
- Share the link of the correct branch as submission and a gameplay video of your game as well
