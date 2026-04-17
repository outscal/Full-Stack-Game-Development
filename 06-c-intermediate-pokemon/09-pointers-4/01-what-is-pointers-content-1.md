> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your current branch called → ***Feature_8_Pointers***

> Let’s start working on the new feature now!



Get ready—we’re about to tackle one of the trickiest topics in C++: **pointers**.



If you ask anyone learning C++, most will say, “I hate pointers!” 

And yeah, I get it. Pointers can be confusing at first. 

They feel like that puzzle you can’t solve... until suddenly you do.

And then everything clicks, and you feel like a coding wizard.



Here’s the thing—if you know how to use pointers, you can master C++. 

It is like having a superpower. But yes, they can be scary. **Why?** 



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_06_2024__12_03_55.png)





Because pointers let you work directly with your computer’s memory. 

If you don’t use them right, things can go wrong. 



If you don't manage things properly, it’s easy to lose control

Just like leaving the front door open during a party and letting things get out of hand.



But don’t worry, you’re in good hands. 

In this chapter, you’ll learn all about pointers, and I’ll make sure it’s simple and clear. 

By the end, you’ll understand what pointers are and why they’re so cool.



So, what *are* these mysterious pointers, and why do they matter so much? 

Let’s find out!



# What is Pointers ?


---



A pointer is something that points to something else! 

Yes, it's as simple as that.

![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_06_2024__12_16_25.png)



But, what exactly does it point to? 

Let’s break it down.



When you create a variable in your program.

let's say `int a = 10;.`

what happens behind the scenes is that the computer reserves a little spot in its memory to store the value 10. 

Every variable has its own special place in memory.



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_17_2024__10_23_05.png)



And the computer knows where to find it by using something called an **address**. 

Think of it like a house having its own address, so the computer can find out where the value is stored.



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_17_2024__10_24_33.png)





Now, this is where** pointers come in**. 

A pointer doesn't hold the actual value of the variable (like 10).



But instead, it holds the **address** of where that value is stored. 

So, if you imagine your variable as a house, the pointer is like a signpost pointing to the exact location of that house!



**For example :**

       if `a` is stored in memory at address `0x1234` (this is just an example of how addresses look. Cover this in the next lesson).

      A pointer will hold that address, like this:

```cpp
int* ptr = &a; // ptr now points to the address of 'a'
```



Now, You might be confused from this line.

Let's understand this bit by bit.





Dereference operator ( * )

The `*` here tells the computer, "Hey, this is not a regular variable—this is a pointer that will store the address.



and `int*` - stores the address of integer.



Note : ` ptr` is just name of pointer variable.



address of (&) 

The `&` symbol is used to get the memory address of a variable.

The `&a` means "the address of `a`.


So here, we’re saying, "Take the address where the integer `a` is stored in memory.



It makes `ptr` point to the address of `a`, meaning `ptr` knows where `a` is located in memory.

But it doesn't hold the actual value of `a`. 



If you want to access the value of `a` through `ptr.`

you'd use `*ptr`, which gives you the value stored at the address `ptr` is pointing to.



```cpp
int a = 10;
int * ptr  = &a   // int * --> pointer ,   ptr = name of pointer variable store address of a  ,  &a = give address of a

// now accessing value of a through ptr
cout << *(ptr) << endl;   // it prints value of a  --> 10
```



> 💡**PRO TIP** :  what will happen if you don’t use `*` while printing `ptr` value?



Run the code and Tell me what your output is.

Yes, This is the address of `a` where variable a is stored.



## Why use pointers ?


---



Pointers are one of the key tools that give you real control over how your program uses memory. 

They allow you to manage memory in an efficient way, which is crucial for writing optimized code.



**Examlple : **

Imagine you have a huge list of numbers. 

Instead of copying the whole list each time, you pass the address where it's stored.

Like sharing a drawer number instead of the whole stack of papers.



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_17_2024__10_41_02.png)







Did'nt get it ? Don't worry. We will discuss about this later.



The main thing to remember here is that mastering pointers gives you power. 

If you can manage memory wisely, you’re not just writing code—you’re optimizing it. 

This is why developers who know how to use pointers effectively are considered some of the best at creating fast, efficient programs.



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_06_2024__13_12_10.png)





Above, You encountered with  `0x1234` this.

What is this?

This is address of memory where a variable is stored.

so, You will learn about more in the next lesson!
