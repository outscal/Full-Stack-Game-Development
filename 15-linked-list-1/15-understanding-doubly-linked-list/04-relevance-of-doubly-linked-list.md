You might be thinking...

"*My snake game is working fine with a Singly Linked List (SLL), so why would I need a Doubly Linked List (DLL)?*"



It’s a valid question! 

While the Doubly Linked List might increase memory usage, it brings several advantages that make the Singly Linked List feel a bit short in certain scenarios.



To understand why Doubly Linked Lists can be superior, let’s look at some real-world applications where Singly Linked Lists might fall short.



## Real-World Applications


---



## **Browsing History: **

![Image](//outscal.github.io/Full-Stack-Game-Development/images/3fea3e2dcdb241eb.gif)

***browser’s tab history***



Ever wondered how your browser’s tab history works? 

It's essentially a linked list, with each visited page being a **node** in a doubly linked list. This allows you to navigate back and forth smoothly between recently visited pages.

If we were using a Singly Linked List, moving back to the recently visited page was impossible!

With a Doubly Linked List, when you click the **back** button, the browser simply follows the pointer to the previous page. When you click **forward**, it follows the pointer to the next page. 

No need to start at the beginning and traverse through each page—saving both time and computational resources.



## **Document Editing: UNDO FEATURE**

![Image](//outscal.github.io/Full-Stack-Game-Development/images/5cf97c8c5a6deea3.gif)

*Document Editing*



Think about using Microsoft Word. 

Every edit you make is stored as a **node** in a Doubly Linked List. This structure allows you to undo or redo actions smoothly by traversing backward or forwards through the list. 

If it were a Singly Linked List, undoing an action would require traversing all the way from the start, making the process inefficient.

Each action (like typing a letter, deleting a word, formatting text) is a **node** in a Doubly Linked List. 

When you hit '**undo**', the program moves to the previous node; when you hit '**redo**', it moves to the next node. 



## GAME-World examples


---



- **Weapon Wheel**: In games, a player can press the right/left arrow keys or buttons to switch between a list of multiple equipped weapons in a game.
- **Spectator Modes**: For games with spectator modes like Chess, where viewers can rewind or fast-forward through live or recorded gameplay, Doubly Linked Lists offer an effective way to manage gameplay frames for playback.



## Technical Advantages of Doubly Linked Lists


---



- Doubly Linked Lists (DLLs) allow easy navigation in both directions, making them ideal for tasks like navigating browser tabs or undoing and redoing edits in a document.
- Deleting a node in a DLL is straightforward since you have direct access to both the previous and next nodes.
- DLLs enhance performance for applications requiring frequent forward and backward traversals, such as video players, ensuring smooth navigation and a better user experience.



So, when should you call in the big brother? 

When you need an **efficient bidirectional traversal and easy node removal** that the Doubly Linked List offers.



**See you in the next chapter! 👋🏼**
