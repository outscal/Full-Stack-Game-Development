![Snake Moving](//outscal.github.io/Full-Stack-Game-Development/images/835aed2b45e6ea02.gif)

***The Snake is moving around***



In this chapter, your snake will start moving all over the screen!



## How will the Snake move?


---

You have a `SnakeController` that controls the entire snake. So, even the movement will be controlled by `SnakeController` 



Here is the pipeline for that movement:

![Snake Movement Flow Chart](//outscal.github.io/Full-Stack-Game-Development/images/4cce6cad7e1ecfd4.png)

**Snake Movement Flow**



`SnakeController` will update the `SinglyLinkedList` with the direction and then the `SinglyLinkedList` will update each `Node`'s `BodyPart` with the direction and then each `BodyPart` will calculate the next position based on its current position and direction.



This mission is crucial for your Snake's movement, so get ready! Platypus Perry!

![Platypus Perry Transformation](//outscal.github.io/Full-Stack-Game-Development/images/34daf68c311f738f.gif)
