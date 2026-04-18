Time to understand Bubble Sort, one of the simplest way to sort data.

But first, a quick activity! Arrange the following list in ascending order:

![ ](/Full-Stack-Game-Development/images/10a3b7d9551a4c03.jpg)



Take your time and think about how you would sort this list. Write down your approach.



![ ](/Full-Stack-Game-Development/images/ae9713165ddb95b9.png)

🕛...🕧...🕐...🕜...🕑...🕝...🕒...

Great! How did you approach the problem?

You might have considered moving each larger number to the end one by one.

At the moment, it's easy for us (humans) to identify which element is bigger because there are only 8 elements.



However, imagine if there were around 100 elements in the list. How would your approach change?

You would visit each element one by one, comparing it with the next element and swapping, if necessary, until the largest element makes its way to the end of the list.

This process repeats until the entire list is sorted.



This is exactly the concept behind **Bubble Sort**!

This method works well but can become time-consuming and inefficient as the number of elements increases.



## What is Bubble Sort?


---

In **Bubble sort**, each element is compared with its adjacent element. 

If the first element is bigger than the second one, the positions of the elements are interchanged; otherwise, they are not changed.

Then, the next element is compared with its adjacent element, and the same process is repeated for all the elements until we get a sorted array.

For example: `[6, 5, 8]`

1. - Compare `6` and `5`. Since `6` > `5`, swap them. List after swap `[5, 6, 8]`
  - Compare `6` and `8`. Since `6` < `8`, no swap is needed.



Let's sort the above example array `[6, 5, 3, 1, 8, 7, 2, 4]` :

![ ](/Full-Stack-Game-Development/images/bad6cc3917b5e972.gif)

*Bubble Sort *

Did you notice something?

After each pass, you compare one fewer pair of elements compared to the previous pass.

This is because with each pass, the largest unsorted element "**bubbles up**" to its correct position at the end of the list. 

Thus, you don't need to compare it again in the subsequent passes.



## Bubble Sort Algorithm Pseudocode


---

Below is the pseudocode for the Bubble Sort algorithm.

This will give you a clear, step-by-step understanding of how Bubble Sort works.

Try to follow along and see how each pass helps sort the array!



```cpp
// Bubble Sort Algorithm Pseudocode
// procedure bubbleSort takes an array 'A' as input
procedure bubbleSort(A)
    // Get the number of elements in the array
    n = length(A)
    // Repeat the sorting process until the array is sorted
    repeat
        // Variable 'swapped' tracks whether any elements were swapped in this pass
        swapped = false
        // Iterate over the array from the first element to the second-to-last unsorted element
        for i = 1 to n-1 inclusive do
            // Compare the current element with the next element
            if A[i-1] > A[i] then
                // Swap the elements if they are in the wrong order
                swap A[i-1] with A[i]
                // Mark that we made a swap in this pass
                swapped = true
            end if
        end for
        // After each complete pass, the largest element is in its correct place,
        // so reduce 'n' by 1 because the last element is sorted
        n = n - 1
    // Continue sorting until no elements were swapped in the last pass
    until not swapped
end procedure

// Note: The swap operation exchanges the values of two elements in the array.
// For example, if A[i-1] = 3 and A[i] = 1, after swap A[i-1] = 1 and A[i] = 3.
```



Try the pseudocode with the same example array `[6, 5, 3, 1, 8, 7, 2, 4]`.

The output you should get is `[1, 2, 3, 4, 5, 6, 7, 8]`.



Now it's your turn to create Bubble Sort with the above pseudocode. 

Just take care of a few things when you implement sorting algorithms:

- Update the positions of the sticks after each pass.
- Make the sticks change colour to green when their position is known to be correct.
- When no swaps are needed, all sticks should turn green.



Take a look at how it should appear:




<iframe src="https://www.loom.com/embed/27d2b629ebf241d39366c7ed37c129ee" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Bubble Sort in Action***



Try implementing the sort yourself in the assignment before you move on to the next lesson.

**See you there!👋🏼**
