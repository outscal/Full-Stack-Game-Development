Before moving to better approaches, first, understand the limitations of the sorts you've covered so far.

In this lesson, you will summarize the knowledge you have learned so far by differentiating between Bubble Sort, Insertion Sort, and Selection Sort.



## Bubble vs Insertion vs Selection Sort


---

All three algorithms have a worst-case time complexity of `**O(n²)**`, making them less suitable for large datasets. 

They all operate with `**O(1)**` auxiliary space, meaning they are **in-place sort** algorithms.



> **Auxiliary space** refers to the extra memory used by an algorithm, excluding the space needed to store the input data. It measures the additional temporary storage required during execution.



Each of these algorithms is easy to implement and understand, making them excellent for educational purposes. 

They all sort the elements by comparing pairs of elements and rearranging them based on those comparisons.



Wait, the points so far look like the similarities, but we are here to discuss the differences. 

So, where do they all differ? 

The actual difference between them lies in the way they sort the elements.



**Bubble Sort**

Bubble Sort repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. 

This process is repeated until the list is sorted while maintaining the relative order of elements with equal keys, which makes it a **stable** sort.



**Insertion Sort**

Insertion Sort builds the final sorted array one item at a time. 

It takes each element and inserts it into its correct position among the already sorted elements.

It also maintains the relative order of elements with equal keys, making it a **stable** sort.



**Selection Sort**

Selection Sort divides the input list into two parts: the sorted part at the beginning and the unsorted part. 

It repeatedly selects the smallest (or largest) element from the unsorted part and swaps it with the leftmost unsorted element, moving the boundary of the sorted part one step to the right.

Because of swapping, the relative order of elements with equal keys changes, making it an **unstable** sort.



**Click here for **Bubble vs Insertion vs Selection** Sort Comparision Chart**

![ ](//outscal.github.io/Full-Stack-Game-Development/images/38defd84c0d2cd37.png)

***Bubble vs Insertion vs Selection Sort***



After discussing these basic sorting algorithms, the need for more advanced sorting methods for larger datasets is clear.

In the upcoming chapters, we will discuss various sorting methods that are suitable for them.

**See you there👋🏼**
