Here we will discuss the operations in a circular linked list.



Operations in a Circular Linked List (CLL) depend on the type of node you choose:

- **SingleNode:** Operations are similar to those in a Singly Linked List (SLL), but with a unique twist: ensuring the last node points back to the head node, creating a continuous loop of data.

![Image](/Full-Stack-Game-Development/images/c9e8dd21e8ea7218.png)

***Singly Circular Linked List***



- **DoubleNode:** Operations resemble those in a Doubly Linked List (DLL). Here, the last node's `next` pointer connects back to the head node, and the head node's `previous` pointer links to the last node. The one you saw in UNO.

![Image](/Full-Stack-Game-Development/images/c5664ad617ef6d3f.png)

***Doubly Circular Linked List***



## Creating and Initializing a CLL


---

Creating a node of Circular Linked List (CLL) is similar to creating a Singly Linked List (SLL) or a Doubly Linked List (DLL). 

However, the initialization process is different from them.

To convert a normal list into a CLL:

1. Construct the nodes as you would for any linked list.
2. Connect each node to the next, just like in an SLL or DLL.
3. Point the last node’s **next** (or **previous** and **next** for DLL) to the **head** node, forming a circular structure.

Now, your list is converted to an endless loop. 



## Individual Operations of CLL


---

It's great that you still want to know about the individual operations. 

So here we go:



1. **Insertion: **Adding a node to a CLL involves placing the new node in the desired position and updating pointers to maintain the circular structure.

![Image](/Full-Stack-Game-Development/images/77aa00792c97ba56.gif)

***Insertion at Beginning***


1. **Deletion:** Removing a node requires updating the pointers to maintain the circular flow.



![gif](/Full-Stack-Game-Development/images/5105b40c9f6c9238.gif)

***Deletion from End***

1. **Traversal:** Start from any node (starting point) and follow the pointers until you return back to the starting point.



![Image](/Full-Stack-Game-Development/images/53149b8e8873802b.gif)

***Traversal***



Don't you want to try it out on your Snake Game? 🐍

Well, hold your snakes.

Listen first. Using a Circular Linked List for your snake game isn't practical. 😣

 

Remember the logic for updating the snake's position and direction? 

It requires reaching the end of the list to update each node. 

But in a CLL, there is no true "**end**". The head node loops back to itself.



If you treat the head node as the end, it defeats the purpose of a circular structure. 

Instead, a Singly or Doubly Linked List is more appropriate for your game.



Now you have the idea of operations in CLL.

In the next section, you'll explore the time complexities in CLL operations.

**See you there.👋🏼**
