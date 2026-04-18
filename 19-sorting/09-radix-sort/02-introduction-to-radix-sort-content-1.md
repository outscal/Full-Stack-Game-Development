Imagine sorting a list of students. There are two types of sorting: Comparison-Based Sorting and Non-Comparison-Based Sorting.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/c0f9284ac87bf569.png)

***List of Student***



In comparison-based sorting, you directly compare elements to determine their order. For example, 

- You might use Bubble Sort, where you repeatedly compare and swap adjacent student IDs until the whole list is sorted. 
- Alternatively, you could use Quick Sort, where you select a pivot ID and partition the list around it, sorting smaller and larger IDs on each side.



Now, imagine there's another way to sort the deck without comparing the cards directly. 

This is where non-comparison-based algorithms come in.



## Non-Comparison-Based Algorithms


---

Non-comparison-based sorting algorithms, such as Radix Sort or Counting Sort, sort the elements based on their individual digits or characters without directly comparing them.

These algorithms perform better on certain data types because they sort data using its **properties**, such as digits or categories. 



Let's sort the list of students, but this time not by Student ID but by their names using a non-comparison-based sorting algorithm.



If this sounds difficult, don’t worry! 

You’ve likely used a similar method in everyday life.



Think about alphabetizing (arrange in alphabetical order) words. We’ve all done that, right?

How would you start putting these names in order?



You’d begin by grouping the names by their first letters:

- `A`: `Arun`, `Alex`
- `D`: `David`, `Diana`, `Daisy`
- `H`: `Hannah`



Next, alphabetize within each group. For the `A` group, you compare the second letters: `Alex` comes before `Arun` because `l` comes before `r`.



Now, alphabetize the `D` group by comparing their second letters and, if needed, third letters:

- `David` comes before `Diana` because '`a`' comes before '`i`'.
- `Daisy` comes before `David` because '`i`' comes before '`v`'.



The `H` group only has one name, so it's already sorted!



So, you have:

- `A`: `Alex`, `Arun`
- `D`: `Daisy`, `David`, `Diana`
- `H`: `Hannah`



Finally, you combine the sorted groups back together in order. 

Starting with the `A` group, then the `D` group, and finally, the `H` group, you end up with a sorted list of names: `Alex`, `Arun`, `Daisy`, `David`, `Diana`, `Hannah`.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/323cf6e42058178a.png)

***Sorted List of Students***



This process of sorting names by their letters, one letter at a time, is similar to how radix sort works.



## Introduction to Radix Sort


---

**Radix Sort** is a non-comparison-based algorithm that sorts numbers based on their individual digits.

Before you understand the inner workings of radix sort and how it works, let’s first understand what the word *radix* actually means.



A radix is another term for "base." It represents the number of digits used in a number system.

- The binary number system has a radix of 2.
- The hexadecimal number system has a radix of 16.



> **💡Protip: **The word **radix** comes from Latin work *radix* which mean "**root**"



Now, how does the term *radix* tie back into radix sort? 

Well, if you’re guessing that radix sort has something to do with the base or digits of a number, you’re right.



The ***radix sorting algorithm*** is an integer sorting algorithm that groups numbers by their individual digits (or by their radix). 

It uses each radix/digit as a key and implements counting sort or bucket sort under the hood to do the sorting work.



## Understanding Radix Sort


---

To understand how radix sort functions on integers, you need to first decide which form of radix sort to examine.

That’s right — there are *two* different basic formats of the radix sort algorithm.



In the student's example, you sorted names by starting with their first letter and grouping words with the same first letter. 

If needed, you look at the second letter for sorting.



This form of radix sort is known as the ***most significant digit (MSD)*** radix sort. 

It sorts by processing from the greatest digit to the least significant one. 

In other words, it starts with the largest number and then continues sorting until it reaches the smallest digit.

It uses counting sort or bucket sort and often involves recursion.



The other form of radix sort is called the ***least significant digit (LSD)*** radix sort. 

It begins by processing the smallest digit first and progresses towards the more significant digits.

While it also uses counting or bucket sort internally like MSD, LSD is typically solved iteratively rather than recursively.



Since you’ve already seen how MSD radix sort works with our example.

Let’s look at how LSD radix sort works with an array of integers: `**[10, 52, 5, 209, 19, 44]**`



To apply LSD radix sort, rewrite these numbers so that they all have the same number of digits.

This isn’t part of radix sort, but rather just a way to make it easier to see what happens in each algorithm step.



Since the largest number (`209`) has three digits, add zeros to make all elements in the array have three digits.

Rewritten, your array now looks like this: `[010, 052, 005, 209, 019, 044]`



Now, you can start sorting based on the LSD, which means you'll begin by looking at each number's rightmost digit.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/2b37b5de3f758409.png)

***least significant digit: the ones***



In the example shown above, the least significant digit, the unit place in each integer element, is highlighted in blue.

You’ll use counting sort to sort all of these integers.



But what exactly is counting sort, and how does it work?

That will be discussed in the next lesson.



**See you there!👋🏼**
