Did you try to implement Bubble Sort yourself?

No worries if you did not. Let’s properly implement it in this lesson!



This time, all the setup for the `GameplayService` and `StickCollection` is already set up, so you don't need to worry about that.

You just have to implement Bubble Sort. 

Ready? Let's go! 



> ✅**TODO: **
> 
> 1. Uncomment the button bindings for Bubble Sort in `MainMenuUIController`
> 2. Create an empty private method `void processBubbleSort()` in `StickCollectionController`
> 3. Uncomment the switch-case for the `processBubbleSort` inside the `sortElements()` method in `StickCollectionController`



Do you remember the pseudocode for Bubble Sort?

Let's quickly recap it:

- **Initialize: **Get the number of elements in the array and store it in `n`.
- **Repeat: **The outer loop runs until the array is sorted. 
- - Initialize a variable `swapped` to `false`
  - Inside the inner loop:
  - - Iterate through the array from the first to the second-to-last unsorted element.
    - Swap elements if the current element is greater than the next and set `swapped` to `true`.
  - Reduce `n` by 1 after each pass.
- **End:** Stop when no swaps are made in a pass (`until not swapped`).



## Implement Bubble Sort


---

Alright, it's time to start implementing Bubble Sort! 

But first, let's talk about a few important things to make the visualizer experience better:



1. **Updating texts for array access and comparison**: Remember when you created a search visualizer? You'll do something similar here. It's not too hard!

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_14_2024__09_43_07.gif)





1. **Playing sounds during operations**: You've done this before, too. Here, you'll play sound:

- - `**COMPARE_SFX**`: When comparing two sticks.
  - You can find the sound in `**SoundService**` and the file path in `**Config**`.



1. **Changing stick colours to highlight key moments**: 

- - **Red**: Comparisons between two sticks.
  - **Green**: When you get the sorted sticks (largest sticks at the end).

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_14_2024__09_48_46.jpg)





## Update Stick Positions


---



This is new! You'll need to update the stick positions whenever the sticks need to change position. ( No Shit 💡)

To update the stick positions, you already have a function called `**updateStickPosition()**`.



It iterates through each stick in the collection, calculates its new x and y positions based on its index, size, and spacing, and then sets its position accordingly. 



Watch this video carefully.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_14_2024__10_04_29.gif)

***Swap Operation***



Notice how the red sticks initially have the shorter one on the right and the taller one on the left?

According to the comparison condition, they get swapped, placing the taller one on the right and the shorter one on the left.



This is exactly what happens in the `**updateStickPosition()**` function: it updates the sticks' positions after a swap, ensuring that they are always in the correct order and position.





## **Checking the Sort State**


---

The sorting process can be stopped or completed either due to user action (such as clicking the `**MENU**` button) or by reaching the end of the sort.

When the process ends, If you don't check the sort state, your program may crash or freeze, causing a poor user experience.

This is because the sorting thread will continue running unnecessarily to complete the sorting process.



To handle this, create an `enum class` called `SortState` which will have two states:

- `**NOT_SORTING**`: The sorting process is not active, and the sticks are not being sorted.
- `**SORTING**`: The sorting process is active, and the sticks are being sorted.

These states allow you to control and monitor the sorting process.



**enum class **`**SortState**`**:**

```cpp
enum class SortState
{
    SORTING,
    NOT_SORTING,
};
```



> ✅**TODO: **
> 
> 1. Add `enum class SortState` in `StickCollectionModel`
> 2. Add a property `SortState sort_state` in `StickCollectionController`



To use these states, you need a property called `**sort_state**` of type `SortState` in `StickCollectionController`.

You have to:

- Set the `sort_state` to `SORTING` whenever the sorting process starts.
- Set the `sort_state` to `NOT_SORTING` when the sorting process is completed or stopped. 
- Check the `sort_state` during sort process, if the `sort_state` is `NOT_SORTING` then use `**break**`** ** to abort the loop/process.



