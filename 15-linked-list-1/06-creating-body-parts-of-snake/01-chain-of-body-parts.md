![Snake into Pieces](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__10_53_23.png)

**Snake into Pieces**



This snake is nothing but a chain for its body parts.

The head moves according to user input and rest every node follows the node ahead of it.



It is like walking in a March Past in school, you only need to follow the person ahead of you.



![Marching](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__11_09_29.png)

***1...2...1...***



This means each body part needs to have information about itself and a reference to the next body part.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__11_39_36.png)



This is exactly like the *Nodes* of a *Linked List🔗* 



Now you see why Linked Lists are the best Data Structure to create a snake?

If you think you are so smart, here is a question.

**What would be the issue with using Vectors for the snake?** 

Think about it, take your time, I'll wait...

 

Want to know the answer? Come have a quick look 👁️👁️ **Why Linked Lists are better than vectors for creating a Snake🐍?** 

**SPACE OPTIMISATION:** Vectors are dynamic arrays that keep increasing in size when they reach full capacity. So when a vector reaches its capacity, it moves to a new array that is 2x in size. Now, this is a waste of memory. While in Linked List, only the space for 1 new node is allocated. This is much more optimised than Arrays.



Alright!

So the snake is a chain of Body Parts, fine.

This means you'll have to create a file for `BodyPart`, right?

Right!



What else?



The snake is not just a connection of Body Parts, it is a Linked List also!

And what is a Linked List made up of?

...Nodes!



## What is a Node?


---

A node is nothing but a collection of data and reference to the next node.

In your case, that 'Data' will be a Body Part



![Snake Node](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__11_43_53.png)

**Snake's Node**

> **TODO**
> ✅ Create an empty `BodyPart` class inside `Player` folder and create `namespace Player` inside it



In the next chapter we will discuss `BodyPart` in detail
**See you there !👋🏼**
