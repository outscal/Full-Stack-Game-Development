In the last chapter, you visualized linear search. 

Now, it's time to visualize a more powerful search algorithm: Binary Search.



![      ](/Full-Stack-Game-Development/images/395bdcebb80d7e59.jpg)





So, let's get into the implementation of binary search as a new feature in your game.



How will Binary Search work?



Let’s discuss the steps that you need to follow to implement the search algorithm:-

1. **Connecting to the Main Menu:** You'll connect the button in the main menu, which when clicked, triggers the binary search function.
2. **Sorting the Array:** Remember, binary search only works on sorted arrays. So, you'll implement a `sort()` method to arrange the array in ascending order.
3. **Comparing Elements:** You'll initialize a function called `compare()` to compare elements in the sorted array with the target value that is being searched.
4. **Binary Search Implementation:** You'll create the main part of the process - the `binarySearch()` method. This method will use the sorted data and the `compare()` function to find the target element's position in the array.



Now, let's start implementing these steps.



You will first need to declare and implement the methods for sorting the sticks that take place in the binary search.



## Sorting the sticks


---

The methods to implement sorting the sticks are : 

- a method for sorting elements
- a method for comparing the data.



Let's start with their declaration.



> ✅**TODO: In **`**StickCollectionController.h**`

> 

> 1. Declare a private method called `void sortElements()`.

> 2. Declare a `private` method to compare the data, namely `compareElementsByData(),` which takes two constant pointers to `Stick` objects (`a` and `b`) and returns a `boolean` value.



Now, let's implement the methods that you created.



- The `sortElements()` takes a range of elements and sorts them in an ascending order. 
- It uses a custom comparison function `compareElementsByData()` to sort by specific criteria.
- It calls the `updateSticksPosition()` function after sorting to update the view.



`**sortElements()**`

```cpp
// . . some code

void StickCollectionContoller::sortElements()
{
	// sort the sticks collection based on a custom comparison function
	std::sort(sticks.begin(), sticks.end(), [this](const Stick* a, const Stick* b) { return compareElementsByData(a, b); }); 		 // 'compareElementsByData' function to determine order

	// after sorting, update the positions of the sticks in the view.
	updateSticksPosition();
}

// . . some code
```



As you can see in the code, a helper function `compareElementsByData()` is used. Let's explore this function.



- The `compareElementsByData` function defines custom comparison criteria for sorting `StickCollection`. 
- It acts as a helper function for the `sortElements` method.



`**compareElementsByData(const Stick* a, const Stick* b) const**`

```cpp
// . . some code


// this function compares two Stick objects based on their data member. 
// it takes two pointers to Stick objects, 'a' and 'b', as arguments.
bool StickCollectionContoller::compareElementsByData(const Stick* a, const Stick* b) const
{
	
	// if 'a->data' is less than 'b->data', the expression evaluates to true which indicates that 'a' should precede 'b' in the sorted order.
	return a->data < b->data;
}

// . . some code
```



> ✅**TODO: In **`**StickCollectionController.cpp**`

> 

> 1. Implement the methods as discussed above.





## Adding delay


---

Now let's add the delay. This will help you visualize the search process on the sticks.



> ✅**TODO: In **`**StickCollectionModel.h**`

> 

> 1. Declare a public variable for delay, namely `binary_search_delay`

> 2. Define the `binary_search_delay` variable with some value.



It's time for the binary search method!



## Binary search on Sticks


---

The sticks have been sorted in order and the time delay has been set. Now, let's perform the Binary search on sticks!



> ✅**TODO: **

> 

> 1. Declare `void processBinarySearch()` function as private in `StickCollectionController.h`

> 2. Implement `processBinarySearch()` method in `StickCollectionController.cpp` but keep it empty for now.



You will be able to implement the method after it is connected to the `Binary Search Button` in the `Main Menu`.



1. When the player clicks `binary search` , the `searchElement` is initiated.
2. The short delay has been added as `current_operation_delay`
3. The new thread is created to perform the binary search. 



