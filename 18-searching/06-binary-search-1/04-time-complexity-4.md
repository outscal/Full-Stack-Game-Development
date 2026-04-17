In this lesson, let's understand about the time complexity of Binary Seach.



Let's go through all the key points and differences that make binary search different from other algorithms.



Starting with time complexity analysis:-

The time it takes for binary search to find something in an array is determined by the number of times it can divide the array in half until it finds target element or confirms its absence.



The key to understanding the time complexity lies in the worst-case scenario. 



## Worst-case time complexity


---



Worst-case time complexity for binary search involves two possibilities:

- **Target is at the end:** The target element exists but is at the end of the sorted array.
- **Target is not present:** The target element is not present in the array at all.



In both these cases, the search continues until the search space is reduced to a single element, which is the target element, requiring the maximum number of comparisons.



Let's represent the number of divisions required in the worst case as `k`.



- **Initial Search Space:** There is an array of size `n`.
- **First Division:** After the first comparison, the search space reduces to `n/2`.
- **Second Division:** In the next iteration, the search space becomes `n/4` (half of `n/2`).
- **Continued Divisions:** This halving process continues with each iteration.



The number of divisions required to reduce the search interval to 1 element or determine that the target is not present can be represented by the equation:

```cpp
n / 2^k = 1
```

where,

`n` is the initial size of the array

`k` is the number of divisions (comparisons in the worst case)

`2^k` represents the number of times the array has been halved.



*Solving for k:*

To find out how many divisions are needed to reach the condition where the search interval is down to one element, you need to solve for `k`.



To solve for `k`, take the logarithm of both sides of the equation with base 2 (since the process is halving):

```cpp
2^k = n
k = log2(n)
```

`k = log2(n)` tells that `k` is the logarithm of the initial size of the array `n` to the base `2`.



This gives:

```cpp
log2(n) - k = 0
```



With `k` (comparisons or divisions) growing logarithmically with n (array size), the time complexity of the binary search is **O(log n)**.

```cpp
k = log2(n)
```

This indicates that the number of comparisons or divisions in binary search grows logarithmically with the size of the array



Now, let's look at some of the features of Binary search.



## features of binary search


---



**Logarithmic growth**: With a logarithmic time complexity of `**O(log n)**`, binary search ensures that the number of comparisons needed remains relatively low even with large arrays.



**Division of search space**: Binary search reduces the search space by **half** with each iteration. This process of halving the search interval rapidly narrows down the possible locations of the target element.



**Sorted array requirement**: The efficiency of binary search relies on the array being sorted. Without a sorted array, binary search cannot be applied directly. But, when the array is sorted, binary search quickly locates the target element.



You should also assign value to the time complexity variable for binary search.



> ✅**TODO: In **`**StickCollectionController.cpp**`

> 

> 1. Assign the string value "O(log n)" to the variable representing the time complexity for binary search.



The code snippet is given below. Go through it!

Click here!

```cpp
// . . some code

void Gameplay::Collection::StickCollectionContoller::searchElement(SearchType search_type)
{
	this->search_type = search_type;

	switch (search_type)
	{
	case Gameplay::Collection::SearchType::BINARY_SEARCH:
		sortElements();
		time_complexity = "O(log n)";
		current_operation_delay = collection_model->binary_search_delay;
		search_thread = std::thread(&StickCollectionContoller::processBinarySearch, this);
		break;
	}
}

// . .  some code

```





Check out the code below to make sure you didn't miss anything.

