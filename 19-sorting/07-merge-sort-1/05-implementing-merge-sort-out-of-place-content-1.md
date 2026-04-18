Hey!! Have you already tried creating the merge sort visualizer?

Whether you have or haven't, no worries!

In this lesson, we'll walk through the entire process step by step. 



> ✅**TODO: **
> 
> 1. Uncomment the button bindings for Merge Sort in `MainMenuUIController`
> 2. Create an empty private method `void processInPlaceMergeSort()` in `StickCollectionController`
> 3. Create a case for `MERGE_SORT` and call the `processInPlaceMergeSort` inside the `sortElements()` method in `StickCollectionController`.



Let's do a quick recap of the steps for merge sort before seeing the implementation:

- **Step 1: Divide:**
- - Calculate the midpoint: `mid = left + (right - left) / 2`.
  - Recursively sort the left subarray `A[left..mid]`.
  - Recursively sort the right subarray `A[mid+1..right]`.
- **Step 2: Conquer (Merge):**
- - Initialize a pointer `start2` to `mid + 1`.
  - Check if the subarrays are already sorted by comparing `A[mid]` and `A[start2]`. If `A[mid] <= A[start2]`, return immediately.
  - Loop while `left <= mid` and `start2 <= right`:- If `A[left] <= A[start2]`, increment `left`.
    - Otherwise, store `A[start2]` in a temporary variable `value`.
    - Shift all elements from `left` to `start2-1` one position to the right.
    - Place `value` at `A[left]`.
    - Increment `left`, `mid`, and `start2`.
- **Step 3: Base Case**
- - If the subarray has only one element (`left >= right`), it is already sorted.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_21_2024__09_07_28.gif)

**Merge Sort**



Now, let's get our hands dirty with the actual implementation.



## **IMPLEMENT MERGE SORT**


---



Key points you should follow during the implementation:

- Keep track of array accesses and comparisons by updating relevant texts in the UI.
- Highlight key moments of the sort by changing the colours of elements during different stages of the algorithm.
- Use thread sleep operations to slow down the sort for better visualization.
- Make sure to update the positions of the sticks in the UI as the sorting progresses.
- Add sound effects to enhance the visualization experience when operations happen.



To initiate the Merge Sort, a call is made to `processInPlaceMergeSort()` method, which serves as the entry point for sorting the entire array of sticks.

However, this method alone isn't enough for Merge Sort's recursive division and conquering.



## in Place Merge Sort - SPLIT INTO TWO HALVES



To achieve the recursive division of the array into smaller segments, `inPlaceMergeSort(int left, int right)` method will be introduced.



To understand its working, consider an array of sticks with the following heights: `[3, 1, 6, 8, 4, 5, 7, 2]`.



During the first function call to `inPlaceMergeSort()`, it's necessary to correctly identify the starting left and right indices for the entire array. At this stage, the only segment you have to sort is the whole array itself. 

So, the starting left index for the entire array is `0`, and the right index is `size - 1`, where `size` is the size of the array.



Therefore, when `inPlaceMergeSort()` initiates the first call, `inPlaceMergeSort(0, arraySize - 1)` is used to cover the entire range of elements in the array.



Now comes the recursive part.

This method will continue to divide the array into smaller segments. 

It will be done by calculating the midpoint (`mid`) of the current segment, which divides the array into two halves.

For example, `inPlaceMergeSort(0, 8)` will split the array into `inPlaceMergeSort(0, 4)` and `inPlaceMergeSort(5, 8)`. 



This process continues, further dividing each segment until the base condition is reached, where the segment cannot be divided further (i.e., when `left >= right`).



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__07_20_57.gif)

**Split Into Two Halves**



> ✅**TODO: StickCollectionController**
> 
> 1. Create and implement a private method `void inPlaceMergeSort(int left, int right)` and make the initial call from `processMergeSort()`



**Click here to check **`processInPlaceMergeSort()`

```cpp
void StickCollectionController::inPlaceMergeSort(int left, int right)
{
	if (left < right) {
		int mid = left + (right - left) / 2;
		inPlaceMergeSort(left, mid);
		inPlaceMergeSort(mid + 1, right);
	}
}
```



Done That?? Great!!

That's all for the recursive division in merge sort. 

However, you haven't implemented the logic for merging the divided segments back together. 



## in Place Merge - MERGING THE SEGMENTS



