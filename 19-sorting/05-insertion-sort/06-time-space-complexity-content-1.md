The time and space complexity of Insertion Sort isn't very different from Bubble Sort.

It all depends on the number of comparisons made and the extra space taken to process the sort.



## Time Complexity


---

Insertion Sort operates by dividing the array into a sorted and an unsorted region.

It repeatedly picks the first element from the unsorted region and inserts it into the correct position in the sorted region.



In the **worst-case scenario**, where the array is sorted in reverse order (e.g., `[5, 4, 3, 2, 1]`), each insertion requires shifting all previously sorted elements. For instance:

- Inserting the second element requires 1 comparison and shift.
- Inserting the third element requires 2 comparisons and shifts.
- Inserting the fourth element requires 3 comparisons and shifts.
- And so on



This forms an arithmetic series: `T(n)=1+2+3+…+(n−1)`. 

The sum of the first `n−1` integers is: `T(n)=((n−1)*n)/2`, resulting in a worst-case time complexity of `**O(n^2)**`.



In the **best-case scenario**, where the array is already sorted (e.g., `[1, 2, 3, 4, 5]`), each element is compared once with no shifts needed. 

Thus, the total number of comparisons is `T(n)=n−1`, leading to a best-case time complexity of `**O(n)**`.



In the **average case**, the elements are in random order. On average, an element might be compared to half of the previously sorted elements before finding its correct position.

Therefore, the average-case complexity also turns out to be `**O(n^2)**`.



## Space Complexity


---

Insertion Sort is an **in-place** sorting algorithm, meaning it only requires a constant amount of additional memory space for variables.

It just uses one additional variable for `key`.

So, it only needs a constant amount of extra space, which is `**O(1)**`.



## CHARACTERISTICS OF Insertion SORT


---

- **Simple Implementation:** Just like Bubble Sort, Insertion Sort is easy to implement and understand.
- **Stable Sort:** Insertion Sort maintains the relative order of equal elements. 
- **Adaptive:** It is adaptive, meaning that its performance improves with a partially sorted input. The closer the input list is to being sorted, the faster it will complete.



## **Applications**


---

- **Small Data Sets:** Insertion Sort is efficient for small arrays due to its simplicity and low overhead.
- **Nearly Sorted Arrays:** It's particularly effective when the array is already or nearly sorted.
- **Online Sorting:** Can sort a list as new elements come in, making it suitable for real-time applications.



While it may not always be the best choice for large datasets, it can still be used to teach sorting.



There are still more sorting algorithms to learn.

Let's keep Going!



**See you in the next chapter👋🏼**
