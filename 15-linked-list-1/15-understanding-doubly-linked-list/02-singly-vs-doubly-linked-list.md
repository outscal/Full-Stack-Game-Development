**Differences between two Brothers!!**

**Singly Linked List 👹 vs 😈 Doubly Linked List**



Before the differences, let's start this section with a little brainstorming session! **Ready?**

Imagine you're tasked with implementing a doubly linked list for a video player.🎬

How would you tackle this? 🤔



![Music Player Carousel](/Full-Stack-Game-Development/images/137eff5a7147070a.gif)





> **💡Hint: **Think about the music player's functionality. How would you keep track of the current song being played, as well as easily navigate to the previous and next song in the playlist?



Take a moment to brainstorm your approach!!

**Done? **Let's explore this together.



Video Player are also the same!

Implementing a doubly linked list in a video player involves creating a playlist where each node represents a video file. 📽️

Each node would contain data about the video and pointers to the previous and next videos. 

This structure allows bidirectional navigation. When adding or removing videos, you would update the pointers of adjacent nodes to maintain the list structure. 

With this setup, users can easily navigate between videos. Moving back and forth in the playlist becomes seamless!



Now that you've warmed up with a practical example let's quickly jump to the key differences between singly and doubly linked lists.



## Differences Between Singly and Doubly Linked Lists


---

Let's discuss them one feature at a time:

1. **Structure:**

- - **Singly Linked List:** Each node has one pointer (**next**) pointing to the next node in the sequence.



![Image](/Full-Stack-Game-Development/images/aafab718db84b9fd.png)

***Singly Linked List***



- - **Doubly Linked List:** Each node has two pointers, one pointing to the next node (**next**) and one to the previous node (**prev**).



![Image](/Full-Stack-Game-Development/images/d3b65bc31e15996c.png)

***Doubly Linked List***



1. **Memory Usage:**

- - **Singly Linked List:** Uses less memory since each node only contains one pointer.
  - **Doubly Linked List:** Uses more memory due to the additional pointer.



1. **Traversal:**

- - **Singly Linked List:** Only forward traversal is possible.



![Image](/Full-Stack-Game-Development/images/427322879bdd7386.png)



- - **Doubly Linked List:** Both forward and backward traversal are possible, making navigation more flexible.



1. **Insertion/Deletion:**

- - **Singly Linked List:** To delete a node, you must traverse from the head to locate the previous node. Insertions also require access to the previous node if not inserted at the head.
  - **Doubly Linked List:** Insertion and deletion are more straightforward since you can quickly adjust the previous and next pointers without full traversal.



Check out this code snippet showcasing the difference in deleting a **node** between the two:



***Single Linked List Deletion:***

```cpp
void deleteNode(Node* target) {
    Node* temp = head;
    while(temp->next != target) {
        temp = temp->next;  // Finding the previous node
    }
    temp->next = target->next;  // Unlink the target node
}
```



***Doubly Linked List Deletion:***

```cpp
void deleteNode(Node* target) {
    if(target->prev != nullptr)
        target->prev->next = target->next;
    if(target->next != nullptr)
        target->next->prev = target->prev;
}
```



See the difference? 

Singly linked lists require traversing, while doubly linked lists can directly update pointers for efficient removal!



Just like this, there are many operations where time complexity for operations differs between these two types of lists: 

![Image](/Full-Stack-Game-Development/images/9ba686da361ca8c7.png)



Now, let's talk about space. 👀 

While both types of lists store data elements, the memory usage differs due to an **additional pointer **in doubly linked lists. 

In a singly linked list, each node only needs to store a pointer to the next node, resulting in lower memory usage. 

However, our big brother, the doubly linked list, requires each node to store pointers to both the next and previous nodes, doubling the memory usage. 

**Big Brain!!🧠**



Both brothers have strengths and weaknesses, but ultimately, it all comes down to your needs and preferences. 

They are both reliable in the linked list game and ready to tackle whatever challenges come their way. 



In the next section, you will tackle the application of DLL. To understand why it is so cool!

**See you there!👋🏼**
