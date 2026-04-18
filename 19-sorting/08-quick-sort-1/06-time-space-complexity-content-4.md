If you don't know, Quick Sort is often the default choice for the sorting algorithm in many standard libraries. 

Let's explore why this is so! 🧐



## Time Complexity


---

Quick Sort, similar to Merge Sort, has a time complexity of `**O(nlog n)**`.



In the best and average case, each partition operation divides the array into two halves. 

This results in a balanced recursive tree structure, with each level of the tree requiring `**O(n)**` operations, and there are `**O(log⁡n)**` level.



**Example:** Sorting `**[3, 6, 8, 10, 1, 2, 1]**`

Let's pick the middle element as the pivot `**(8)**`. 

Partitioning the array around the pivot `**(8)**` : Left: `**[3, 6, 1, 2, 1]**`  & Right: `**[10]**`

Sort `**[3, 6, 1, 2, 1]**` with pivot `**(2)**`: Left: `**[1, 1]**` & Right: `**[3, 6]**`

Combine all parts: `**[1, 1, 2, 3, 6, 8, 10]**`



Did you notice something? 

Choosing a *good* pivot, one that divides the array into nearly equal parts, ensures we get the best performance of `**O(nlog n)**`.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/67aa1884cbe38a50.png)

*Choosing a ****good**** pivot*



But what if we make *poor* choices for the pivot, consistently picking the smallest or largest element in the array?

This will end up degrading Quick Sort's time complexity to `**O(n²)**`. This is the worst-case scenario.



**Example: **Sorting `**[1, 2, 3, 4, 5]**`

Pivot selection involves always picking the last element as the pivot.

Partitioning the array around the pivot `**(5)**` : Left: `**[1, 2, 3, 4]**`  & Right: `**[]**`

Sort `**[1, 2, 3, 4]**` with pivot 4: Left: `**[1, 2, 3]**` & Right: `**[]**`

Continue similarly until the entire array is sorted.



Each partitioning step results in one subarray of size `**n−1**` and another of size 0, leading to a highly unbalanced tree with `**n**` levels.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/9269d49942b4edf1.png)

*Choosing a ****bad**** pivot*



Each level takes `**O(n)**` time, and there are `**n**` levels, leading to `**O(n²)**` time complexity.



## Space Complexity


---

As you know, Quick Sort's **in-place sorting** means it doesn’t copy over elements into a new array.

Instead, it swaps elements in the existing array to sort them. This characteristic makes it memory-efficient compared to merge sort.



But it doesn't mean that it doesn't use any memory to sort the data.

Quick Sort still requires additional memory for its recursion stack during the sorting process.

The space complexity of Quick Sort depends on the implementation and the depth of the recursion stack.



In the best and average cases, Quick Sort has a space complexity of `**O(log⁡n)**`, where `**n**` is the number of elements to be sorted. 

This is due to the logarithmic depth of the recursion stack means in the best and average case of time complexity.



However, in the worst case, particularly when the pivot selection is *poor*, Quick Sort's space complexity can degrade to `**O(n)**`, where `**n**` is the number of elements.



## Important Characteristics of Quick Sort


---

- In efficient implementations, Quick Sort is an **unstable sort**, meaning that the relative order of equal sort items is not preserved.
- Since Quick Sort is an **in-place sorting** algorithm, it is well-suited for situations where memory usage is a concern.
- Although Quick Sort performs well on average, its worst-case time complexity of `**O(n²)**` can be a drawback for certain scenarios.
- Quick Sort is often used in database management systems to sort large datasets efficiently.



Since you're familiar with Quick Sort now, let's have a debate about which sorting algorithm, between Merge Sort and Quick Sort.



**See you in the next lesson👋🏼**
