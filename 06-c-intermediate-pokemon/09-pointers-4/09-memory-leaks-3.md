In the last lesson, we talked about memory allocation and deallocation using `new` and `delete` keywords. 

Now, let's think about how much memory can we actually allocate ?



Memory allocation is limited by the amount of available system memory. 

If you keep allocating memory, your program can eventually run out of available space.



Let’s see what happens if we try to allocate memory in an infinite loop. 



Imagine this loop:

```cpp
while (true) {
    Player* player = new Player();
}
```



**Take a moment to think **

*will this loop keep running forever?*



The answer is **NO**. Eventually, it will stop.



The loop stops because the system runs out of memory. 

The memory allocation fails, and the program can’t continue. 

This situation is often called a **memory leak.**



# What is a Memory Leak?


---



Imagine adding books to a library but never returning them.
The space keeps getting filled up, but the books are never given back.
That’s what a memory leak does to your system.



![img](/Full-Stack-Game-Development/images/d82728d2cd677587.png)



**A memory leak happens when your program keeps allocating memory but never releases it.**



Memory leaks can have serious consequences.

If your program uses too much memory.

It can cause the entire system to shut down.



Programs with memory leaks might crash because they run out of memory.

Memory that could be used for other tasks is wasted, slowing down your system.





For programs that run for a long time, like servers or applications.

That stay open all day, memory leaks can be especially harmful. 



Over time, these leaks can use up all available memory.

Causing the program to crash and potentially losing data.



# Ways to Avoid Memory Leaks


---



**Always Pair **`**new **`**with **`**delete**`

Whenever you allocate memory with `new`, make sure to free it with `delete`.



**Monitor Memory Usage**

Keep an eye on how much memory your program is using over time. 

This can help you spot leaks before they become a problem.



By following these practices, you can keep your programs running smoothly.

And avoid the pitfalls of memory leaks. 



In the next lesson, You will use this  pointer in your code and make changes Accordingly.
