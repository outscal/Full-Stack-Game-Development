**Why Linked List over Arrays? 🤔**



Array and linked lists have similar functionalities, such as storing elements and allowing access through indexing. 

However, where they differ is their capability to increase or decrease their size **dynamically**.



Let's understand these differences to know why you are re-creating the OG Snake Game for Linked Lists and not for Arrays!



## **Linked Lists: Flexible Structure**


---

It’s great for situations where you need to add or remove elements frequently, as its size can change easily based on the number of nodes.

Imagine building a ***Lego Tower 🏗️****,* and you want to add the yellow block between the green and blue block.

So, for that, just **break the bond** between the blue and green blocks (unlink them as they are not tightly bounded). 

Insert the yellow block above the blue and then connect the green block with the yellow. Tada, simple that was. 

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_30_2024__17_38_14.jpg)

*** Lego Tower***



In terms of a linked list, the **node** represents an individual Lego block, and the **linked list** is the combination of blocks, similar to a tower.

The new block is like the **new node**. 

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_01_2024__10_03_36.jpg)



The connection between these Lego blocks is like a **pointer**: the yellow block **points** to the blue block.

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_01_2024__10_09_03.jpg)



If you add a new red block on top, the blue block must now **point** to the red block to maintain the connection. This process is known as **Insertion**.



**Arrays:  Fixed Structure **

Arrays are great for fast-indexed access, but you must know the exact number of elements.

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_30_2024__17_48_23.jpg)

***Theatre***



Imagine watching a movie in a theatre. The seats are arranged well and obviously tightly bound. Can you add a seat in between them? 

Obviously, it's not so easy. This is where Array fall short.



## dynamic size change


---

Let's see the difference between an Array and a Linked List with one operation.

Imagine you have a filled array of size 4 and a linked list with 4 nodes.



Now, if you want to insert an element/node in the 2nd index of both data structures, here's what happens.



**Array:**



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_01_2024__10_44_52.png)



- The array is already full!
- You'll have to create a new array! 
- You can create a new array with 1 extra size. (5)
- Now you'll copy elements at index 0 to 1 from the old array to the new array
- Then add the new element at index 2 in the new array
- and then copy the rest elements from old array and the new array

uhhhh!
Sounds like too much work?

Well, what if you have to add another new element at index 3?!

Will you create another new array and do everything again?!



Alternatively,

You can just have a huge new array that is double in size at once!

And now insert double the number of elements!





But but but…

You'll still have to shift a lot of elements when you insert an element between the array, and you will be occupying DOUBLE STORAGE! When you don't even know if it'll be useful!



As a developer...
This sounds painful😞 



**Linked List:**

You simply create a new node for the new node **n**. You adjust the pointers of the surrounding nodes to include this new node. No shifting or copying of elements is needed, just updating a couple of pointers.

Simple right?



![gif](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_01_2024__10_27_08.gif)

***Insertion at Middle***



This highlights the advantages of linked lists for dynamic data management scenarios. 

They offer easy insertion and deletion without requiring too much memory.



**See you in the next chapter 👋**
