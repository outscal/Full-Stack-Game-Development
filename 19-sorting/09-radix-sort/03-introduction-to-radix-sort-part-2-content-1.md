So far, you know that Radix Sort is a non-comparison-based sorting algorithm that sorts numbers by processing their digits from the least significant to the most significant.

But to achieve this, Radix Sort relies on another sorting technique: Counting Sort.



## what is counting sort?


---

Counting Sort is a sorting algorithm that works well when the range of elements in the input array is small compared to the array's size.



The fundamental idea behind Counting Sort is to count the number of occurrences of each unique element in the input array and then use that information to arrange the elements in sorted order.



Counting sort assumes that you know your input's range, which is actually the difference between the maximum and minimum values of the array elements.



Let's understand it with an example:

Sorting an array `A` with just eight elements: `[9, 4, 1, 7, 9, 1, 2, 0]`. 

Notice that there are some duplicate values, which is totally okay!



In this situation, you know that the data you’re sorting will always range between 0 and 9.

You’ll start by creating the “count array” of the size `(9 - 0) + 1 = 10`.



When you initialize your “count array”, every single index starts off with an initial value of `0`. 

Then, you’ll need to populate your “count array” with the tallied elements from your unsorted input array.

- Count the occurrences of each element: `0(1), 1(2), 2(1), 4(1), 7(1), 9(2)`.
- Populate the count in the “count array”.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__10_06_42.png)

*Counting occurrences & updating ****count**** array*



The next step involves some math — but don’t worry, it won’t be too difficult! 

All you need to do is accumulate and add each pair of consecutive values in our count array.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__10_08_12.png)

*Accumulating ****count**** array*



Let's think about why this step is important.

Each number in the count array helps you determine where the last instance of that digit will be in the sorted array.



For example, the value of index `9` in your count array is `8`.

This means the last `9` in our array will be at position `(8-1) = 7` in our sorted array.

Try this for all other indexes on paper, and you'll see how it works!



Next, create an `output` array of the same length as `A`, initialized with `0's`: output = `[0, 0, 0, 0, 0, 0, 0, 0]`



Now, place each element from `A` in its correct position according to the logic in the output array and decrement the count for that digit:



- Original Array (`**A**`): `[9, 4, 1, 7, 9, 1, 2, 0]`
- Count Array (`**count**`): `[1, 3, 4, 4, 5, 5, 5, 6, 6, 8]`
- Output Array (`**output**`): `[0, 0, 0, 0, 0, 0, 0, 0]`


By decrementing the count for each digit, you can find the positions for all occurrences of that digit in the sorted array, starting from the last and moving to the first.



Iterate through elements in `A` from right to left to ensure that the sort is **stable **(equal elements retain their original relative order).

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__10_34_01.gif)

`***i***`*** is the Element of Original Array***



After processing all elements from right to left, the `output` array becomes: 

`output` = `[0, 1, 1, 2, 4, 7, 9, 9]`

The last step is to copy the `output` array back to the original array `A`:

`A` = `[0, 1, 1, 2, 4, 7, 9, 9]`



Nice! Your array = sorted. And your situation = handled. **Good work!**



Let's review the basic steps of counting sort.

- Find the range of the input values.
- Create a count array of size equal to the range, initialized to 0.
- Iterate through the input array and count the occurrences of each digit. Store these counts in the count array.
- - `count[A[i]] = count[A[i]] + 1`
- Modify the count array such that each element at index `i` contains the cumulative count of elements up to `i`. 
  This will help in placing the elements in the correct position.
- - `count[i] = count[i] + count[i - 1]`
- Create an output array of the same length as the input array, initialized to 0.
- Iterate through the input array from right to left to maintain stability.
- - For each element, find its position in the output array using the count array, place it, and 
    then decrement the count.
  - `index = A[i]`
    `index = count[index] - 1`
    `output[index] = A[i]`
    `count[index]--`
- Copy the sorted output array back to the original array.



That's all about the counting sort.

Let's see how you integrate the counting sort into the radix sort.



## Integrating count sort into radix sort


---

In radix sort, the range for the counting sort is determined by the digit places of the numbers in the array. 

Since you're sorting each digit individually, the range will always be from **0 to 9**.



So, the size of the "count array" will always be 10.



Let's continue with the same example from the last lesson: 

You have an array `[10, 52, 5, 209, 19, 44]`

Which was rewritten as `[010, 052, 005, 209, 019, 044]`



Using counting sort, sort the numbers by their rightmost digit (units place).

To find the unit place, you can use the remainder operation.

By dividing each number by 10 and taking the remainder, you get the unit place digit.



For example:

- 010 % 10 = 0
- 052 % 10 = 2
- 005 % 10 = 5
- 209 % 10 = 9
- 019 % 10 = 9
- 044 % 10 = 4



Next, you'll use counting sort on these unit digits:

- Count the occurrences of each digit (`0-9`).
- Modify the count array to position the elements correctly.
- Place the elements in the sorted order based on the unit's place.



After running your dataset through counting sort using the unit place as our *keys*, our array is slightly more sorted.

It now looks like this: `[010, 052, 044, 005, 209, 019]`



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__10_40_53.png)

***Radix sort on LSD (units digit)***



If you notice, the array is now sorted by the unit digits.

Also, see how `19` and `209` appear in the same order as they did in the original array.



However, you want to sort these integers as entire numbers, not just by the unit place! 

So, you’ll need to sort by the next place value: **the tens**.



After our second pass through our array, it now like this: `[005, 209, 010, 019, 044, 052]`

Notice how the numbers are now sorted by the second digit. 

The number `52`, which has the largest value for the tens place with `5`, is now at the end of the array.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__10_41_48.png)

***Radix sort on tens digit***



But is the array fully sorted? Not yet!

So do the same thing with next place value: **the hundreds**.



After running counting sort this third time, all the numbers are completely sorted.

Our array now looks like this: `[005, 010, 019, 044, 052, 209]`.



After removing the extra zeros, our sorted array looks like this: `[5, 10, 19, 44, 52, 209]`.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__10_42_33.png)

***Radix sort on hundreds digit***



Your array is sorted. Pretty cool, right?



But how can you determine when to stop? 

Why do you only need three passes in this example?



Knowing when to stop in Radix Sort depends on the maximum number of digits in the input data.

In our example, since the largest number is `209` with three digits, you needed three passes to ensure all digits were sorted correctly.



In this case, you were dealing with only numbers that had a radix of three. 

However, you can imagine that if you had to deal with numbers with radixes of five, ten, or fifteen…, you’d have to make five, ten, or fifteen passes through our array to sort them.



To sort the dataset using radix sort, follow these steps.



## steps to perform radix sort


---

- Find the maximum element to know the number of digits/passes
- Begin sorting by the least significant digit (units place) and move towards the most significant digit.
- - Start a loop from unit digit and increment the digit place by multiplying 10 in each iteration.
  - Ensures that the loop continues as long as there are more digit places to sort.
  - `for exponent = 1 to maxElement/exponent > 0 by exponent *= 10`
- Use a stable sorting algorithm like Counting Sort to sort the elements based on each digit's value.
- Repeat the sorting process for each digit place until reaching the most significant digit.
- Combine the sorted arrays to get the final sorted dataset.



Now, it's time for you to try Radix Sort! 

Take a look at how it should appear:


[Watch video](https://www.loom.com/embed/b51a3f77a13745f485fd354126b2b10d)



***Radix Sort***



Try implementing the sort yourself in the assignment before you move on to the next lesson.

So, let’s get *sorting* — one last time!



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_19_2024__10_48_17.gif)



**See you there!👋🏼**
