Here we go again!!

We're gathered here to welcome our new guest: **the Circular Linked List, or CLL.**



![gif](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_28_2024__10_59_33.gif)



Yes, we're not done with just two types of linked lists. There's one more, and it's even more exciting than a regular linked list!

Have you ever wondered if there's a linked list that never ends?



Imagine your Spotify playlist – a series of songs you love. 

You must have noticed the **repeat** feature on Spotify that keeps your favourite playlist playing on a loop. 



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_28_2024__11_31_05.png)



How would you achieve that with a regular linked list? You'd need something special, right? 

Well, guess what? It exists, and it's called the **Circular Linked List (CLL)**! 🔄



## In-depth on Spotify's Repeat Feature


---



In a regular linked list, traversal ends when you reach your playlist's last node (song). But with a Circular Linked List, you can create a playlist that loops endlessly. 

Here’s how it works:

1. **Starting Point**: When you start playing your playlist, you begin with the first song.
2. **Traversal**: You move to the next song, one by one, until you reach the last song.
3. **Looping**: Instead of stopping at the last song, the pointer from the last song points back to the first song.
4. **Continuous Play**: This creates a continuous loop, allowing your playlist to play indefinitely. 

With this structure, you never run out of songs to play, creating endless music.





## Why Circular Linked Lists?


---



Circular Linked Lists are perfect for scenarios requiring continuous cycling through data. 

Here are a few real-life examples where CLLs shine:

- **Music Playlists:** As discussed, your favourite playlists can loop endlessly, providing non-stop music.
- **Round-Robin Scheduling**: In operating systems, processes are given an equal share of CPU time in a cyclic order.
- **Multiplayer Games**: Turn-based games circularly manage players to ensure a smooth game flow like UNO, Ludo, etc.
- **Traffic Lights**: Traffic signals at intersections change in a cyclic manner, ensuring orderly traffic movement.





## What are Circular Linked Lists?


---

A Circular Linked List is a type of linked list in which the **last node points back to the first node**, forming a circle, Just like an Oroborus.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_28_2024__11_47_10.png)

***The Oroborus is an ancient symbol of a snake eating its own tail.***



Unlike singly and doubly linked lists, a CLL allows for seamless traversal from any node without encountering a null reference.

Circular linked lists are classified into two types: singly circular linked lists and doubly circular linked lists, depending on the type of node used.



## Comparison with SLLs and DLLs


---



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_28_2024__12_08_26.png)



**Representation Difference:**



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_28_2024__12_57_30.png)

***SLL vs DLL vs CLL***



> **🤯 Interesting Thought:** Imagine creating a linked list linked to different nodes, forming a pattern like a ***spider web*** or a ***matrix***. 🕸️ What if your data structure could handle complex relationships like this? 
> **Hint:** There's a data structure called ***graphs*** that behaves like this, and that's for the future!



Ready to explore more?

**See you in the next section.👋🏼**
