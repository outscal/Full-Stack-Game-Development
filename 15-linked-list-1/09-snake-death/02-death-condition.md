![OG Snake Death](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_20_2024__08_51_32.gif)



You see, the snake can die for 2 reasons:

1. Snake Collides with itself... **BAAM BAAM BAAM! Death!**
2. Snake Collides with an Obstacle... **BOOM BOOM BOOM! Death!**



## How will you detect collision in this game?


---

In games, collisions are detected by checking if 2 objects are overlapping, i.e. if they share a common coordinate in the game-world.

In this game, every Body Part occupies 1 position in the grid, so you can just check if any 2 body parts share a common point on grid and that'll be a condition for collision!



# Optimised Collision Detection


---

## Collision Detection in Games


---

![Polygons](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_20_2024__09_07_43.gif)

**Polygons in a 3D Model**



In 3D games, an object is made up of many "***Polygons***" or points. 

If 2 objects are made up of 1,000 and 5,000 polygons each, then to check for collisions, the program needs to check for

`1,000x5,000 = 5,000,000` overlapping polygons.



Yes! That is the number!

And this is only for 2 objects...

Imagine having Hundreds or Thousands of such objects!



To reduce this computation load, there are collision boxes.

![Collision Box in a 3D Model](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_20_2024__09_11_46.png)

**Collision Box on a 3D model**



Collision Boxes are simpler shapes with a very small number of polygons that are put on top of the 3D Models, these simpler shapes roughly cover the entire 3D object and then these collision boxes are used for collision detection.



## You did it better!


---

Now, in your case, you will only use 1 single point per body part, which is much more optimised than a generic 3D game or even a normal 2D game.

All of this is thanks to the **grid-system** you implemented



Good Job!💪🏼😎
