Did you try creating the sort? 

No worries if not. You will go through the process step by step in this lesson!



> ✅**TODO: **
> 
> 1. Uncomment the button bindings for Selection Sort in `MainMenuUIController`
> 2. Create an empty private method `void processSelectionSort()` in `StickCollectionController`
> 3. Create a case for `SELECTION_SORT` and call the `processSelectionSort` inside the `sortElements()` method in `StickCollectionController`.



Let's do a quick recap of the steps for selection before seeing the implementation:

1. Set the smallest number to be the first element in the list.
2. Look through the entire list and find the actual smallest number.
3. Swap that value with the item at the index of the smallest number.
4. Move on to look at the next unsorted item in the list, repeat steps 2 + 3.
5. Continue to do this until we arrive at the last element in the list.



![ ](/Full-Stack-Game-Development/images/62b454291793e4e8.gif)

***Selection Sort***



Now, let's integrate the Selection Sort logic with the sticks in your program.



## **IMPLEMENT INSERTION SORT**


---

Key points you should follow during the implementation:

- Keep track of array accesses and comparisons by updating relevant texts in the UI.
- Highlight key moments of the sort by changing the colours of elements during different stages of the algorithm.
- Use thread sleep operations to slow down the sort for better visualization.
- Make sure to update the positions of the sticks in the UI as the sorting progresses.
- Add sound effects to enhance the visualization experience when operations happen.
- Check the `sort_state` , if sorting is stopped or completed.



Let's break down the steps to implement Selection Sort with an example.

Consider you have a collection of sticks : `sticks = [170, 45, 75, 90]`



1. Start with initializing a pointer to the `SoundService` object to play `COMPARE_SFX` sound effects when processing each element.
2. **Outer Loop for Selection Sort**: Iterate through the array `sticks` from the first element to the second last element. 
3. `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
4. For each iteration, consider the current element as the smallest and its index as the `**min_index**`.

- - Set the colour of the current index `i` stick to `selected_element_color i.e. blue` to indicate it's current smallest.
  - Add a delay for visualization.



![ ](/Full-Stack-Game-Development/images/febe16335394a579.png)

`stick` array



1. **Inner Loop to Find the Minimum Element**: Iterate through the elements from `i+1` to the end of the array.
2. - `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
  - Set the colour of the current element to `processing_element_color i.e. red` and plays a sound.
  - Add a delay for visualization.
3. **Compare and Update Minimum Index**:
4. - If the current element is less than the `**min_index**` stick, update the `**min_index**`:
  - - Set the previous `**min_index**` stick colour to `element_color`
    - Update `min_index` to the current index `j`.
    - Set the colour of `**min_index**` stick to `temporary_processing_color i.e. yellow`.
  - Else, the current element is not the minimum; reset its colour to `element_color i.e. white`.



![ ](/Full-Stack-Game-Development/images/ff1b96fca54621ee.gif)

*Find the Minimum Element*


1. **Swap the Elements**:
2. - After finding the minimum element (`min_index`) in the unsorted part of the array, swap it with the first element of the unsorted part (element at index `i`).
  - Set the colour of the stick to `placement_position_element_color i.e. green` indicating it's sorted
  - Update the stick positions and pause for visuals.



![ ](/Full-Stack-Game-Development/images/d16718fe5fec0cc9.gif)

*Swap Elements*



1. Ensure the last element is also marked as sorted by setting its colour to `placement_position_element_color`.



> ✅**TODO: StickCollectionController**
> 
> 1. Implement `void processSelectionSort()`



**Click here to check **`processSelectionSort()````cpp
void StickCollectionController::processSelectionSort()
{
	
			SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();

		for (int i = 0; i < sticks.size() - 1; ++i)
		{

			if (sort_state == SortState::NOT_SORTING) { break; }

			int min_index = i;
			sticks[i]->stick_view->setFillColor(collection_model->selected_element_color);  // Mark the start of processing

			for (int j = i + 1; j < sticks.size(); ++j)
			{

				if (sort_state == SortState::NOT_SORTING) { break; }

				number_of_array_access += 2;
				number_of_comparisons++;

				sound->playSound(SoundType::COMPARE_SFX);
				sticks[j]->stick_view->setFillColor(collection_model->processing_element_color);
				std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));

				if (sticks[j]->data < sticks[min_index]->data)
				{
					if (min_index != i) sticks[min_index]->stick_view->setFillColor(collection_model->element_color);  // Reset previous min
					min_index = j;
					sticks[min_index]->stick_view->setFillColor(collection_model->temporary_processing_color);  // New min found
				}
				else
				{
					sticks[j]->stick_view->setFillColor(collection_model->element_color);  // Not the minimum, reset color
				}
			}

			number_of_array_access += 3;
			std::swap(sticks[min_index], sticks[i]);  // Place the found minimum at its final position

			sticks[i]->stick_view->setFillColor(collection_model->placement_position_element_color);  // Mark as sorted
			updateStickPosition();
		}

		// Ensure the last stick is also marked as sorted
		sticks[sticks.size() - 1]->stick_view->setFillColor(collection_model->placement_position_element_color);
	
	}

```



## DRAMATIC END EFFECT


---

Lastly, add `setCompletedColor()` to your `processSelectionSort()` to create a dramatic visual effect at the end.



> ✅**TODO: StickCollectionController**
> 
> 1. Call `setCompletedColor()` at the end of `processSelectionSort()`



This is how it should look like:


<iframe src="https://www.loom.com/embed/72bbb180ec274311824a5509081a71aa" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Selection Sort***


Now, your final task to complete!



> ✅**TODO: StickCollectionController**
> 
> 1. Add `time_complexity = "O(n^2)"` inside the `SELECTION_SORT` case of `sortElements()`.



**See you in the next lesson👋🏼**
