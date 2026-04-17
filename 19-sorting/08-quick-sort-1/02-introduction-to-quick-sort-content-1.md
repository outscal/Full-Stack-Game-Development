This chapter will teach you why Quick Sort got Quick in its name. 🏃💨 

But before that, take a closer look at the inner workings of Quick Sort.



## Understanding Quick Sort


---

This algorithm does something that you’ve seen before in Merge Sort: It divides and conquers.



**Quick Sort** is a sorting algorithm that first picks a ***pivot*** element, often the last element in the array.

It then ***rearranges*** the array so that elements smaller than the pivot come before it, and larger elements come after.

Once this is done, the pivot is in its final sorted position.



Quick Sort then recursively applies this process to the subarrays on either side of the pivot.

This divide-and-conquer method continues until the entire array is sorted, similar to how Merge Sort uses a midpoint to split the array.



If you read the definition again, the algorithm can be divided into three parts:



1. **Selecting the Pivot:** There are various ways to choose the ***pivot***, an arbitrary element. You could choose the middle stick, the one on the left, or the right, or even choose one at random.



> An **arbitrary element** is an element chosen at random or without any specific criteria from a set or collection.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_07_02.png)

***Choose a Pivot***



1. **Partitioning:** In the context of Quick Sort, this step means rearranging the elements around the pivot. It moves smaller elements to the left of the pivot and larger ones to the right. 



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_08_41.png)

***Partitioning***



1. **Recursively Sorting Subarrays: **After partitioning, Quick Sort recursively applies the same process to the subarrays formed by the elements to the left and right of the pivot. This continues until the entire array is sorted.



## Quick Sort in Action


---

To understand how the steps are implemented in Quick Sort, let's take an example of an array: `[9, 12, 9, 2, 17, 1, 6]`.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_12_06.png)

**Pivot + Partitioning**



Notice that the entire collection isn't fully sorted after partitioning around the pivot.

However, the elements are correctly positioned relative to the pivot. 

This means you no longer need to compare elements in the left partition with those in the right.



Now, it's time to use **recursion**. 

Take the exact same steps and apply them to the left and right partitions that still need to be sorted.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_10_05.gif)



Great! Now that all the subarrays are sorted, you can combine them into the final sorted array.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_14_11.gif)

***Combining the Subarrays***



Notice how similar this is to what you saw with merge sort recently!



## Steps to implement Quick Sort


---

Does Quick Sort create a new array and copy elements over in the correct order? Well, not exactly.

One of the many reasons Quick Sort is preferred is because it sorts efficiently without consuming extra space.



Instead, this algorithm sorts elements **in-place**. 



So, if it doesn’t copy over elements into a new array…how does it sort then? 

The answer is by ***swapping***! 



The basic steps to implement the swap functionality. It would be great to understand it with an example array `**[9, 5, 2, 6, 1, 11, 3]**`:



1. First, choose a pivot (the last element for this example).



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_18_29.png)

***Pivot Selection***



1. Then, Create a `***"i"***`*** ***reference to the index before the lowest index (the first) to track the smaller elements.
2. Create a `***"j"***` reference to the lowest index (the first) to track the larger elements.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_19_33.png)

`***i***`*** and ***`***j***`*** reference***



1. Next, compare `***j***` in relation to the pivot, independently. 
2. - If the `***j***` reference is greater than the pivot, you increment it. 

- - If the `***j***` reference is less than pivot, which means it is not in order. In this case, increment the `***i***` reference and swap the elements at the `***i***`*** ****and**** ***`***j***` references to correct their positions.

1. Continue moving the `***j***` reference and keep swapping elements until you're finished sorting the partitions.
2. The last step, move the ***pivot*** into its correct place by swapping it with the item at the `***i+1***` The last, creating the new pivot for that subarray.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__09_39_31.gif)

*Single Iteration of How Quick Sort Works *



## Pseudocode for the quick sort algorithm


---

```cpp
Algorithm QuickSort(A, low, high)
    if low < high then                   // Check if there are elements to sort
        pivotIndex = Partition(A, low, high)   // Get the pivot index using the Partition function
        QuickSort(A, low, pivotIndex - 1)      // Recursively sort the left partition
        QuickSort(A, pivotIndex + 1, high)     // Recursively sort the right partition

Algorithm Partition(A, low, high)
    pivot = A[high]                     // Choose the pivot as the last element of the array
    i = low - 1                         // Initialize the index of the smaller element
    for j from low to high-1 do         // Loop through the array
        if A[j] <= pivot then           // If the current element is less than or equal to the pivot
            i = i + 1                   // Move to the next element in the smaller partition
            swap A[i] with A[j]         // Swap the elements to maintain the partitioning
    swap A[i + 1] with A[high]          // Swap the pivot element to its correct position
    return i + 1                        // Return the index of the pivot


```



The Partition algorithm essentially partitions the array into two parts by re-arranging:

- Elements less than or equal to the pivot on the left side.
- Elements greater than the pivot on the right side.



This partitioning is then used by QuickSort to:

- Recursively sort the left partition until it's sorted.
- Recursively sort the right partition until it's sorted.



This process continues until the entire array is sorted.



Now, it's time for you to try Quick Sort! 

If you understood Merge Sort, Quick Sort should be straightforward for you to implement.



Take a look at how it should appear:


[Watch video](https://www.loom.com/embed/cfc5aeefa1e3417884b8ad4e2b35db60)




Try implementing the sort yourself in the assignment before you move on to the next lesson.

**See you there!👋🏼**