`StickCollectionController.cpp````cpp
#include "Gameplay/StickCollection/StickCollectionController.h"
#include "Gameplay/StickCollection/StickCollectionModel.h"
#include "Gameplay/StickCollection/StickCollectionView.h"
#include "Gameplay/StickCollection/Stick.h"
#include "Gameplay/GameplayService.h"
#include "Global/ServiceLocator.h"
#include "Sound/SoundService.h"
#include <random>

namespace Gameplay {
	namespace Collection {

		using namespace UI::UIElement;
		using namespace Global;
		using namespace Graphics;

		void Gameplay::Collection::StickCollectionContoller::initializeSticks()
		{
			float rectangle_width = calculateStickWidth();


			for (int i = 0; i < collection_model->number_of_elements; i++)
			{
				float rectangle_height = calculateStickHeight(i); //calc height

				sf::Vector2f rectangle_size = sf::Vector2f(rectangle_width, rectangle_height);

				sticks[i]->stick_view->initialize(rectangle_size, sf::Vector2f(0, 0), 0, collection_model->element_color);
			}
		}

		float Gameplay::Collection::StickCollectionContoller::calculateStickWidth()
		{
			float total_space = static_cast<float>(ServiceLocator::getInstance()->getGraphicService()->getGameWindow()->getSize().x);

			// Calculate total spacing as 10% of the total space
			float total_spacing = collection_model->space_percentage * total_space;

			// Calculate the space between each stick
			float space_between = total_spacing / (collection_model->number_of_elements - 1);
			collection_model->setElementSpacing(space_between);

			// Calculate the remaining space for the rectangles
			float remaining_space = total_space - total_spacing;

			// Calculate the width of each rectangle
			float rectangle_width = remaining_space / collection_model->number_of_elements;

			return rectangle_width;
		}

		void Gameplay::Collection::StickCollectionContoller::updateSticksPosition()
		{
			for (int i = 0; i < sticks.size(); i++)
			{
				float x_position = (i * sticks[i]->stick_view->getSize().x) + ((i + 1) * collection_model->elements_spacing);
				float y_position = collection_model->element_y_position - sticks[i]->stick_view->getSize().y;

				sticks[i]->stick_view->setPosition(sf::Vector2f(x_position, y_position));
			}
		}

		void Gameplay::Collection::StickCollectionContoller::shuffleSticks()
		{
			std::random_device device;
			std::mt19937 random_engine(device());

			std::shuffle(sticks.begin(), sticks.end(), random_engine);
		}

		void StickCollectionContoller::sortElements()
		{
			std::sort(sticks.begin(), sticks.end(), [this](const Stick* a, const Stick* b) { return compareElementsByData(a, b); });
			updateSticksPosition();
		}

		bool StickCollectionContoller::compareElementsByData(const Stick* a, const Stick* b) const
		{
			return a->data < b->data;
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

		void Gameplay::Collection::StickCollectionContoller::processSearchThreadState()
		{
			if (search_thread.joinable() && stick_to_search == nullptr)
			{
				joinThreads();
			}
		}

		void Gameplay::Collection::StickCollectionContoller::joinThreads()
		{
			search_thread.join();
		}

		void Gameplay::Collection::StickCollectionContoller::processLinearSearch()
		{
			Sound::SoundService* sound_service = Global::ServiceLocator::getInstance()->getSoundService();
			for (int i = 0; i < sticks.size(); i++)
			{


				number_of_array_access += 1;
				number_of_comparisons++;

				sound_service->playSound(Sound::SoundType::COMPARE_SFX);

				if (sticks[i] == stick_to_search)
				{
					stick_to_search->stick_view->setFillColor(collection_model->found_element_color);
					stick_to_search = nullptr;
					return;
				}
				else
				{
					sticks[i]->stick_view->setFillColor(collection_model->processing_element_color);
					std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));
					sticks[i]->stick_view->setFillColor(collection_model->element_color);
				}

			}
		}

		void StickCollectionContoller::processBinarySearch()
		{
			int left = 0;
			int right = sticks.size();

			Sound::SoundService* sound_service = Global::ServiceLocator::getInstance()->getSoundService();
			while (left < right)
			{
				int mid = left + (right - left) / 2;
				number_of_array_access += 2;
				number_of_comparisons++;

				sound_service->playSound(Sound::SoundType::COMPARE_SFX);

				if (sticks[mid] == stick_to_search)
				{
					sticks[mid]->stick_view->setFillColor(collection_model->found_element_color);
					stick_to_search = nullptr;
					return;
				}

				sticks[mid]->stick_view->setFillColor(collection_model->processing_element_color);
				std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));
				sticks[mid]->stick_view->setFillColor(collection_model->element_color);

				number_of_array_access++;
				if (sticks[mid]->data <= stick_to_search->data) left = mid;
				else right = mid;
			}
		}

		void Gameplay::Collection::StickCollectionContoller::initializeSticksArray()
		{
			for (int i = 0; i < collection_model->number_of_elements; i++)
				sticks.push_back(new Stick(i));
		}

		float Gameplay::Collection::StickCollectionContoller::calculateStickHeight(int array_pos)
		{
			return (static_cast<float>(array_pos + 1) / collection_model->number_of_elements) * collection_model->max_element_height;
		}

		void Gameplay::Collection::StickCollectionContoller::destroy()
		{
			if (search_thread.joinable()) search_thread.join();

			for (int i = 0; i < sticks.size(); i++) delete(sticks[i]);
			sticks.clear();

			delete (collection_view);
			delete (collection_model);
		}

		Gameplay::Collection::StickCollectionContoller::StickCollectionContoller()
		{
			collection_view = new StickCollectionView();
			collection_model = new StickCollectionModel();
			initializeSticksArray();
		}

		Gameplay::Collection::StickCollectionContoller::~StickCollectionContoller()
		{
			destroy();
		}

		void Gameplay::Collection::StickCollectionContoller::initialize()
		{
			
						collection_model->initialize();
			initializeSticks();
			
						reset();

			time_complexity = "XYZ";
		}

		void Gameplay::Collection::StickCollectionContoller::update()
		{
			processSearchThreadState();

			collection_view->update();

			for (int i = 0; i < sticks.size(); i++)
				sticks[i]->stick_view->update();
		}

		void Gameplay::Collection::StickCollectionContoller::render()
		{
			collection_view->render();
			for (int i = 0; i < sticks.size(); i++)
				sticks[i]->stick_view->render();
		}

		void Gameplay::Collection::StickCollectionContoller::reset()
		{
			current_operation_delay = 0;

			if (search_thread.joinable()) search_thread.join();

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
				time_complexity = "O(n)";
				current_operation_delay = collection_model->linear_search_delay;
				search_thread = std::thread(&StickCollectionContoller::processLinearSearch, this);
				break;
			case Gameplay::Collection::SearchType::BINARY_SEARCH:
				sortElements();
				time_complexity = "O(log n)";
				current_operation_delay = collection_model->binary_search_delay;
				search_thread = std::thread(&StickCollectionContoller::processBinarySearch, this);
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

		int Gameplay::Collection::StickCollectionContoller::getDelayMilliseconds()
		{
			return current_operation_delay;
		}

		sf::String Gameplay::Collection::StickCollectionContoller::getTimeComplexity()
		{
			return time_complexity;
		}

	}
}




```



You have learnt all the necessary concepts for both the search algorithms: **Linear search** and **Binary search**.



In the next lesson, you'll compare both of them.

You'll explore their strengths and weaknesses to help you pick the right one according to your needs.



For the final time, see you in the next lesson!
