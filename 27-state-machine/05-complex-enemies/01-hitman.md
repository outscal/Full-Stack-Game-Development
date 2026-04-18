> Before you begin this Chapter, please checkout the following branch: [***Complex-Enemies-Setup***](https://github.com/outscal/AGD_StateMachine/tree/Complex-Enemies-Setup)



Your code has evolved a lot since you started. Now let's move on and use all this good architecture that you have created to add some more complex enemies in your game.

 ![](/Full-Stack-Game-Development/images/9ee526dd5157785b.jpg)



The next enemy that we are going to create is called Hitman. This guy must have the following states:

- Idle
- Patrolling
- Chasing
- Shooting
- Teleporting



The patrolling behavior and chasing behavior will be same as it is for Patrol Man. But whenever Hitman shoots at player he will teleport at some random place and continue chasing and attacking player from there. Hitman adds an element of surprise by teleporting after shooting. This creates an engaging challenge for players.


<iframe src="https://www.loom.com/embed/d3891cbd0e2242f3a7182529cd38b9c3" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





**Pick up a pen & paper**Create a state diagram for the Hitman's State Machine.



Let's put our game development skills to work and bring this formidable enemy to life!
