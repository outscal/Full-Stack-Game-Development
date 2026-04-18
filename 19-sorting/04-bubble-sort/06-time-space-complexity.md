Now that you've implemented Bubble Sort, it's time to understand its performance. 

Why is the time complexity `O(n^2)`?



## Time Complexity


---

Bubble Sort repeatedly steps through the list, compares adjacent elements, and swaps them if they're in the wrong order. 

Let's analyze the worst-case, average-case, and best-case scenarios:



- **Best Case (**`**O(n)**`**)**: This happens when the array is already sorted. 
  The algorithm only needs one pass to confirm everything is in order, so it only takes `n` comparisons. 
  For, eg: `[1, 2, 3, 4, 5, 6, 7, 8, 9]`
- **Worst Case (**`**O(n^2)**`**)**: This happens when the array is sorted in reverse order. 
  In this scenario, Bubble Sort has to go through the entire array `n` times, making about `n * (n-1) / 2` comparisons and swaps. For, eg: `[9, 8, 7, 6, 5, 4, 3, 2, 1]`
- **Average Case (**`**O(n^2)**`**)**: On average, Bubble Sort still ends up comparing and swapping elements in roughly `n^2` time. 
  For, eg: `[9, 8, 7, 6, 5, 1, 2, 3, 4]`



So, why is it `O(n^2)`? 

For each element in the array, Bubble Sort has to make a pass through the remaining elements to place it correctly. 

If you have 10 elements, it takes about 10 passes, and within each pass, it does comparisons and swaps roughly 10 times. 

Hence, 10 * 10 = 100 operations, which is `O(n^2)`.



## Space Complexity


---

Next, let’s talk about space complexity.

This is measured by calculating how much additional memory an algorithm needs to complete its task.

Did Bubble Sort use any additional memory? No, it did not.



Bubble Sort is an **in-place sorting** algorithm, meaning it doesn’t require any extra space proportional to the size of the input.

It just uses a few additional variables for swapping and tracking the sort progress. 

So, it only needs a constant amount of extra space, which is `O(1)`.



## Characteristics of Bubble Sort


---

You already know that Bubble Sort is an in-place sorting algorithm, but what other characteristics does it have? 



Bubble Sort is incredibly straightforward and easy to understand.

With just two nested for loops, it repeatedly checks for descending order and swaps adjacent elements if they’re out of order. 

This makes it very simple to implement.



Did you notice it preserves the relative order of elements with equal keys?

Try sorting this list on paper using bubble sort: `[4a, 2b, 3c, 2d, 4e]`. 

After sorting, the list will be `[2b, 2d, 3c, 4a, 4e]`, where `2b` and `2d` maintain their original order, as do `4a` and `4e`.

This shows that Bubble Sort is a **stable sorting** algorithm.



## When to Use Bubble Sort


---

Bubble Sort is practical for **small datasets** where the simplicity of the algorithm outweighs the need for efficiency.

However, because it takes `O(n^2)` time, it is not suitable for sorting large datasets.



Try changing `number_of_elements` in `StickCollectionModel`.

As the number of elements grows, the process slows down significantly and may even crash.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/aac7028778f8cafc.jpg)



But don’t worry; there are better algorithms for sorting large datasets.

You'll cover these efficient algorithms later.

Just stay patient and focus on clearing the fundamentals of sorting for now.



**See you in the next chapter👋🏼**
