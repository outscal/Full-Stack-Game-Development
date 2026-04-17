**Ready for Restructuring??**



You've made it this far, so give yourself a pat on the back. 

![Image](https://giphy.com/gifs/Friends-friends-season-6-tv-XGnH2RGHoCqumsAXpo)



Now, take a moment to relax and clear your mind before jumping into the next challenge.

Take a deep breath, maybe even do a quick meditation. Ready? 🧘‍♂️



![Image](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExdjM0ZWRhdW43NDlxb3o1bXJ4NmU2dnBoNTUwanh3bHU3cTZ5OWhiMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/H7kfFDvD9HSYGRbvid/giphy.gif)

***ohhhhmmmm!***



Alright, now that you’re calm and centred, prepare for some chaos! 

You're about to implement a Doubly Linked List in your snake game. 



Earlier in old architecture, you built a basic structure of a linked list and used a single linked list for the game. 

Now, with the introduction of the Doubly Linked List (DLL), you need a new and better architecture to handle both lists.



## **New** architecture


---



In the old architecture, you had properties and classes for only `SingleLinkedList`.



**Old Architecture** 👇

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_24_2024__10_36_37.png)

***Node for only Single Linked List***



But in new architecture, you will be creating a new `DoubleLinkedList` but then a lot of common properties and functions will be there btw `SingleLinkedList` and `DoubleLinkedList` so its better to use inheritance here. 



For that, you will be creating base classes that will share the common properties and functions of both the linked list and inherit them in `SingleLinkedList` and `DoubleLinkedList`.

Same goes for `SingelNode` and `DoubleNode`.



This means better organization and more reliable code. 



**New Architecture** 👇

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_23_2024__08_40_32.png)

***Nodes divided into 2 Parts***



Why is this change necessary? 

Because a good developer needs to be flexible and ready to adapt to new requirements, this is exactly what you're learning to do. 

Writing scalable code is crucial for creating a great game that stands the test of time. 



The essence of what being an ***Outscaler*** is all about preparing you to be an **exceptional** developer who can handle evolving challenges.



In the next section, you’ll get into the details of the new architecture. 

**See you there!👋🏼**
