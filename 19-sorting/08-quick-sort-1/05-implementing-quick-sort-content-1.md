Already tried Quick Sort? If not, don't worry. 

You'll go through it step by step and create a visualizer for Quick Sort in no time!



> ✅**TODO: **
> 
> 1. Uncomment the button bindings for Quick Sort in `MainMenuUIController`
> 2. Create an empty private method `void processQuickSort()` in `StickCollectionController`
> 3. Create a case for `QUICK_SORT` and call the `processQuickSort` inside the `sortElements()` method in `StickCollectionController`.




Let's quickly recap the pseudocode for Quick Sort:

- **Choose Pivot:** Select a pivot element, often the last one in the array.
- **Partitioning:** Rearrange elements so that smaller ones are before the pivot and larger ones are after it, using two pointers moving towards each other.
- **Recursive Calls:** Apply Quick Sort recursively to the left and right subarrays formed by the pivot.
- **Base Case:** Stop recursion when subarrays have less than two elements, considering them sorted.



![ ](/Full-Stack-Game-Development/images/6b0e35ee4de11d4a.gif)

***Quick Sort***


Now, let's integrate the Quick Sort logic with the sticks in your program.



## **IMPLEMENT quick SORT**


---

Key points you should follow during the implementation:

- Keep track of array accesses and comparisons by updating relevant texts in the UI.
- Highlight key moments of the sort by changing the colours of elements during different stages of the algorithm.
- Use thread sleep operations to slow down the sort for better visualization.
- Make sure to update the positions of the sticks in the UI as the sorting progresses.
- Add sound effects to enhance the visualization experience when operations happen.



Like Merge Sort, `processQuickSort()` initiates the Quick Sort process for the entire array of sticks, which alone isn't enough for recursive division and conquering. To perform recursive operations, use `quickSort(int left, int right)`.



To divide the array into smaller segments in Quick Sort, you need a pivot index that is used to partition the array.

To find the pivot index, create a new method `partition(int left, int right)` that returns an integer, which signifies the pivot index.



## partition - Dividing the Array



To understand this method, consider an array of sticks with the following heights: `**[5, 7, 1, 3, 9, 2, 8, 6, 4]**`.



Let's choose the last element `4` as the pivot.



In the partition function, start by setting the pivot element to `selected_element_color (i.e. blue)` to highlight it on the screen.

Then initialize `i` to the index before the lowest index (i.e `left - 1`) to keep track of the smaller elements.



![ ](/Full-Stack-Game-Development/images/d3f56e8296b4704a.png)

*Pivot Selection*



For each element of the stick array from `left` to `right - 1`, compare it with the pivot element. 

If the current element is smaller than the pivot, increment `i` and swap the current element with the element at `i`.

For example, 

- `5` > `4`, so no swap, `i` remains `-1`.
- `7` > `4`, no swap, `i` remains `-1`.
- `1` < `4`, swap `1` with `5`, `i` becomes `0`.
- and so on.
- After all comparisons `i` becomes `2`.



To visualize this process, change the colour of the current element to `processing_element_color (i.e. red)`.

If a swap occurs, play a sound effect and update the position of the sticks on the screen, followed by a short delay for better visualization.



![ ](/Full-Stack-Game-Development/images/9599d9f1aa55d4c8.gif)

*Swapping based on Pivot*


After processing all elements, swap the pivot element with the element at `i + 1` to place the pivot in its correct sorted position. Then, update the stick positions accordingly.

i.e. After the loop, swap the pivot `4` with `7` (element at `i+1`).



![ ](/Full-Stack-Game-Development/images/1bec26965fecad86.gif)

*Pivot on Correct Position*


The array is now partitioned as `[1, 3, 2, 4, 9, 5, 8, 6, 7]`.



At the end, you return the pivot index `i + 1` for partitioning. ( i.e return `3` )



![ ](/Full-Stack-Game-Development/images/ed2f58494cfde92b.gif)

***Partitioning***



> ✅**TODO for StickCollectionController:**

> 1. Create and implement a private method `void partition(int left, int right)` to handle the logic for partitioning the array.



**Click here to check **`partition()````cpp
int StickCollectionController::partition(int left, int right)
{
	//set pivot blue
	sticks[right]->stick_view->setFillColor(collection_model->selected_element_color);
	int i = left - 1;
	SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();

	for (int j = left; j < right; ++j)
	{

		sticks[j]->stick_view->setFillColor(collection_model->processing_element_color);
		number_of_array_access += 2;
		number_of_comparisons++;

		if (sticks[j]->data < sticks[right]->data)
		{
			++i;
			std::swap(sticks[i], sticks[j]);
			number_of_array_access += 3;
			sound->playSound(SoundType::COMPARE_SFX);


			updateStickPosition();
			std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));
		}

		// Reset the color of the processed element if it's not swapped
		sticks[j]->stick_view->setFillColor(collection_model->element_color);
	}

	std::swap(sticks[i + 1], sticks[right]);
	number_of_array_access += 3;

	updateStickPosition();
	return i + 1;
}

```



## QuickSort - Recursive Sorting



The `quickSort` function is where the recursive division and conquering happens. 

It takes `left` and `right` as parameters to sort the segment of the array between these indices.



Call the `partition` function to get the pivot index, then recursively call `quickSort` on the left and right sub-arrays.



After the initial partitioning with pivot `4`, our array looks like this: `[1, 3, 2, 4, 9, 7, 8, 5, 6]`.

The pivot index is `3`, meaning `4` is now in its correct position.

Now that you have two sub-arrays to sort:

1. Left sub-array: `[1, 3, 2]`
2. Right sub-array: `[9, 7, 8, 5, 6]`



Similarly, it will recursively sort the left and right sub-arrays by repeating the partitioning process until the entire array is sorted.



After sorting the segment, set the colour of all elements in this segment to `placement_position_element_color` to indicate they are sorted. Then, update the stick positions accordingly. 



![ ](/Full-Stack-Game-Development/images/8823654b909ad639.gif)

***Recursive Division***



> ✅**TODO: StickCollectionController**
> 
> 1. Create and implement a private method `void quickSort(int left, int right)` and make the initial call from `processQuickSort()`



Click here **to check **`quickSort()````cpp
void StickCollectionController::quickSort(int left, int right)
{
	if (left < right)
	{
		int pivot_index = partition(left, right);

		quickSort(left, pivot_index - 1);
		quickSort(pivot_index + 1, right);

		// Set all elements in this segment to green after sorting is done
		for (int i = left; i <= right; i++) {
			sticks[i]->stick_view->setFillColor(collection_model->placement_position_element_color);
			updateStickPosition();
		}
	}
}
```



## DRAMATIC END EFFECT


---

Lastly, add `setCompletedColor()` to your `processQuickSort()` to create a dramatic visual effect at the end.



> ✅**TODO: StickCollectionController**
> 
> 1. Call `setCompletedColor()` at the end of `processQuickSort()`



This is how it should look like:


<iframe src="https://www.loom.com/embed/cfc5aeefa1e3417884b8ad4e2b35db60" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Quick Sort***



Now, your final task to complete!



> ✅**TODO: StickCollectionController**
> 
> 1. Add `time_complexity = "O(n Log n)"` inside the `QUICK_SORT` case of `sortElements()`.



The time complexity might be similar to Merge Sort, but there's more to explore.

**See you in the next lesson👋🏼**
