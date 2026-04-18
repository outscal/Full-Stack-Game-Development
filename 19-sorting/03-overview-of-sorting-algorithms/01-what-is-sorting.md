> **Try the visualizer for all sorting algorithms in the **`**Radix-Sort-Solution**`** branch**



I hope you have tried and enjoyed the visualizer!

You will create your own visualizer, but first, you need to learn what sorting is.



In this chapter, you will gain a deep understanding of sorting, its applications, and its importance.



## what is sorting/Sorting Algorithm?


---

**Sorting** is the process of rearranging elements/data based on specific criteria, such as arranging numbers from smallest to largest or arranging names alphabetically.



**Sorting Algorithms** are the *different ways *in which you can sort something. These algorithms follow specific rules and methods to reorder elements.



There are various types of sorting algorithms that are designed for different data structures, scenarios, and conditions. 

Each algorithm has its unique approach and performance characteristics, making it essential to choose the right algorithm for the sorting task at hand. Some common sorting algorithms:

1. Bubble Sort
2. Selection Sort
3. Insertion Sort
4. Merge Sort
5. Quick Sort, and many others. 



## Why is sorting useful, and when is it needed?


---

Imagine you walk into a library with thousands of books scattered randomly on shelves.

It would be very difficult to find a particular book that you came to read.



Now, if the library sorts books by categories like fiction, nonfiction, fantasy, mystery, etc., and each category is arranged alphabetically, finding a book becomes much easier.

You head to a section of your choice and then search the book by its name!



As you might have noticed in the above example, sorting the books in the library has the following benefits:

- **Easier Data Interpretation**: Sorting makes the data more readable, just like organizing books by genre or author, making it easier to browse and locate specific books.
- **Efficient Searching:** When books are organized on shelves, finding the one you need becomes quick, as you just need to locate their positions instead of searching through a jumbled collection.

For instance, let's say you have to **find a number** within a list.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/b5b3089ccb31b89e.png)



If the example above looks familiar to you, that’s because it’s our good old friend, ***binary search***!



## Classifications of sorting algorithms


---

There are so many sorting algorithms, and to distinguish between them, we classify them based on key factors that help programmers choose the best one for their needs.



Each algorithm has its own pros and cons. We'll use these classifications to understand their effectiveness. 



1. **Time complexity:**
  The easiest way to classify an algorithm is by its** *****time complexity*** or by the relative time it takes to run the algorithm, given a different input size.
2. **Space complexity/memory usage:** 
  The amount of extra space or memory a sorting algorithm needs to sort its input varies. Different algorithms require different amounts of space, depending on their complexity.
  
  There are two types of classifications for the space complexity of an algorithm: *in-place* or *out-of-place*.
  
  **In-place vs. Out-of-place Sorting:**
3. - **In-place Sorting:** 
    In-place sorting means sorting your data right where it is, without using extra space for another copy of the data. This type of sorting works directly on the original data, changing it as it goes. 
  - - **Pros:** It uses very little extra memory, just a small, constant amount: **O(1)**. 
    - **Cons:** The original data gets altered, so you can't keep the original version.
  - **Out-of-place Sorting: **
    Out-of-place sorting means creating a new, sorted copy of your data while leaving the original data unchanged. 
  - - **Pros:** It preserves the original data, making it safer.
    - **Cons:** It requires more memory since you have both the original and the new sorted data, doubling the memory usage.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/1823fe91cb5b06db.png)

*In-place vs. Out-of-place Sort*



1. **Stable vs. Unstable Sorting:**
  
  **Stable Sorting:** Stable sorting means that if two elements are equal, their relative order remains the same in the sorted data as it was in the original data.
  
  **Unstable Sorting:** Unstable sorting means that the order of equal elements may change in the sorted data.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/a71eacb801b95ea0.png)

*Stable vs. Unstable Sorting*



Okay, we’ve exhausted our list of classifications.

Hopefully, by now, you can see that sorting algorithms are a *big deal*!



In the upcoming chapters, you will learn about different sorting algorithms and see the differences between them.

Before that, let's see some applications of sorting in gaming.



**See you in the next lesson!👋🏼**
