Most of the algorithms you've covered so far have been quite slow and seem inefficient.

This is why they are the basic sorting algorithms and are often considered the naive approach or the simplest way to sort a collection.

Selection Sort is no different. 🤭



Let's look into why the sorting algorithm called ***selection sort***!



## UNDERSTANDING Selection SORT


---

A ***selection sort*** algorithm sorts a list of items by going through the data, picking the smallest item from the unsorted part, and moving it at the end of the sorted part. It keeps doing this until everything is sorted.



In other words, it iterates through the unsorted subset, *selecting* the smallest element from it and *swapping* it with the first element of the unsorted subset. This makes it a part of the sorted subset and reduces the size of the unsorted subset by 1.


Let's see how selection sort actually works in detail.



- **Start with an unsorted dataset**: Imagine a dataset of numbers that aren't in order yet.

![ ](/Full-Stack-Game-Development/images/7a14b64ca69b7741.png)



- **Mark the first element**: Begin by assuming the first element is the smallest.

![ ](/Full-Stack-Game-Development/images/29da40bd5081cb6d.png)



- **Find the smallest number**: Go through the entire dataset to find the actual smallest number. When you find it, swap it with the first element of the unsorted subset, making it the first element of the sorted subset.

![ ](/Full-Stack-Game-Development/images/f1f5100927b6b664.gif)



- **Repeat the process**: Now, ignore the first element (since it's sorted) and repeat the steps for the rest of the dataset.

![ ](/Full-Stack-Game-Development/images/5cf7e355b2058d89.gif)



- **Continue until sorted**: Keep doing this until the whole list is sorted. Eventually, you will have a sorted dataset! 

![ ](/Full-Stack-Game-Development/images/0e054e9aa5e92315.gif)

***Final Sorted Dataset***



Now, look at the whole process together:

![ ](/Full-Stack-Game-Development/images/85f9b0b2f171e1eb.gif)

***Selection Sort ***

Very straightforward, right?

Time to summarize these steps for implementation.



## STEPS TO PERFORM Selection SORT


---

1. Assume the first element in your array is the smallest. Set it as "`**min_index**`"
2. Look through the entire array to find the smallest number. Compare each number with the `**min_index**`. If you find a smaller number, update the `**min_index**`.
3. Once you find the actual smallest number, swap it (`**min_index**`) with the first element of the array.
4. Now, ignore the first element (since it's sorted) and repeat the process for the next position in the array.
5. Continue this process for each position in the array, until you've sorted the entire array.



Now, it's time for you to try Selection Sort! 

Take a look at how it should appear:


<iframe src="https://www.loom.com/embed/72bbb180ec274311824a5509081a71aa" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Selection Sort***


Try implementing the sort yourself in the assignment before you move on to the next lesson.

**See you there!👋🏼**
