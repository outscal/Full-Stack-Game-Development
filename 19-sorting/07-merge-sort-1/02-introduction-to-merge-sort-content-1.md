Are you excited about this algorithm? You should be!

Before getting into Merge Sort, you should understand what merging means in the context of programming.



## What is Merging?


---

Merging is the process of combining two datasets, such as arrays, lists, or strings, into a single dataset. 

Just like your jacket zip, it smoothly combines both sides to make one unit.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_15_2024__07_23_17.gif)



But hey, there's a twist with Merge Sort!



The elements in the arrays being merged must be sorted in advance.

Once two sorted arrays are available, they can be combined to form a single, fully sorted array



But for that, you need to know how to merge two sorted arrays.



## **How to Merge Two Sorted arrays?**


---

Imagine you have two sorted arrays:

Array `A`: `[2, 11, 18, 20, 22]`

Array `B`: `[4, 9, 19, 25]`


Can you merge these two arrays? 

Take your time and try to combine both arrays on your own.



> **💡Hint:** Compare the smallest elements from both arrays and add the smaller one to the new array. Repeat until all elements are merged.






---

# **Don't Scroll Down Until You're Ready!**


---



Alright, ready?



To merge them, you will need one extra array to put the merge result in it.

You can merge two sorted arrays very easily. 

Simply compare the two smallest elements and then copy the smaller one to the third array.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_15_2024__07_57_09.gif)

***Merge Two Sorted Arrays***



1. Start with *i* index in the first array,* j* index in the second array and *k* index at the third.
2. Compare the value at* i *& *j*
3. Put the smallest value in *k* & move the smallest value index to the next.
4. Keep doing that till reaching the end of one of the arrays.
5. If there are remaining elements in one of the arrays, just move them to the third array as they are.



Click here to check the Pseudocode for merging two sorted arrays.

This pseudocode ensures that the resulting array is sorted while merging two already sorted arrays.

```cpp
function MergeSorted(arr1, arr2):
    i = 0
    j = 0
    k = 0
    resultArray = new array of size length of arr1 + length of arr2

    // Merge the two sorted arrays into resultArray
    while i < length of arr1 and j < length of arr2:
        if arr1[i] < arr2[j]:
            resultArray[k] = arr1[i]
            increment i
        else:
            resultArray[k] = arr2[j]
            increment j
        increment k

    // Copy any remaining elements from arr1
    while i < length of arr1:
        resultArray[k] = arr1[i]
        increment i
        increment k

    // Copy any remaining elements from arr2
    while j < length of arr2:
        resultArray[k] = arr2[j]
        increment j
        increment k

    return resultArray
```





Now you understand how to merge two arrays.

However, what if those two arrays you merged were part of **one array**? 



For example: `[2, 5, 8, 12, 3, 6, 7, 11]`, in this array, the elements from index 0 to 3 (`[2, 5, 8, 12]`) and from index 4 to 7 (`[3, 6, 7, 11]`) are already sorted.

How will you sort these sub-arrays so that the whole array becomes sorted?



## out-of-place Merging


---

Well, you can apply the same merging concept within this array.

To do that, you can define low (l), high (h), and mid (m), which you can use to define the boundaries of the first and second subarrays.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__07_16_19.png)

***Define the two sub-array boundaries***.



Now, create another array of the same size.

Then, do exactly the same procedure, but instead of `i`, `j`, & `k` starting from `0`, make sure that:

- `i` starts from low (`l`), 
- `j` starts at mid (`m`)+1 and 
- `k` starts at low (`l`).



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__07_11_19.gif)

***Merge Two Sorted Sub-Arrays**** ****(Out-of-Place)***



This process forced you to create a temporary array, this obviously takes some extra space.
Did you know that there is an **in-place** alternative for merging as well, which doesn't require extra space to do the merging.

Let's see how that works.



## In-place Merging


---

In-place merging involves merging two sorted sub-arrays within the original array without using extra space for another array.

This method is a bit trickier than out-of-place merging. 

In-place merging swaps the elements in the original arrays instead of creating a new array to store the merged result.



Let's take the same example array: `[2, 5, 8, 12, 3, 6, 7, 11]` 

Just like before, you need to define the boundaries of the two sub-arrays using low (`l`), mid (`m`), and high (`h`).

- The first sub-array is from `l` to `m`.
- The second sub-array is from `m+1` to `h`.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__07_16_19.png)

***Define the two sub-array boundaries***.



Next, you'll perform the in-place merging by swapping elements in the original array.

Initialize a starting point `s` to `m+1`. Then, start comparing the elements at `l` and `s`.



If the element at `l` is smaller or equal, it is already in the right place, so just increment `l`.

If the element at `s` is smaller, here comes the main logic of **in-place**, you need to place it in the correct position in the first sub-array. To do this:

- Save the element at `s` in a temporary variable.
- Shift all elements from `l` to `s-1` one position to the right. (Just like in Selection Sort, to find the correct position for the smallest element.)
- Place the saved element in the position of `l`.
- Increment `l`, `m` & `s`.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_29_2024__12_06_17.gif)

***In-place Merging***



Now, you just have to repeat the process until you have processed all elements in both sub-arrays.

