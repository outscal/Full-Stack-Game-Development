Did you try creating the sort? 

No worries if not. You will go through the process step by step in this lesson!



> ✅**TODO: **
> 
> 1. Uncomment the button bindings for Insertion Sort in `MainMenuUIController`
> 2. Create an empty private method `void processInsertionSort()` in `StickCollectionController`
> 3. Create a case for `INSERTION_SORT` and call the `processInsertionSort` inside the `sortElements()` method in `StickCollectionController`.



Let's do a quick recap of the steps for insertion sort before seeing the implementation:

1. Begin sorting from the second element, as the first element is already considered sorted.
2. Pick and Insert Elements:

- - Choose an element from the unsorted part.
  - Compare it with elements in the sorted part, starting from the right.
  - Shift elements to the right to make space for the key element.
  - Insert the key into its correct position in the sorted part.

1. Continue this process for each element in the unsorted part until the entire array is sorted.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/a56a342c547c9dbe.gif)

***Insertion Sort***



Now, let's integrate the Insertion Sort logic with the sticks in your program.



## **IMPLEMENT Insertion SORT**


---

Key points you should follow during the implementation:

- Keep track of array accesses and comparisons by updating relevant texts in the UI.
- Highlight key moments of the sort by changing the colours of elements during different stages of the algorithm.
- Use thread sleep operations to slow down the sort for better visualization.
- Make sure to update the positions of the sticks in the UI as the sorting progresses.
- Add sound effects to enhance the visualization experience when operations happen.
- Check the `sort_state` , if sorting is stoped or completed.



Let's break down the steps to implement Insertion Sort with an example.

Consider you have a collection of sticks : `sticks = [170, 45, 75, 90]`



1. Start with initializing a pointer to the `SoundService` object to play `COMPARE_SFX` sound effects when processing each element.
2. You will iterate through the stick collection, starting from the second element `(i = 1)`.
3. `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
4. For each iteration, consider the current element (`sticks[i]`) as the `key`.

- - `Stick* key = sticks[i]`
  - Set the colour of the `key` stick to `processing_element_color i.e red` to indicate it's the processing element. 
  - Add a delay for visualization.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/b1154f25bae37e5a.png)

`stick` array



1. Initialize a variable `j` to track the position in the sorted subset (starting from `i - 1`).
2. - `int j = i - 1`
3. Compare the `key` with each element in the sorted subset in reverse order.
4. - Increment the array access and comparison counters.
  - If the current element (`sticks[j]`) is greater than the `key`, shift the current element to the right to make room for the `key`.
  - `sticks[j + 1] = sticks[j]`
  - Increment the array access and comparison counters.
  - Set the colour of `sticks[j + 1]` to `processing_element_color` and plays a sound.
  - Update the stick positions and pause for visuals.



1. Place the `key` in its correct position.
2. - Set the colour of the stick to `temporary_processing_color i.e. yellow` indicating it's sorted and plays a sound.
  - Update the stick positions and pause for visuals.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/f67ffdcbef6e5399.gif)





> ✅**TODO: StickCollectionController**
> 
> 1. Implement `void processInsertionSort()`



**Click here to check **`processInsertionSort()````cpp
void StickCollectionController::processInsertionSort()
{
	SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();

	for (int i = 1; i < sticks.size(); ++i)
	{

		if (sort_state == SortState::NOT_SORTING) { break; }

		int j = i - 1;
		Stick* key = sticks[i];
		number_of_array_access++; // Access for key stick


		key->stick_view->setFillColor(collection_model->processing_element_color); // Current key is red

		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));

		while (j >= 0 && sticks[j]->data > key->data)
		{

			if (sort_state == SortState::NOT_SORTING) { break; }

			number_of_comparisons++;
			number_of_array_access++;

			sticks[j + 1] = sticks[j];
			number_of_array_access++; // Access for assigning sticks[j] to sticks[j + 1]
			sticks[j + 1]->stick_view->setFillColor(collection_model->processing_element_color); // Mark as being compared
			j--;
			sound->playSound(SoundType::COMPARE_SFX);
			updateStickPosition(); // Visual update

			std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));

			sticks[j + 2]->stick_view->setFillColor(collection_model->selected_element_color); // Mark as being compared

		}

		sticks[j + 1] = key;
		number_of_array_access++;
		sticks[j + 1]->stick_view->setFillColor(collection_model->temporary_processing_color); // Placed key is green indicating it's sorted
		sound->playSound(SoundType::COMPARE_SFX);
		updateStickPosition(); // Final visual update for this iteration
		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));
		sticks[j + 1]->stick_view->setFillColor(collection_model->selected_element_color); // Placed key is green indicating it's sorted
	}

}

```



## DRAMATIC END EFFECT


---

Lastly, add `setCompletedColor()` to your `processInsertionSort()` to create a dramatic visual effect at the end.



> ✅**TODO: StickCollectionController**
> 
> 1. Call `setCompletedColor()` at the end of `processInsertionSort()`



This is how it should look like:


<iframe src="https://www.loom.com/embed/9ebd20625c8146f09ba312743de19801" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



***Insertion Sort***


Now, your final task to complete!



> ✅**TODO: StickCollectionController**
> 
> 1. Add `time_complexity = "O(n^2)"` inside the `INSERTION_SORT` case of `sortElements()`.



**See you in the next lesson👋🏼**
