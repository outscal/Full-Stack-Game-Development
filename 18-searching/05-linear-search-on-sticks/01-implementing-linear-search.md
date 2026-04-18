Are you ready to visualize Linear Search?

That's exactly what you are going to do in this chapter!



Let's take a quick look at the pseudocode before you start implementing it.

Pseudocode```cpp
// Function to perform linear search on an array
function linear_search(array, target)
  for i = 0 to array.length - 1
    if array[i] == target
      return i			// return the index of element, if found
  return -1			// return -1, if not found

```



As you already know,** linear search** is a simple algorithm for finding a target value within a list or an array. 

It checks each element in the list sequentially until a match is found or the list ends.



How do you think the search algorithm takes place on sticks?



In the context of our stick visualizer, the linear search algorithm will iterate through each stick in the collection, comparing the stick’s value to the target value. 

- If a match is found, the search is successful, and the stick is highlighted.
- If no match is found by the end of the list, the search concludes without finding the target.



Currently, the sticks are placed in increasing order, making it very easy to identify and target something that is already in order.

But can Linear Search find the target stick from a shuffled or unordered collection?



The answer is yes! Linear Search does not rely on the order of elements.

It will check each stick one by one until it finds the target, regardless of the order.



The main reason linear search is important is because it can be used on any kind of data, no matter what type it is. This makes it a very flexible and powerful algorithm for searching.



To visualize this, lets first shuffle the sticks in any random order and then verify its working. 



## Shuffling the sticks


---



`**shuffleSticks():**` As discussed, it's important to ensure that the sticks are properly shuffled before implementing linear search.



Before directly implementing it, you need to seed the function so that you get the correct random values, not in any order.

And for that you need to create a method `initializeRandomSeed()`  in `**GameplayService**`



Here's the code snippet:

```cpp
void GameplayService::initializeRandomSeed() // Helper function for initializing the random seed
{
    // Seed the random number generator with the current time
    // This ensures that the sequence of random numbers will be different each time the program is run
    // The `std::time(nullptr)` function returns the current time as the number of seconds since the Unix epoch (January 1, 1970)
    // The `static_cast<unsigned int>` is used to cast the `std::time_t` value to an `unsigned int`, which is required by `std::srand`
    std::srand(static_cast<unsigned int>(std::time(nullptr)));
}

```



> ✅**TODO: **`**GameplayService**`

> 

> 1. Create and implement a private method `void initializeRandomSeed()`
> 2. Call  `initializeRandomSeed` during `initialize()`



So, let’s implement `**shuffleSticks()**` before you move to the search algorithm.



The code snippet for the shuffle function in the `StickCollectionController.cpp` is given below:-

```cpp
// . . some code

void Gameplay::Collection::StickCollectionContoller::shuffleSticks()
{
	// declare a variable 'device' of type std::random_device
	// 'std::random_device is a random number generator that produces non-deterministic random numbers.
	std::random_device device;
	std::mt19937 random_engine(device());

	// shuffle the elements in the sticks collection using the random engine
	std::shuffle(sticks.begin(), sticks.end(), random_engine);
}

// . . some code
```



> ✅**TODO:**

> 

> 1. Declare the `void shuffleSticks()` function as private in `StickCollectionController.h`.

> 2. Implement the method in the source file based on the discussion above.

> 3. Call the `shuffleSticks()` function within the `reset` function in the source file to ensure that the sticks are re-initialized when the project resets.



Done that? Great!



You still need a method that will help you randomly pick one stick and highlight it making it as **target stick** for your algorithm.

For that you will create `**resetSearchStick()**`**:**



The code snippet for `resetSearchStick()`:

```cpp
void Gameplay::Collection::StickCollectionContoller::resetSearchStick()
{
	stick_to_search = sticks[std::rand() % sticks.size()];
	stick_to_search->stick_view->setFillColor(collection_model->search_element_color);
}
```



> ✅**TODO:** **StickCollectionController**

> 

> 1. Add `Stick* stick_to_search` property as private. 
> 2. Declare and implement a private function `void resetSearchStick()` and call it in `reset()`



Now you can have everything for your Linear Search algorithm.

You can move onto it.



## Linear search on sticks


---

`**processLinearSearch():**` Let's briefly discuss what this function will do:-

- Iterate through the collection of sticks, set the color of stick to `processing_element_color` indicating it is getting processed in that operation and just after it reset the color to `element_color`.
- Check if the current stick is the target stick
- If the target stick is found, change current stick's color to `found_element_color` (green), reset `stick_to_search` to `nullptr` and then `return`.



> ✅**TODO**: **StickCollectionContoller**

> 

> 1. Declare and implement `void processLinearSearch()` function as private in `StickCollectionController.h`.
> 2. Create a switch-case inside `searchElement()` based on `search_type` parameter, 
>        update `search_type` of `StickCollectionContoller` , 
>        when there if a case of `LINEAR_SEARCH` call `processLinearSearch()`



Want the project to be more fun?

Let's add a sound that plays while the search is running!



If you check your config file, you'll see that you already have a sound that you can use for each stick comparison.

All you need to do is: set it up in the `SoundService` and play it inside your `linearSearch()` method!



> ✅**TODO:** **In **`**SoundService.h**`

> 

> 1. Define a sound type for comparison as `COMPARE_SFX` in `enum class SoundType`

> 2. Make sure you create a buffer for the new sound.



> ✅**TODO: In **`**SoundService.cpp**`

> 

> 1. Include** **`Config.h`.

> 2. Load the comparison sound effect upon initialization.

> 3. Play the sound based on `SoundType`



> ✅**TODO: In **`**StickCollectionController.cpp**`

> 

> 1. Call the `playSound()` function to play the comparison sound within the `processLinearSearch` loop.