`**searchElement(SearchType search_type)**`

```cpp
void Gameplay::Collection::StickCollectionContoller::searchElement(SearchType search_type)
{
	// store the chosen search type
	this->search_type = search_type;

	switch (search_type)
	{
	case Gameplay::Collection::SearchType::BINARY_SEARCH:
		// sort the collection before the binary search performs
		sortElements();
		
		// sets delay for binary search
		current_operation_delay = collection_model->binary_search_delay;
		
		// separate thread for executing 'processBinarySearch'
		search_thread = std::thread(&StickCollectionContoller::processBinarySearch, this);
		break;
	}
}

```





The Binary search algorithm runs on the new thread.



Let’s finally implement `processBinarySearch()`

This method will do the following;-

- Initializes left, right and retrieve sound
- Calculates middle index, tracks access and comparisons, and plays a comparison sound.
- Checks if target is found at middle and updates element visuals.
- Updates search space based on comparison (`<=`): left for less than or equal to, right for greater.



`processBinarySearch()`

```cpp
void StickCollectionContoller::processBinarySearch()
{
	// initialize left index to the start of the collection
	int left = 0;
	
	// initialize right index to the size of the collection which is the end
	int right = sticks.size();

	Sound::SoundService* sound_service = Global::ServiceLocator::getInstance()->getSoundService();
	
	// loop for binary search
	while (left < right)
	{
		
		// calculate the middle index
		int mid = left + (right - left) / 2;
		number_of_array_access += 2;				//keeps track of the number of sticks array is accessed
		number_of_comparisons++;					// keeps track of the number of comparisons made between target stick and another stick

		sound_service->playSound(Sound::SoundType::COMPARE_SFX);			// play comparison sound effect

		// check if target element is found at the middle index
		if (sticks[mid] == stick_to_search)
		{
			// if the target element is found, set color for found element
			sticks[mid]->stick_view->setFillColor(collection_model->found_element_color);
			stick_to_search = nullptr;			//ets the pointer to null; meaning the search is completed
			return;
		}

		sticks[mid]->stick_view->setFillColor(collection_model->processing_element_color);			// if mid is not the target element, set the stick color to processing element color
		std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));			// //pauses the thread for a small duration to show the searching operation
		sticks[mid]->stick_view->setFillColor(collection_model->element_color);			// sets the fill color of the mid stick's view back to the default element_color after the pause.


		number_of_array_access++;			// increment counter for array access for mid element access
		
		// target can be in the right half or middle element itself
		if (sticks[mid]->data <= stick_to_search->data) left = mid;				// target must be in the right half, mid element included beacuse '<='
		else right = mid;				// target must be in the left half
	}
}


```





> ✅**TODO: In **`**StickCollectionController.cpp**`

> 

> 1. Implement the `processBinarySearch()` method as discussed above.



Click to see the complete code:-



`StickCollectionController.h`  ( CLICK HERE! )```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include <vector>
#include <thread>

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
            std::thread search_thread;


            int number_of_comparisons;
            int number_of_array_access;
            int current_operation_delay;
            int delay_in_ms;
            sf::String time_complexity;


            void initializeSticks();
            float calculateStickWidth();

            void updateSticksPosition();
            void shuffleSticks();
            void sortElements();
            bool compareElementsByData(const Stick* a, const Stick* b) const;

            void resetSticksColor();
            void resetVariables();
            void resetSearchStick();

            void processSearchThreadState();
            void joinThreads();
            void processLinearSearch();
            void processBinarySearch();
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
            int getDelayMilliseconds();
            sf::String getTimeComplexity();
        };
    }


}





```

`StickCollectionController.cpp` ( CLICK HERE! )```cpp
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



Let’s see if the search is being visualized properly before moving forward.

Check out the video below:-



![  ](/Full-Stack-Game-Development/images/35031f2695e1dbf7.gif)



Congrats, you have created the Binary search visualizer for the project!

Great work so far!



In the next lesson, let's look at the time complexity for the Binary search!
