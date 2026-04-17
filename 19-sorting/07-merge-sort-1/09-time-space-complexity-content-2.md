## **Time Complexity**


---

The time complexity of Merge Sort is `**O(nlogn)**` in all the 3 cases (worst, average and best.

To calculate the time complexity, divide the whole operation into two parts:



First is the **divide phase** of the merge sort...

In this phase, the input array is recursively divided into halves until each subarray contains a single element. 

Just like you did during the binary search.



Suppose you start with an array of size `n`.

After the first division, there are two subarrays of size `n/2` each. 

After the second division, there are four subarrays of size `n/4` each, and this pattern continues.

This division process continues until each subarray contains only one element, resulting in `**log(n)**` divisions.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_04_31.png)

`***O(log(n))***`*** time complexity***



In the second or **merge phase**, the sorted subarrays are merged back together to create larger sorted subarrays until the entire array is sorted.

Each merge operation compares and combines elements from two subarrays, resulting in `**O(n)**` time complexity relative to the size of the merged subarrays.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__08_02_46.png)

`***O(n)***`*** time complexity***



Combining the divide and merge phases, the total time complexity of the merge sort can be expressed as `**O(n*log(n))**`, where `**n**` is the size of the input array.



This complexity comes from `**logn**` divisions in the divide phase, each followed by merge operations that take `**O(n)**` time relative to the size of the subarrays being merged.



## Comparison with Bubble Sort, Selection Sort, and Insertion Sort


---

Merge Sort's time complexity surpasses Bubble Sort, Selection Sort, and Insertion Sort, all of which have a time complexity of `**O(n²)**`** **

Let's compare these algorithms mathematically. 



Take an array with n = 8 elements:

- Merge Sort: 8 * log₂(8) = 24 operations
- Bubble Sort: 8² = 64 operations
- Selection Sort: 8² = 64 operations
- Insertion Sort: 8² = 64 operations



I know you are amazed by the efficiency gap between Merge Sort and these quadratic-time sorting algorithms.

Now, suppose you have an array with n = 1000 elements.

Try yourself, and you will see the difference.



Click here to check the answer.- Merge Sort: 1000 * log₂(1000) ≈ 1000 * 10 = 10,000 operations
- Bubble Sort: 1000² = 1,000,000 operations
- Selection Sort: 1000² = 1,000,000 operations
- Insertion Sort: 1000² = 1,000,000 operations



## Space Complexity


---

In Merge Sort, when you merge two sorted arrays into one larger array, you need space to store the merged result.

This extra space comes from creating an auxiliary (temporary) array during the merging process.



Consider merging two arrays, each with `**n/2**`​ items. 

The total number of items being merged is `**n/2 + n/2 = n**`. 

Therefore, you'll require `**O(n)**` extra space for the auxiliary array.



So, the space complexity of Merge Sort due to this auxiliary array is `**O(n)**`.

The auxiliary array is used to store the merged result, and the input array is overwritten with the sorted result.



While there is no space taken in the **In-place Merge Sort**. 

So, the space complexity for it is `**O(1)**`.



## Characteristics of Merge Sort


---



- **Divide and Conquer Approach**: Merge Sort splits the array into halves, sorts each half, and merges them back together.



- **Recursive Approach**: Merge sort is typically implemented using a recursive approach.



- **Efficient Time Complexity**: Merge Sort boasts an efficient time complexity of O(n log n) in all cases (worst, average, and best).

  It is highly efficient and fast for sorting large datasets.



- **Stable Sorting Algorithm**: Merge Sort is a stable sorting algorithm, meaning that equal elements retain their relative order after sorting. Try to sort `[4a, 3, 4b, 2]` this array.



- **Out-of-Place Sorting**: It is not an in-place sorting algorithm, as it requires **extra memory** for the **temporary arrays** used during the merge process.



- **Non-Adaptive**: It performs the same number of operations regardless of whether the input data is already sorted, partially sorted, or in reverse order. 



- **External Sorting**: Merge Sort is particularly useful for sorting data that doesn't fit into memory.



Remember the Amazon example in Project Goal? 

Online retailers like Amazon or eBay use Merge Sort to arrange large inventories. Sorting products by price, rating, or popularity improves user experience.



> **💡Pro Tip: **Although in-place merge sort was better in visualization, out-of-place merge sort is the one being used in real-life applications because it is much more efficient at the worst case.



That's all about Merge Sort! ✨

In the next chapter, you will find a worthy competition of Merge Sort.



**See you there👋🏼**
