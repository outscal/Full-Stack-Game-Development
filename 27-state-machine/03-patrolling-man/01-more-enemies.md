In this section, we will be expanding our game dev knowledge by introducing a new enemy: **Patrol Man**. 

Unlike One Punch Man, Patrol Man brings some additional set of behaviors to our game.



Go ahead and check out the following branch before moving forward: [***Patrol-Man-Setup***](https://github.com/outscal/AGD_StateMachine/tree/Patrol-Man-Setup)



PatrolMan is all about movement. He's designed to patrol an area, moving from one point to another. However, things get interesting when the player enters his range. At that point, PatrolMan switches into chase mode, pursuing the player and opening fire until the player exits his range.




<iframe src="https://www.loom.com/embed/ecd1bbd3f71145b587abc6640d5684cc" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





To achieve this, we'll be creating four distinct states for PatrolMan:

1. **Idle**: The default state when PatrolMan is at rest.
2. **Patrolling**: PatrolMan's routine movement state.
3. **Chasing**: Activated when the player enters his range, initiating pursuit.
4. **Shooting**: PatrolMan fires at the player during the chase.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_20_2023__11_40_09.png)
