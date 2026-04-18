# **Boss Fight !!!**



Now it is time for your final challenge. The most difficult one. 

You must defeat the Boss of all enemies... they call it the **Infernoth** named after the fact that this dude can breath fire. 

![](/Full-Stack-Game-Development/images/038a3d8c0196b156.gif)



Its time to make a Boss Level !!!  

Implementing the complex behavior of this enemy is as difficult as defeating it in a battle, But it is much easier for you if you apply your knowledge of state machines to create this creature.

You can name this creature whatever you like, its is your Frankenstein.

![](/Full-Stack-Game-Development/images/0a000f20699be300.gif)



Create a state machine for the Boss enemy:** Infernoth** in your game which include all the states given below:

- **Idle State**: Initially dormant, the **Infernoth** awaits the player's approach.
- **Detection State**: When the player enters its detection radius, the **Infernoth** transitions to this state and chases the player.
- **Roaring Intimidation**: The **Infernoth** can initiate a roar to intimidate the player, causing nearby objects to tremble. This state doesn't involve direct attacks but increases the player's fear, making them temporarily slower.
- **Quadruple Attack**: The **Infernoth** uses its four arms to perform a powerful melee combo, each arm executing a different swing. This attack is devastating but has a wind-up, allowing the player a chance for running away to dodge.

![](/Full-Stack-Game-Development/images/6bce4d73e66a4f82.gif)



- **Fire Breath**: The Colossus breathes out a torrent of fire, covering a wide area in front. The player needs to dodge or find cover to avoid getting severely burnt.
- **Adaptive Defense**: The **Infernoth** enters a defensive stance, regenerating health and becoming briefly invulnerable. The **Infernoth **can only enter this state twice during a single battle. 
- **Teleportation**: When the **Infernoth** is Idle for a certain duration and no action takes place, the **Infernoth** will teleport to a random place on the map and may surprise the player.
- **Summoning Minions**: Periodically, the Colossus summons smaller monsters/enemies to aid in the fight, increasing the challenge for the player.
- **Ultimate Chaos**: When the boss is low on health, it enters a state of desperation, becoming faster and more aggressive. In this state, the boss combines all its attacks in a chaotic manner, performing a rapid succession of melee strikes, fire breaths, and teleports, creating an immensely challenging phase for the player to survive. It is advised to the player to solely focus on survival when enemy is in this state rather than attacking.

![](/Full-Stack-Game-Development/images/e574eae969814195.gif)