Remember to initialize the variable as `NOT_SORTING`



> ✅**TODO: StickCollectionController**
> 
> 1. Set `sort_state = SortState::SORTING` in `sortElements()`.
> 2. Set `sort_state = SortState::NOT_SORTING` in `initialize()`, `processSortThreadState()` & `reset()`.




Click here to check `StickCollectionController`.

```cpp
// Some Code

void StickCollectionController::initialize()
{
	sort_state = SortState::NOT_SORTING;
	collection_view->initialize(this);
	initializeSticks();
	reset();
}

// Some Code 

void StickCollectionController::processSortThreadState()
{
	if (sort_thread.joinable() && isCollectionSorted()) {

		sort_thread.join();
		sort_state = SortState::NOT_SORTING;

	}
}

//Some Code

void StickCollectionController::reset()
{
	color_delay = 0;
	current_operation_delay = 0;

	sort_state = SortState::NOT_SORTING;
	
  //Some Code
}

//Some Code 

void StickCollectionController::sortElements(SortType sort_type)
{
	current_operation_delay = collection_model->operation_delay;
	this->sort_type = sort_type;
	sort_state = SortState::SORTING;

	switch (sort_type)
	{
	case Gameplay::Collection::SortType::BUBBLE_SORT:
		sort_thread = std::thread(&StickCollectionController::processBubbleSort, this);
		break;
	}
}

//Some Code
```





If you do not keep these points in mind then your process might freeze when the user tries to exit the sort in between.



## Implement Bubble Sort 2.0


---

Let's break down the steps to implement Bubble Sort:

1. Start with initializing a pointer to the `SoundService` object to play `COMPARE_SFX` sound effects when processing each element.
2. **Outer Loop**: Loop through the entire collection of `sticks`.
3. `break` the loop if `sort_state` is `SortState::NOT_SORTING`.
4. Initialize `swapped` to `false` to track if any swaps are made during a pass.
5. **Inner Loop**: Loop through the sticks from the first element to the last unsorted element.
6. - Break the inner loop if `sort_state` is `SortState::NOT_SORTING`.
  - Increment the array access and comparison counters.
  - Set the colour of the two elements being compared to `processing_element_color`.
  - **Compare and Swap**: If `sticks[i - 1]` data is greater than `sticks[i]` data:
  - - Swap the two elements using the inbuilt `swap()` function.
    - Set `swapped` to `true`.
  - Pause the execution for `current_operation_delay` using thread sleep.
  - Revert the colour of the two sticks back to the default `element_color`
  - Call `updateStickPosition()` method to update the positions of the sticks.



1. Set the colour of the last sorted element to `placement_position_element_color`.
2. If no swaps were made during a pass, the array is already sorted, `break` out of the loop.



> ✅**TODO: StickCollectionController**
> 
> 1. Implement `processBubbleSort()` method.



Click here to check `**processBubbleSort()**````cpp
void StickCollectionController::processBubbleSort() {
  SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();

  for (int j = 0; j < sticks.size(); j++) {   // Loop through the sticks array
    if (sort_state == SortState::NOT_SORTING) { break; }   // Check if sorting has stopped or been interrupted

    bool swapped = false;  // To track if a swap was made

    for (int i = 1; i < sticks.size() - j; i++) {    // Loop through the array, reducing the range each pass
      if (sort_state == SortState::NOT_SORTING) { break; }      // Check if sorting has stopped or been interrupted

      // Increment the number of array accesses and comparisons
      number_of_array_access += 2;
      number_of_comparisons++;

      sound->playSound(SoundType::COMPARE_SFX);      // Play the compare sound effect

      // Set the current sticks to the processing color
      sticks[i - 1]->stick_view->setFillColor(collection_model->processing_element_color);
      sticks[i]->stick_view->setFillColor(collection_model->processing_element_color);

      if (sticks[i - 1]->data > sticks[i]->data) {      // Check if the current stick is greater than the next stick
        // Swap the sticks if necessary
        std::swap(sticks[i - 1], sticks[i]);
        swapped = true;  // Set swapped to true if there was a swap
      }

      std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));

      // Reset the stick colors
      sticks[i - 1]->stick_view->setFillColor(collection_model->element_color);
      sticks[i]->stick_view->setFillColor(collection_model->element_color);

      updateStickPosition();
    }

    if (sticks.size() - j - 1 >= 0) {    // Set the last sorted stick to the placement position color
      sticks[sticks.size() - j - 1]->stick_view->setFillColor(collection_model->placement_position_element_color);
    }

    if (!swapped) { break; }    // If no swaps were made, the array is already sorted
  }
}

```



