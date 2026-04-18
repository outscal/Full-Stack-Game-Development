Did you try creating the sort? 

No worries if not. You will go through the process step by step in this lesson!



> ✅**TODO: **
> 
> 1. Uncomment the button bindings for Radix Sort in `MainMenuUIController`
> 2. Create an empty private method `void processRadixSort()` in `StickCollectionController`
> 3. Create a case for `RADIX_SORT` and call the `processRadixSort` inside the `sortElements()` method in `StickCollectionController`.



Let's quickly recap how Radix Sort works using Count Sort:

- Find the maximum element in the array to determine the number of digits in the largest number.
- Iterate through each digit place (from the least significant to the most significant digit).
- Use Counting Sort for each digit place:
- - Count the occurrences of each digit in the current digit place.
  - Modify the count array to position the elements correctly based on the digit.
  - Place the elements in the sorted order based on the current digit place.
- Repeat the sorting process for each digit place until reaching the most significant digit.
- After sorting all digit places, the array will be sorted in ascending order.



Now, let's integrate the Radix Sort logic with the sticks in your program.



## **IMPLEMENT Radix SORT**


---


Let's create the methods needed to implement sort, this will include count sort as well.



> ✅**TODO: StickCollectionController**
> 
> 1. Declare an empty private method `void radixSort()` and call it from `processRadixSort()`



Radix Sort relies on Counting Sort as a crucial step in sorting elements based on their digit places.

So, first, create and implement a method for count sort. 



But as you know, radix sort is a non-comparison algorithm.

So, the usual `updateStickPosition()` method is not suitable for it, since it was designed for situations where multiple sticks' positions change. 



However, in Radix Sort, only one stick's position changes, so there's no need to iterate through all the sticks. Instead, you can simply update the position of that one stick, passing its index as a parameter.



> ✅**TODO: StickCollectionController**
> 
> 1. Declare and implement a private method `void updateStickPosition(int i)`



**Click here to check **`updateStickPosition()````cpp
void StickCollectionController::updateStickPosition(int i)
{
	float x_position = (i * sticks[i]->stick_view->getSize().x) + ((i)*collection_model->elements_spacing);
	float y_position = collection_model->element_y_position - sticks[i]->stick_view->getSize().y;

	sticks[i]->stick_view->setPosition(sf::Vector2f(x_position, y_position));
}
```



Now, implement the count sort.



## implement count sort


---

This method will update the positions of the sticks and take care of the visualization of the sticks.

It takes an integer parameter `exponent`, which plays a major role in determining the digit position used for sorting the sticks.



The `exponent` parameter is typically set based on maximum number of digits in the stick `based on`, such as the number of digits in the largest stick value.



Let's break down the steps to implement count sort with an example.

Specifically focusing on digit-based sorting for a radix sort.



Consider you have the sticks (each represented by a number):

`sticks = [75, 90, 24, 9, 15]`



1. First, initialize a pointer to a `SoundService` object to play sound effects when processing each element.
2. Create two vectors, `output` to store the sorted sticks and `count` to keep track of the count of digits (0-9).



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_28_2024__07_17_26.png)

`***output***`* & *`***count***`* array*



1. Iterate through each stick, 
2. - Calculate the digit of the stick's data based on the current exponent. 
    For example, if the exponent is `**1**`, the unit place of `75` will be `(75 / 1) % 10`, which gives us `5`.
    (`**Mod(%) 10**` is used to extract the digit in the unit place.)
  - Increment the count of that digit in the `count` vector. 
    For instance, if `count[5]` is initially `0`, after processing `75`, it becomes `1`.
  - Play a sound and update visuals for each element processed.
    Use `processing_element_color` to change the colour of the processing sticks.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_28_2024__07_37_47.gif)

`***count***`* array*



Count vector after counting digits: `count = [1, 0, 0, 0, 1, 2, 0, 0, 0, 1]`



- Then, accumulate the counts in the `count` vector to determine the positions for sorted output.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_28_2024__07_49_59.png)

`**count**` array accumulation



- Update the `output` vector based on the current `exponent` and decrement the count for each digit. 
  Update the colour of the sticks in `output` to `temporary_processing_color`.

For example, if the `exponent` is `1` and you're processing the number `66`, its unit digit is `6`.

