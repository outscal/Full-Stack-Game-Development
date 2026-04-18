**LINKED LIST!!**



Let's understand it, 

but hold on a moment—I'm feeling hungry, and I bet you are too! If not, just wait; 

I'll make you hungry!🍽️😋



Imagine you're at a buffet, you take a plate and start adding items one by one, linking them together like a food train.

![Image](//outscal.github.io/Full-Stack-Game-Development/images/818d83a3a42512b4.gif)



- You grab some salad (healthy choice, right?) and put it on plate. 🥗
- - Salad 🥗
- Next up, a slice of pizza! You put that just after salad. (Who said to eat healthy all day?)🍕
- - Salad ➡️ Pizza 🥗🍕
- Ah, the brownie and put it after pizza. 🍫
- - Salad ➡️ Pizza ➡️ Brownie 🥗🍕🍫
- Feeling the cravings?? have some ice cream after the brownie. 🍨
- - Salad ➡️ Pizza ➡️ Brownie ➡️ Ice Cream 🥗🍕🍫🍨
- Lastly, you go for sushi and decided to put it after Pizza cause who wants to jump from sweet to spicy too quickly? 🍣
- - Salad ➡️ Pizza ➡️ Sushi ➡️ Brownie ➡️ Ice Cream 🥗🍕🍣🍫🍨
- But then, you decide to ditch the healthy food for the day. You remove the salad from your plate, shifting the sequence.
- - Pizza ➡️ Sushi ➡️ Brownie ➡️ Ice Cream 🍕🍣🍫🍨



Just like your buffet plate, where you add or remove items **dynamically**, adjusting your food as needed, Linked Lists are similar to your food plate. Each dish on your plate represents a **node**, linking to another node and creating a linear food chain.



Let's understand it with some technical definitions of linked list:

## What is a Linked List?


---



> A** Linked List **is a fundamental data structure used to store a collection of elements. Unlike arrays, which store elements in **contiguous memory **locations, a Linked List stores elements in nodes that are linked together using pointers. Linked List stores in **non-contiguous manner.**



![Image](//outscal.github.io/Full-Stack-Game-Development/images/ffe4b7841ffcd0b3.png)

***Linked List as a chain of elements, each element holding hands with its neighbor***





Difference between **contiguous** and non-**contiguous memory**- Contiguous memory allocation means storing data elements in a single, continuous block of memory. This allows for fast, direct access via indexing but is inflexible and hard to resize.
- Non-contiguous memory allocation scatters data elements across different memory locations, linking them with pointers. This method is flexible and dynamic (i.e. easy to expand or shrink) but involves slower access times due to pointer traversal and additional memory for storing pointers.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/072309865f6c6304.png)





## Node in a Linked List

![Image](//outscal.github.io/Full-Stack-Game-Development/images/d87ba8bea7e15cfd.png)



> A **node** in a Linked List is a fundamental building block. It consists of two parts: data and a pointer. The data part holds the value or information being stored, while the pointer part points to the **next** node in the sequence.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/ea26d4af266e8a39.png)



In the above picture, each node has two parts, one stores the data and another is connected to a different node.

The last node is not connected to any other node and thus, its connection to the next node is **null**.



> A **null** pointer is a special reserved value which is defined in a **stddef** header file. Here, Null means that the pointer is referring to the 0th memory location. A Null Pointer is a pointer that does not point to any memory location.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/58ae0ac1c6559ba7.png)



So, to create a Linked List, you first make a cool node that holds something valuable (data) and a hint (pointer) about where the next exciting node is waiting.



Let's understand it with an example;

Imagine a series of game quests that unlock sequentially. Each quest is like a node in a Linked List, and completing one quest unlocks the next one.

`Quest 1 ➡️ Quest 2 ➡️ Quest 3 ➡️ Quest 4`



In this representation, completing Quest 1 unlocks Quest 2, completing Quest 2 unlocks Quest 3, and so on. This sequential unlocking mirrors the concept of nodes pointing to each other in a Linked List.





## Music on THE Linked List


---



![Image](//outscal.github.io/Full-Stack-Game-Development/images/df2cf3469359018f.gif)

🎵***MUSIC PLAYLIST***

Open your favourite music app on your phone!

Open your favourite playlist!

Play your favourite music!

And read carefully what I am saying!



**In your playlist...**

You can easily add songs to it

Remove what you are bored off

Some apps even allow you to reorder the sequence!

**While playing...**

The next song plays automatically

You can even move from the next song to the previous song whenever you want

You can add new songs to the queue whenever you want

You can even change the order of the songs!

There is a limit to the number of songs you can add to the queue!

And the apps are super optimised!



This is exactly where Linked List shines!

Quick insertion, deletion and easy traversal!  



## But Arrays?


---

But you can do all these things in Arrays, too! right?

Well, you'll see in the next section.

**See you there!👋🏼 **