You can use either of the methods to merge the two subarrays; your end result will be the same: **a sorted array**.



Click here to check the Pseudocode for In-place Merging.

```cpp
inPlaceMerge(int arr[], int l, int m, int h) {
    // Initialize a pointer
    s = m + 1;

		// Check if the subarray is already sorted
		if (arr[mid] <= arr[s]) {
			return;
		}

    // Loop until one of the sub-arrays is exhausted
    while (l <= m && s <= h) {
        // If element in the first sub-array is in correct position
        if (arr[l] <= arr[s]) {
            l++;
        } else {
            // Element in the second sub-array needs to be placed in the first sub-array
            int temp = arr[s];
            
            // Shift all elements in the first sub-array to the right to make space
            for (int k = s; k > l; k--) {
                arr[k] = arr[k - 1];
            }
            
            // Place the element in the correct position
            arr[l] = temp;

            // Move all pointers forward
            l++;
            m++;
            s++;
        }
    }
}
```





Merging two sorted halves together is the base of the merge sort that you have cleared. 

Now, you will understand how a completely unsorted array can be sorted using the same method that you just learned.



## Merge Sort


---

**Merge Sort** is a classic example of a divide-and-conquer strategy applied to sorting. 



What is divide-and-conquer?Divide-and-conquer is an algorithmic paradigm that involves three main steps:

- **Divide**: Break the problem into smaller subproblems of the same type.
- **Conquer**: Recursively solve these subproblems.
- **Combine**: Combine the solutions of the subproblems to solve the original problem.



Here’s how it works for this specific algorithm:

1. **Divide:** Split the unsorted array into two roughly equal halves.
2. **Conquer:** Recursively sort each half.
3. **Combine:** Merge the two sorted halves back together.



![ ](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

***Merge Sort***



You simply keep dividing the array into halves using recursion until you have only single elements left, as each single-element array is already sorted.

Then, you merge and sort each pair of adjacent elements, slowly building up a completely sorted array.



## STEPS TO PERFORM merge SORT Out-of-place


---

- Initialize `left` to 0 and `right` to `size - 1`, where `size` is the size of the array.
- **Splitting Phase (Divide):**
- - Find the middle of the array using `mid = left + (right - left) / 2`.
  - Recursively divide the array into two roughly equal halves using `mid`.
  - - Left half: from `left` to `mid`.
    - Right half: from `mid + 1` to `right`.
  - Continue dividing each subarray until you have subarrays of only one element.
  - Check if the current segment has one element or less. If so, it's already sorted, then return.
  - - `if (left >= right) { return; }`
- **Sorting Phase (Conquer)**:
- - Merge the sorted left half (`left` to `mid`) with the sorted right half (`mid+1` to `right`).
  - - Create temporary array `temp` to hold the sorted left and right halves.
    - Use three pointers: `i` for the left subarray, `j` for the right subarray and `k` for the temporary array.
    - Compare elements from both subarrays and copy the smaller element to the temporary array.
    - Continue until all elements from any of the subarrays are copied to the temporary array.
  - If any elements are left in the left or right subarray, copy them to the temporary array.
  - Copy the sorted elements from the temporary array back to the original array.



## STEPS TO PERFORM merge SORT in-place


---

- Initialize `left` to 0 and `right` to `size - 1`, where `size` is the size of the array.
- **Splitting Phase (Divide):**
- - Find the middle of the array using `mid = left + (right - left) / 2`.
  - Recursively divide the array into two roughly equal halves using `mid`.
  - - Left half: from `left` to `mid`.
    - Right half: from `mid + 1` to `right`.
  - Continue dividing each subarray until you have subarrays of only one element.
  - Check if the current segment has one element or less. If so, it's already sorted, then return.
  - - `if (left >= right) { return; }`
- **Sorting Phase (Conquer)**:
- - Merge the sorted left half (`left` to `mid`) with the sorted right half (`mid+1` to `right`).
  - Initialize a starting point `start2` to `m+1`.
  - Check if the array is already sorted by comparing `arr[m]` and `arr[s]`. If `arr[m] <= arr[s]`, return immediately.
  - Loop until one of the sub-arrays is exhausted (`l > m` or `s > h`).
  - - Compare the current elements of the two sub-arrays.
    - If the element at `l` is smaller or equal, it is already in the right place, so just increment `l`.
    - If `arr[s]` is less than `arr[l]`, it needs to be placed in the first sub-array:
    - - Store `arr[s]` in a temporary variable.
      - Shift all elements from `l` to `s-1` one position to the right to make space for it.
      - Place it in position `l`.
      - Increment `l`, `m`, and `s` to move to the next elements in both sub-arrays.
    - Repeat the process until you have processed all elements in both sub-arrays.



Let's try it on one more example `[8, 2, 9, 6, 5, 3, 7, 4]`



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__07_18_41.gif)

***Merge Sort***



Now, it's your turn to implement in-place merge sort!

Don't worry if you encounter challenges along the way; that's part of the learning process.



Take a look at how it should appear:


<iframe src="https://www.loom.com/embed/36dcbf98b5c84f23a2d66a6e11f2dfa8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Merge Sort***


Try implementing the sort yourself in the assignment before you move on to the next lesson.

**See you there!👋🏼**
