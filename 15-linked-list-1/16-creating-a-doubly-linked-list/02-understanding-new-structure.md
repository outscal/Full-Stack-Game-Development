![New Architecture](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_04_2024__10_11_01.png)

***New Architecture***



This new architecture needs:

1. Base Node
2. Single Node
3. Double Node
4. Base Linked List
5. Single Linked List
6. Double Linked List





![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_23_2024__09_15_40.png)

**Old Structure ☝**



Alright, say goodbye to the old structure (bye-bye 👋) and build a better one!

**New Structure 👇**

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_23_2024__09_16_18.png)



To understand what the new structure offers, let’s break down the major changes:

1. Each list will have its own node structure class:
2. - You will create two node structure classes: `SingleNode` and `DoubleNode` inheriting from `Node` class.
  - `DoubleNode` will have pointers to both the **next** and **previous** nodes, allowing for bidirectional traversal.
3. Each list will have its own classes to handle operations:
4. - You’ll implement new linked list classes: `SingleLinkedList` and `DoubleLinkedList`.
  - These classes will inherit from a base `LinkedList` class, providing a common interface and shared functionality.
5. Introducing Linked List Library:
6. - All these new classes will be organized under `LinkedListLib` namespace for better code management.



## architecture in detail


---



You might wonder, "What's the point of all this?". Good question!! 

Let's play a quiz, and you will ask me questions this time.

Ready to have your mind blown? 



***What is base Node class?***

The base `Node` class will allow you to define common properties that can be extended by `SingleNode` and `DoubleNode`.

**   **

***What is base Linked List class? ***

The base `LinkedList` class will be an interface for different types of linked lists. 

By using a base class, you can create various linked list (like singly, doubly, and even circular linked lists (**bonus content 📈**) classes with shared functionality. 



***Why create a complete Linked List library****?*

The `LinkedListLib` namespace will have all your linked list-related classes, providing an organized structure for your code. 



Using this technique, you can add a new type of linked list any day or time. 

Now that you understand the new architecture, it’s time to implement it.  🐍💻



**See you in the next section!👋🏼**
