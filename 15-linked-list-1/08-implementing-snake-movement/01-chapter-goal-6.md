![Snake Moving](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__09_11_25.gif)

***The Snake is moving around***



In this chapter, your snake will start moving all over the screen!



## How will the Snake move?


---

You have a `SnakeController` that controls the entire snake. So, even the movement will be controlled by `SnakeController` 



Here is the pipeline for that movement:

![Snake Movement Flow Chart](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_20_2024__07_24_45.png)

**Snake Movement Flow**



`SnakeController` will update the `SinglyLinkedList` with the direction and then the `SinglyLinkedList` will update each `Node`'s `BodyPart` with the direction and then each `BodyPart` will calculate the next position based on its current position and direction.



This mission is crucial for your Snake's movement, so get ready! Platypus Perry!

![Platypus Perry Transformation](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_20_2024__07_28_15.gif)
