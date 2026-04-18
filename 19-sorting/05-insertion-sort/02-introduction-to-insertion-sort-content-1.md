As you know from the last lesson, Insertion Sort compares elements and swaps them to sort the list. 

Now, let’s understand how it actually does this.



## understanding insertion sort


---

On a very basic level, an ***insertion sort algorithm*** contains the logic of dividing the array into a sorted and unsorted section, picking elements from the unsorted part, and then placing them in order in the ordered section. 



If you have no remaining elements in the unsorted portion, then the array is sorted!



Let's look at all of this in a bit more detail now.



- Start with an unsorted dataset.



![ ](/Full-Stack-Game-Development/images/4bc7c810b1c9ce82.png)

***Unsorted Dataset***

- Initially, only the first element is "Sorted".

![ ](/Full-Stack-Game-Development/images/06e672574b810778.png)



- Remove the first unsorted element and insert it into the sorted subset by comparing it with its items. 
- - If the unsorted element is smaller than the sorted element; then shift the sorted element backwards to make room.
  - Otherwise, if it's larger than the sorted element, it stays as it is.

![ ](/Full-Stack-Game-Development/images/4b04442683519ddf.gif)

***Case 1***



This was only a single iteration of how insertion sort works. 

In our example, the sorted subset had only one item to compare. 

But what happens when the sorted subset grows?



When the sorted subset grows, the number of shifts increases. 

As the algorithm continues to iterate through the unsorted subset, it picks elements one by one and places them in their correct positions within the sorted subset.



Imagine you have an unsorted dataset like this: `[6, 5, 3, 1, 8, 7, 2, 4]`.

![ ](/Full-Stack-Game-Development/images/59cbb2c37f857d01.gif)

*Insertion Sort *

Did you notice something?

- Initially, only the first element, `6`, is considered sorted.
- Then, the second element, `5`, from the unsorted subset is taken and compared with the sorted subset.
- - Since `5` is smaller than `6`, it shifts `6` one position to the right to make room for `5`.
  - Resulting in: `[5, 6, 3, 1, 8, 7, 2, 4]`
- Next, it takes 3 and compares it with the sorted subset `[5, 6]`.
- - 3 is smaller than both, so they are shifted to the right to make room for 3.
  - Resulting in: `[3, 5, 6, 1, 8, 7, 2, 4]`
- It continues this process with the remaining elements of the unsorted subset `[1, 8, 7, 2, 4]`, placing each element in its correct position within the growing sorted subset.



The process involves multiple shifts as the sorted subset grows.

However, if you didn't notice, no shift was made when the element was already in sorted order. 



Let's finalize the steps you need to perform for this sort before you do your assignment.



## STEPS TO PERFORM Insertion SORT


---

1. Start the sorting from the second element because the first element is already considered sorted.
2. Initialize a `**key**` variable that holds the value of the element that needs to be inserted into the sorted portion of the array.
3. Then, iterate through the sorted subset in the reverse direction to find the correct position for the `key`
4. - Shift all elements that are greater than `key` to the right.
5. Once the correct position is found (When you encounter an element less than `**key**` or reach the beginning of the array), `**key**` is placed in its correct position.
6. Continue this process for each element in the unsorted part of the array until the entire array is sorted.



Now, it's time for you to try Insertion Sort! 

If you understood Bubble Sort, Insertion Sort should be straightforward for you to implement.



Take a look at how it should appear:


<iframe src="https://www.loom.com/embed/9ebd20625c8146f09ba312743de19801" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Insertion Sort***



Try implementing the sort yourself in the assignment before you move on to the next lesson.

**See you there!👋🏼**