## Number of Array Access and Comparision


---



It's a good practice to calculate how many comparisons were made to find a target element.

And how many times the array was accessed during the search.



These numbers helps to understand which algorithm is better.

Lesser the number of comparisons and array access better the algorithm.



You will also track them in your visualizer.



> ✅**TODO: In **`**StickCollectionController**`

> 1. Add following properties:
>          `int number_of_comparisons`
>          `int number_of_array_access`
>   
> 2. Declare and implement a private function `void resetVariables()`, inside it reset the above two variables to `0` and call it in `reset()`
> 3. Create getter `getNumberOfComparisons()` & `getNumberOfArrayAccess()` for these properties.



Update your Linear Search algorithm to track the number of comparisons and array accesses.

On each operation increment both the variables by 1, until the target stick is found.



> ✅**TODO: In **`**StickCollectionController**`

> 1. Update `processLinearSearch()` and increment `number_of_comparisons` and `number_of_array_access` by `1` on each operation.



`StickCollectionController.h` ( Click Here! )```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include <vector>

namespace Gameplay {

    namespace Collection {

        class StickCollectionModel;
        class StickCollectionView;
        enum class SearchType;
        struct Stick;

        class StickCollectionContoller{

        private:
            StickCollectionView* collection_view;
            StickCollectionModel* collection_model;

            std::vector<Stick*> sticks;
            Stick* stick_to_search;

            Collection::SearchType search_type;

            int number_of_comparisons;
            int number_of_array_access;

            void initializeSticks();
            float calculateStickWidth();

            void updateSticksPosition();
            void shuffleSticks();

            void resetSticksColor();
            void resetVariables();
            void resetSearchStick();

            void processLinearSearch();
            void initializeSticksArray();
            float calculateStickHeight(int array_pos);

            void destroy();

        public:
            
            StickCollectionContoller();
            ~StickCollectionContoller();

            void initialize();
            void update();
            void render();

            void reset();
            void searchElement(SearchType search_type);

            SearchType getSearchType();
            int getNumberOfComparisons();
            int getNumberOfArrayAccess();

            int getNumberOfSticks();
        };
    }


}


```

           

`StickCollectionController.cpp` ( Click Here! )```cpp
// Some code
#include <random>

//Some Code
		void Gameplay::Collection::StickCollectionContoller::shuffleSticks()
		{
			std::random_device device;
			std::mt19937 random_engine(device());

			std::shuffle(sticks.begin(), sticks.end(), random_engine);
		}

		void Gameplay::Collection::StickCollectionContoller::resetSticksColor()
		{
			for (int i = 0; i < sticks.size(); i++)
				sticks[i]->stick_view->setFillColor(collection_model->element_color);
		}

		void Gameplay::Collection::StickCollectionContoller::resetVariables()
		{
			number_of_comparisons = 0;
			number_of_array_access = 0;
		}

		void Gameplay::Collection::StickCollectionContoller::resetSearchStick()
		{
			stick_to_search = sticks[std::rand() % sticks.size()];
			stick_to_search->stick_view->setFillColor(collection_model->search_element_color);
		}

		void Gameplay::Collection::StickCollectionContoller::processLinearSearch()
		{

				for (int i = 0; i < sticks.size(); i++)
				{

					number_of_array_access += 1;
					number_of_comparisons++;

					Global::ServiceLocator::getInstance()->getSoundService()->playSound(Sound::SoundType::COMPARE_SFX);

					if (sticks[i] == stick_to_search)
					{
						stick_to_search->stick_view->setFillColor(collection_model->found_element_color);
						stick_to_search = nullptr;
						return;
					}
					else
					{
						sticks[i]->stick_view->setFillColor(collection_model->processing_element_color);
						sticks[i]->stick_view->setFillColor(collection_model->element_color);
					}

				}
		}

		//Some Code
		
		void Gameplay::Collection::StickCollectionContoller::reset()
		{

			shuffleSticks();
			updateSticksPosition();
			resetSticksColor();
			resetSearchStick();
			resetVariables();
		}

		void Gameplay::Collection::StickCollectionContoller::searchElement(SearchType search_type)
		{
			this->search_type = search_type;

			switch (search_type)
			{
			case Gameplay::Collection::SearchType::LINEAR_SEARCH:
				processLinearSearch();
				break;
			}
		}

		SearchType Gameplay::Collection::StickCollectionContoller::getSearchType()
		{
			return search_type;
		}

		int Gameplay::Collection::StickCollectionContoller::getNumberOfComparisons()
		{
			return number_of_comparisons;
		}

		int Gameplay::Collection::StickCollectionContoller::getNumberOfArrayAccess()
		{
			return number_of_array_access;
		}

		int Gameplay::Collection::StickCollectionContoller::getNumberOfSticks()
		{
			return collection_model->number_of_elements;
		}

	}
}

```



You have created the methods needed to run Linear Search.

However, the result might differ slightly from what you expect from a visualizer.



Take a look at the video below:-



![ ](//outscal.github.io/Full-Stack-Game-Development/images/c16aa763d54d6f29.gif)



The search is running!



However, did you notice anything weird about the visualization?



Well, the linear search is running, but it is running instantly.

The search process is not being visualized at all!



Currently, it is impossible to tell what is happening.



How do you think we can fix this issue?

Think about it…

.

.

Now, check the answer below.

Answer Currently, the function is completed in a single frame.

Due to this, you only see the end result -> the green stick at the end!



To fix this, you must think of a way to provide a small delay between every iteration.

This will allow you to show the searching process as it happens!



Fortunately, every problem has a solution. (mostly)

The answer to this one is **threads!**



Confused?

No worries! You'll get the answer in the next lesson.



Let's properly visualize the search process in the next lesson!