As a result, 66 will be placed in `output[count[6] - 1]`, which is `output[7]`, because `count[6]` is `8` before decrementing.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_28_2024__08_49_27.gif)

`**output**` array



Output vector after sorting unit place: `output = [90, 24, 75, 15, 9]`



- Finally, place the sorted elements back into the `sticks` vector and update visualizations for the final sorted order.
  Use `processing_element_color` to change the colour of the processing sticks.
  Update the positions of the stick using the special function made for radix sort.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_28_2024__08_55_15.png)



Final array`sticks = [90, 24, 75, 15, 9]`



> ✅**TODO: StickCollectionController**
> 
> 1. Create and implement an private method `void countSort(int exponent)`





**Click here to check **`countSort()````cpp
void StickCollectionController::countSort(int exponent)
{
	SoundService* sound = Global::ServiceLocator::getInstance()->getSoundService();
	std::vector<Stick*> output(sticks.size());
	std::vector<int> count(10, 0);

	// Process each element to count digits
	for (int i = 0; i < sticks.size(); ++i) {
		sound->playSound(SoundType::COMPARE_SFX);
		int digit = (sticks[i]->data / exponent) % 10;
		count[digit]++;
		number_of_array_access++;
		sticks[i]->stick_view->setFillColor(collection_model->processing_element_color);
		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay / 2)); // Delay for visual processing
		sticks[i]->stick_view->setFillColor(collection_model->element_color);  // Reset color after processing
	}

	// Accumulate the count array
	for (int i = 1; i < 10; ++i) {
		count[i] += count[i - 1];
	}

	// Sorting based on the current digit
	for (int i = sticks.size() - 1; i >= 0; --i) {

		int digit = (sticks[i]->data / exponent) % 10;
		output[count[digit] - 1] = sticks[i];
		output[count[digit] - 1]->stick_view->setFillColor(collection_model->temporary_processing_color);
		count[digit]--;
		number_of_array_access++;
		
			}

	// Place elements back into the main array
	for (int i = 0; i < sticks.size(); ++i) {
		sticks[i] = output[i];
		sticks[i]->stick_view->setFillColor(collection_model->placement_position_element_color);  // Final sorted color for this digit
		updateStickPosition(i);
		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay)); // Delay to observe final sorting state
	}
}
```



Done with Count Sort?

Let's integrate it with Radix Sort.



## **IMPLEMENT Radix SORT** 2.0


---

You have your count sort method that will be called to sort sticks based on the current digit place.

First, you need to iterate through the `sticks` vector to find the maximum data value among all sticks.



For example, `sticks = [170, 45, 75, 90, 802, 24, 2, 66]`

In this case, the maximum element is `802`.



Store that data because it will determine the number of significant digits to sort through.

Next, you'll iterate over each digit place:

1. Start with `exponent = 1`.
2. Continue while `maxElement / exponent > 0`.
3. Multiply `exponent` by 10 for each iteration.



Here, `802` has 3 digits, so you will have 3 passes:

- for unit place (`exponent = 1`), 
- then the tens place (`exponent = 10`), and 
- finally, the hundreds place (`exponent = 100`)).

,

For each `exponent`, call `countSort(exponent)` to sort the sticks based on the current digit place.



> ✅**TODO: StickCollectionController**
> 
> 1. Implement `void radixSort()`.



**Click here to check **`radixSort()````cpp
void StickCollectionController::radixSort()
{
	int maxElement = INT_MIN;
	const int size = sticks.size();

	for (int i = 0; i < size; ++i) maxElement = std::max(sticks[i]->data, maxElement);
	for (int exponent = 1; maxElement / exponent > 0; exponent *= 10) countSort(exponent);
}

```



Now you can add `setCompletedColor()` to your `processRadixSort()` to make the dramatic visual effect at the end.



> ✅**TODO: StickCollectionController**
> 
> 1. Call `setCompletedColor()` at the end of `processRadixSort()`



This is how it should look like:


<iframe src="https://www.loom.com/embed/b51a3f77a13745f485fd354126b2b10d" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>




Now, your final task to complete!



> ✅**TODO: StickCollectionController**
> 
> 1. Add `time_complexity = "O(w*(n+k))"` inside the `RADIX_SORT` case of `sortElements()`.



What exactly is "`O(w*(n+k))`" will be discussed in the next section.

**See you in the next lesson👋🏼**
