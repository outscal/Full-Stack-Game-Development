> Create a **Bonus-Solution** branch and complete the following tasks, commit all these changes and submit the link of your branch for this assignment.



In this exciting next side-quest you will be making new gameplay features and a State Machine for your Player!

Before that, lets arm your player with some new gameplay elements:



![](https://tenor.com/view/lets-go-keanu-reeves-keanu-lets-goo-john-wick-lets-go-gif-24268126.gif)



## 1) Freeze Bombs


---

- Create an ability for your player to throw **Freeze Bombs** on the ground.
- These bombs when thrown on the ground will detonate after 5 seconds.
- All enemies inside its proximity will be frozen for 10 seconds and can be killed while they are frozen.
- Your player will not have any freeze bombs in its inventory when the game begins but the bombs will be scattered somewhere in the game as collectibles and can be picked up and used.

![](https://tenor.com/view/freeze-squidward-gif-5336675.gif)



## 2) Teleportation Pads


---

- There will be a few pairs of teleportation pads in the game which can be used by Player ONLY
- Once player steps on these it will be teleported to another pad somewhere else. 
- This can be used as a strategic weapon to surprise enemies and perform instant sneak kills or even to run away when cornered by enemies.

![](https://tenor.com/view/dragon-ball-z-dbz-goku-good-bye-bye-gif-5155252.gif)



## 3) Health Pickups


---

- While dealing with so many tough enemies, your player will need to heal in between the fights.
- Create some health pickups and place them strategically in your levels.
- A small amount of player health should be increased instantly after picking up health packs.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/11_17_2023__07_23_01.png)



## 4) Player State machine


---

- At this point, your player is going about doing a lot of things now, it might get a little messy like that spaghetti code we discussed during the start of this module.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/11_17_2023__07_33_40.png)



- You will must implement a state machine for your player as well to keep your code organized.
- Use knowledge of state machines you gained till now to make an independent state machine for your player which takes care of various player states and transitions.
