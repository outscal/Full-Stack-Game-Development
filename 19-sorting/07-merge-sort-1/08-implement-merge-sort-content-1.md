Did you try to implement Out of Place Merge Sort yourself?

No worries if you did not. Let’s properly implement it in this lesson!



> ✅**TODO: **
> 
> 1. Create an empty private method `void processMergeSort()` 
> 2. Update the case for `MERGE_SORT`, change the name from `processInPlaceMergeSort` to `processMergeSort` inside the `sortElements()` method



Let's do a quick recap of the steps for merge sort before seeing the implementation:

- **Step 1: Divide:**
- - Calculate the midpoint: `mid = left + (right - left) / 2`.
  - Recursively sort the left subarray `A[left..mid]`.
  - Recursively sort the right subarray `A[mid+1..right]`.
- **Step 2: Conquer (Merge):**
- - Merge the two sorted subarrays `A[left..mid]` and `A[mid+1..right]` using a temporary array `temp`.
  - Use pointers `i`, `j`, and `k` for the left subarray, right subarray, and temporary array, respectively.
  - Compare elements from both subarrays, copying the smaller one to `temp`.
  - Continue until all elements from both subarrays are in `temp`.
  - Copy any remaining elements from the left or right subarray to `temp`.
  - Copy the sorted elements from `temp` back to the original array `A`.
- **Step 3: Base Case**
- - If the subarray has only one element (`left >= right`), it is already sorted.



![ ](/Full-Stack-Game-Development/images/62a0222ab85600a3.gif)

***Merge Sort***



Now, let's get our hands dirty with the actual implementation.



## **IMPLEMENT MERGE SORT**


---



Key points you should follow during the implementation:

- Keep track of array accesses and comparisons by updating relevant texts in the UI.
- Highlight key moments of the sort by changing the colours of elements during different stages of the algorithm.
- Use thread sleep operations to slow down the sort for better visualization.
- Make sure to update the positions of the sticks in the UI as the sorting progresses.
- Add sound effects to enhance the visualization experience when operations happen.



To initiate the Merge Sort, a call is made to `processMergeSort()` method, which serves as the entry point for sorting the entire array of sticks.

However, this method alone isn't enough for Merge Sort's recursive division and conquering.



## out-of-place Merge Sort - split into two halves



This one is similar to `inPlaceMergeSort()`, to achieve the recursive division of the array into smaller segments, `mergeSort(int left, int right)` method will be introduced.

To understand its working, consider an array of sticks with the following heights: `[3, 1, 6, 8, 4, 5, 7, 2]`.



This method will continue to divide the array into smaller segments. 

It will be done by calculating the midpoint (`mid`) of the current segment, which divides the array into two halves.

For example, `mergeSort(0, 8)` will split the array into `mergeSort(0, 4)` and `mergeSort(5, 8)`. 



This process continues, further dividing each segment until the base condition is reached, where the segment cannot be divided further (i.e., when `left >= right`).



![ ](/Full-Stack-Game-Development/images/fc76429ba1b214ac.gif)

***Split Into Two Halves***



> ✅**TODO: StickCollectionController**
> 
> 1. Create and implement a private method `void mergeSort(int left, int right)` and make the initial call from `processMergeSort()`



**Click here to check **`mergeSort()````cpp
void StickCollectionController::mergeSort(int left, int right){
		if (left >= right) return;
		int mid = left + (right - left) / 2;
		mergeSort(left, mid);
		mergeSort(mid + 1, right);
}
```



Done That?? Great!!

That's all for the recursive division in merge sort. 

However, you haven't implemented the logic for merging the divided segments back together. 


## out-of-place merge - merging the segments



To complete the merge sort, you need to create a method `merge()` that merges the sorted segments into one sorted array.

The `merge()` method works by comparing elements from the two halves and then combining them in sorted order. 

The only difference between `merge()` and `inPlaceMerge()` is that `merge()` uses auxiliary space to process the merging.



You may have noticed the empty spaces in the out-of-place merge sort visualization; these are due to the use of an auxiliary array.

This auxiliary array temporarily holds the elements, and when it updates the stick in the original sticks collection.

Only one stick was picked up from some random place, leaving a blank space and filling the space of the current stick.



No swapping is being made here, so you find the blank spaces.

This is the only reason to use in-place merge sort, but this is not used anywhere in real-life applications.



![ ](/Full-Stack-Game-Development/images/da139e5759cc6533.png)

***Blank Spaces***



Let's break down the steps to implement the `merge()` method by continuing the above example.