Now, run the code and see it in action!

It works!

But hey, it seems a bit boring, right?

Let's add something small at the end for a dramatic effect.



## dramatic effect 🫠


---

To do this, you need to create a method `setCompletedColor()`. But what will it do?

This function is designed to add a dramatic visual effect at the end of every algorithm by changing the colour of the sticks from `element_color` to `placement_position_element_color` with a delay and playing a sound of your choice (we chose `SCREAM`) at the end.



Here's the code snippet for `**setCompletedColor()**`**:**

```cpp
void StickCollectionController::setCompletedColor(){
  	for (int k = 0; k < sticks.size(); k++){
    		if (sort_state == SortState::NOT_SORTING) { break; } // Check if sorting is stoped or completed
    		sticks[k]->stick_view->setFillColor(collection_model->element_color);
  	}
  	SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();
  	for (int i = 0; i < sticks.size(); ++i){
    		if (sort_state == SortState::NOT_SORTING) { break; }  // Check if sorting is stoped or completed
    		sound->playSound(SoundType::COMPARE_SFX);
    		sticks[i]->stick_view->setFillColor(collection_model->placement_position_element_color);
    		std::this_thread::sleep_for(std::chrono::milliseconds(color_delay));
  	}
  	// Play scream sound if sorting is still in progress
  	if (sort_state == SortState::SORTING){
    		sound->playSound(SoundType::SCREAM);
  	}
}
```



But before implementing it, what is `color_delay`?

`**color_delay**` is just the delay used to visualize the final colour change, like the `**current_operation_delay**`, which is used to visualize the operations.

So first initialize it.



> ✅** TODO: **`**color_delay**`
> 
> 1. Add a property `const long initial_color_delay = 40` in `StickCollectionModel`
> 2. Add a property `int color_delay` in `StickCollectionController`
> 3. Inititalize `color_delay` in `sortElements()`
> 4. Set `color_delay=0` in `reset()`



Now you can implement `setCompletedColor()`.



> ✅**TODO: StickCollectionController**
> 
> 1. Implement `setCompletedColor()` method as above
> 2. Call it at the end of `processBubbleSort()`



This is how it should look like:


[Watch video](https://www.loom.com/embed/27d2b629ebf241d39366c7ed37c129ee)



***Bubble Sort in Action***



Notice the empty space in front of Time Complexity? 

That's your final task to complete!



> ✅**TODO: StickCollectionController**
> 
> 1. Add `time_complexity = "O(n^2)"` inside the `BUBBLE_SORT` case of `setCompletedColor()`.



Click here to check `sortElements()````cpp
void StickCollectionController::sortElements(SortType sort_type)
{
	current_operation_delay = collection_model->operation_delay;
	color_delay = collection_model->initial_color_delay;
	this->sort_type = sort_type;
	sort_state = SortState::SORTING;

	switch (sort_type)
	{
	case Gameplay::Collection::SortType::BUBBLE_SORT:
		time_complexity = "O(n^2)";
		sort_thread = std::thread(&StickCollectionController::processBubbleSort, this);
		break;
	}
}
```



Why `O(n^2)` will be discussed in the next lesson.

**See you in the next lesson👋🏼**