To complete the merge sort, you need to create a method `inPlaceMerge()` that merges the sorted segments into one sorted array. This is where the actual visualisation comes into play, making the sorting process interactive.



The `inPlaceMerge()` method works by comparing elements from the two halves and then combining them in sorted order. 

Let's break down the steps to implement the `inPlaceMerge()` method by continuing the above example.



1. First, initialize a pointer to a `SoundService` object to play sound effects when processing each element.
2. Set the starting index for the second subarray (`start2`) to `mid + 1`.
3. Initialize variables: `i` for the first half, `j` for the second half, and `k` for the merged array.
4. Check If Already Sorted:

- - Compare the last element of the first subarray with the first element of the second subarray. 
  - If the last element of the first subarray is already less than or equal to the second, then no merging is needed.



1. Merge Subarrays In-Place:
2. - Use two pointers (`left` and `start2`) to compare and merge elements directly into the original array (`sticks`).
  - Shift elements to the right as needed to place elements from the second subarray into their correct position in the first.
3. Visualize the Process:
4. - Play a sound effect and update the visual representation (stick colours) during each comparison and merging operation.
  - Introduce a delay for visualization after each operation.



Take care of the visualization carefully.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_26_2024__07_25_32.gif)

**Merging Segments**



> ✅**TODO: StickCollectionController**

> 1. Create and implement a private method `void inPlaceMerge(int left, int mid, int right)` to handle merging the sorted segments.



**Click here to check **`inPlaceMerge()`

```cpp
void StickCollectionController::inPlaceMerge(int left, int mid, int right)
{
	SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();
	int start2 = mid + 1;

	// If the direct merge is already sorted
	if (sticks[mid]->data <= sticks[start2]->data) {
		number_of_comparisons++;
		number_of_array_access += 2;
		return;
	}

	// Two pointers to maintain start of both arrays to merge
	while (left <= mid && start2 <= right) {
		number_of_comparisons++;
		number_of_array_access += 2;
		if (sticks[left]->data <= sticks[start2]->data) {
			left++;
		}
		else {
			Stick* value = sticks[start2];
			int index = start2;

			// Shift all the elements between element 1 and element 2, right by 1.
			while (index != left) {
				sticks[index] = sticks[index - 1];
				index--;
				number_of_array_access += 2;
			}
			sticks[left] = value;
			number_of_array_access++;

			// Update all the pointers
			left++;
			mid++;
			start2++;

			// Visual updates for position changes
			updateStickPosition();
		}

		// Instant color change
		sound->playSound(SoundType::COMPARE_SFX);
		sticks[left - 1]->stick_view->setFillColor(collection_model->processing_element_color);
		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));
		sticks[left - 1]->stick_view->setFillColor(collection_model->element_color);
	}
}
```





Now, integrate the splitting and merging to create Merge Sort.



> ✅**TODO: **`**inPlaceMergeSort()**`
> 
> 1. Call this `inPlaceMerge()` method at the end within `inPlaceMergeSort()`



**Click here to check updated **`inPlaceMergeSort()`

```cpp
void StickCollectionController::inPlaceMergeSort(int left, int right)
{
	if (left < right) {
		int mid = left + (right - left) / 2;

		inPlaceMergeSort(left, mid);
		inPlaceMergeSort(mid + 1, right);
		inPlaceMerge(left, mid, right);
	}
}
```





## DRAMATIC END EFFECT


---

Lastly, add `setCompletedColor()` to your `processInPlaceMergeSort()` to create a dramatic visual effect at the end.



> ✅**TODO: StickCollectionController**
> 
> 1. Call `setCompletedColor()` at the end of `processInPlaceMergeSort()`



This is how it should look like:


<iframe src="https://www.loom.com/embed/36dcbf98b5c84f23a2d66a6e11f2dfa8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***In-Place Merge Sort***



Now, your final task to complete!



> ✅**TODO: StickCollectionController**
> 
> 1. Add `time_complexity = "O(n Log n)"` inside the `MERGE_SORT` case of `sortElements()`.



That's all to implement the In-place Merge Sort.

Now is the time to implement the Out-of-Place Merge Sort.

You did it. You can do that as well. 💪



Take a look at how it should appear:


<iframe src="https://www.loom.com/embed/355e9051edb54257a6b485639e01532e" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Out-of-Place Merge Sort***



Try implementing the sort yourself in the assignment before moving on.

Also, see if you can spot something fishy; if you can't, we'll point it out in the next lesson. 😜

**See you there👋🏼**