1. First, initialize a pointer to a `SoundService` object to play sound effects when processing each element.
2. Create a vector `temp` to store the merged elements, the size of the vector = `right - left + 1`.
3. Initialize variables: `i` for the first half, `j` for the second half, and `k` for the merged array.

`i = 0;  // Start of the first half in temp`
`j = mid - left + 1;  // Start of the second half in temp`
`k = left;  // Start position in the original array to merge back`



1. Initially, elements are copied from the original array (`sticks`) into a temporary vector (`temp`) for merging.
2. - To visualize this process, change the colour of the sticks to `temporary_processing_color i.e. yellow`, indicating that they are being processed and temporarily stored in the temp vector.



1. Merge elements back to the original array from temp:
2. - Compare elements from the two halves of `temp` and merge them back into `sticks`.
  - During merging, play a sound and set colour of stick being processed to `processing_element_color i.e. green`.
  - After each comparison and assignment, update stick positions and wait for a specified delay.



1. Handle remaining elements from both halves:
2. - After merging elements from both halves, there might be remaining elements in either half.
  - Handle these elements by copying them directly from the remaining half of `temp` to `sticks`.
  - Similar to merging, play a sound and update the colour of the stick being processed. After that, update stick positions and wait for a specified delay



Take care of the visualization carefully.



![ ](/Full-Stack-Game-Development/images/d8b5d5ab0d873bf1.gif)

***Merging Segments***



> ✅**TODO: StickCollectionController**

> 1. Create and implement a private method `void merge(int left, int mid, int right)` to handle merging the sorted segments.



**Click here to check **`merge()````cpp
void StickCollectionController::merge(int left, int mid, int right)
{
	SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();

	std::vector<Stick*> temp(right - left + 1);
	int i = left, j = mid + 1, k = 0;

	// Copy elements to the temporary array
	for (int index = left; index <= right; ++index) {
		temp[k++] = sticks[index];
		sticks[index]->stick_view->setFillColor(collection_model->temporary_processing_color);
		updateStickPosition();
	}

	i = 0;  // Start of the first half in temp
	j = mid - left + 1;  // Start of the second half in temp
	k = left;  // Start position in the original array to merge back

	// Merge elements back to the original array from temp
	while (i < mid - left + 1 && j < temp.size()) {
		if (temp[i]->data <= temp[j]->data) {
			sticks[k] = temp[i++];
		}
		else {
			sticks[k] = temp[j++];
		}

		sound->playSound(SoundType::COMPARE_SFX);
		sticks[k]->stick_view->setFillColor(collection_model->processing_element_color);
		updateStickPosition();  // Immediate update after assignment
		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));

		k++;
	}

	// Handle remaining elements from both halves
	while (i < mid - left + 1 || j < temp.size()) {
		if (i < mid - left + 1) {
			sticks[k] = temp[i++];
		}
		else {
			sticks[k] = temp[j++];
		}

		sound->playSound(SoundType::COMPARE_SFX);
		sticks[k]->stick_view->setFillColor(collection_model->processing_element_color);
		updateStickPosition();  // Immediate update
		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));

		k++;
	}
}

```



Now, integrate the splitting and merging to create Merge Sort.



> ✅**TODO: **`**mergeSort()**`
> 
> 1. Call this `merge()` method at the end within `mergeSort()`



**Click here to check updated **`mergeSort()````cpp
void StickCollectionController::mergeSort(int left, int right)
{
	if (left >= right) return;
	int mid = left + (right - left) / 2;

	mergeSort(left, mid);
	mergeSort(mid + 1, right);
	merge(left, mid, right);
}
```



## dramatic End effect


---

Lastly, add `setCompletedColor()` to your `processMergeSort()` to create a dramatic visual effect at the end.



> ✅**TODO: StickCollectionController**
> 
> 1. Call `setCompletedColor()` at the end of `processMergeSort()`



This is how it should look like:


<iframe src="https://www.loom.com/embed/355e9051edb54257a6b485639e01532e" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


***Out-of-Place Merge Sort***



Now, your final task to complete!



> ✅**TODO: StickCollectionController**
> 
> 1. Add `time_complexity = "O(n Log n)"` inside the `MERGE_SORT` case of `sortElements()`.



Did you see the time complexity improve from `O(n^2)` in the initial three sorts to `O(n log n)` with Merge Sort?

This seemingly small change actually makes a huge difference!

In the next lesson, we'll discuss why this is so important.

**See you in the next lesson👋🏼**
