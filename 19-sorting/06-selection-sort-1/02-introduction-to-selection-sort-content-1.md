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

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_27_2024__10_40_31.png)



- **Mark the first element**: Begin by assuming the first element is the smallest.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_27_2024__10_39_20.png)



- **Find the smallest number**: Go through the entire dataset to find the actual smallest number. When you find it, swap it with the first element of the unsorted subset, making it the first element of the sorted subset.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_27_2024__10_58_26.gif)



- **Repeat the process**: Now, ignore the first element (since it's sorted) and repeat the steps for the rest of the dataset.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_25_2024__18_25_05.gif)



- **Continue until sorted**: Keep doing this until the whole list is sorted. Eventually, you will have a sorted dataset! 

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_25_2024__18_26_25.gif)

***Final Sorted Dataset***



Now, look at the whole process together:

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_25_2024__18_36_43.gif)

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
