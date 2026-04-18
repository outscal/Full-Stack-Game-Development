In this lesson, you’ll finally visualize the linear search algorithm!

Excited?

Let's go!!



In the last lesson, you saw that the visualization was completed in a single frame.

Adding delay will help you with this issue. But do you think only adding delay is enough to complete your project?

Probably not! More things need to be done.



Let's explore what all do you have in this lesson:-

- **New thread:** You'll create a new thread to handle the search, ensuring the main program stays responsive while the search is running.
- **Short delay:** The thread will iterate through sticks, pausing for a brief duration between each comparison to visualize the searching algorithm taking place.
- **Sync threads:** The new thread joins the main thread before going to the main menu.



Let's start with adding the delay. This will help you visualize the search process on the sticks.



## Adding delay


---

You have to initialize two variables : 

- linear_search_delay (You have already initiated it😜)
- current_operation_delay



Let's discuss what they are and what their roles are, respectively.



`***linear_search_delay***`

- `linear_search_delay` is specific to the linear search algorithm.
- It represents the desired delay between comparisons during the visualization of linear search.
- If other search algorithms are added (e.g., binary search), they might have different operation delay for visualization.
- Having separate delay variables like `linear_search_delay` allows having specific control over the visualization for each search type.



`***current_operation_delay***`

- `current_operation_delay` is a general delay that applies to various parts of the visualization process during any search.
- This delay can be used to introduce pauses between visualizations, like for comparisons, array accesses, etc.
- The `current_operation_delay` variable is adjustable, allowing you to control the visualization speed for all search processes.



> ✅**TODO: In **`**StickCollectionController.h**`

> 

> 1. Declare a variable as `current_operation_delay`.

> 2. Also declare the corresponding getter `getDelayMilliseconds()` method for it.
> 3. Set `current_operation_delay = 0` in `reset()`



As you have declared both the delays, namely `linear_search_delay` and `current_operation_delay`, let's see how they will be implemented in the code. 



`current_operation_delay` is set according to the algorithm that is working.

Since it's the linear search, the `current_operation_delay` will be as same as the `linear_search_delay`.



> ✅**TODO: In **`**StickCollectionController.cpp**`

> 

> 1. Set `current_operation_delay` as `linear_search_delay` in `LINEAR_SEARCH` case in `searchElement()`



`StickCollectionController.h````cpp
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
            int current_operation_delay;


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



One task is done for the visualization.

It's time to move on to the next!



## Implementation of threading


---

Let’s implement threading now.



You will need to add two methods to the `**StickCollectionController:**`

- A method to start the search thread
- Another method to check if the search is complete and join the threads if they are.



> ✅**TODO: In **`**StickCollectionController.h**`

> 

> 1. Add the `#include <thread>`

> 2. Declare `search_thread` as `private` `std::thread `in class `StickCollectionController`

> 3. Declare `joinThreads()` as `private void` in class `StickCollectionController`



Now that you have declared the functions for threads, let's look into how the whole process of search visualization will take place on the screen:-

- When player clicks on linear search,  `searchElement` method gets triggered.
- Linear search is chosen as `search_type`.
- Set `current_operation_delay` as `linear_search_delay`.
- A separate thread handles the actual search algorithm, which allows the main thread to stay responsive during the search.
- `search_thread` is used to creates a new thread that calls the `processLinearSearch` method on the current instance of `StickCollectionController`.
- `joinThreads` waits for `search_thread` to finish, which ensures search visualization is completed before the program proceeds further.

 

Let's start with the process!



1. The player clicks `linear search` and the `searchElement` gets initiated.
2. The short delay is added as `current_operation_delay`
3. Now, the new thread is created to perform the linear search. So, the `processLinearSearch()` is going to get executed.



Click here to check `searchElement(SearchType search_type)````cpp
void Gameplay::Collection::StickCollectionContoller::searchElement(SearchType search_type)
{
	// stores the search type that is chosen
	this->search_type = search_type;

	switch (search_type)		// checks the value of search_type
	{
	case Gameplay::Collection::SearchType::LINEAR_SEARCH:			// checks if the search type is LINEAR SEARCH
	
		// obtains delay for linear search
		current_operation_delay = collection_model->linear_search_delay;
		
		// a new thread, 'search_thread' is created to execute the 'processLinearSearch'
		// 'this' keyword is passed to provide the context of the current 'StickCollectionContoller' object, allowing 'processLinearSearch' to access its data
		search_thread = std::thread(&StickCollectionContoller::processLinearSearch, this);
		break;
	}
}

```



Now, let’s discuss the thread methods before making any changes in the respective class.



1. `search_thread.joinable()` checks if the `search_thread` is still running and if it should be waited for. This method checks whether the new thread is ready to join the main thread.



Also note that, in the `update` function of `StickCollectionController`, the `processSearchThreadState` function is called.

This function is called everytime in `update` and checks if the thread is active or not or if the algorithm is completed or not.

If it is, then call the `joinThreads()`.



`**processSearchThreadState()**`

```cpp
// . . some code

void Gameplay::Collection::StickCollectionContoller::processSearchThreadState()
{
	if (search_thread.joinable() && stick_to_search == nullptr)
	{
		joinThreads();
	}
}

// . . some code
```



Next, you need to ensure the search operation's completion. 

For this, implement the `joinThreads()` function.



1. It calls the `join` method on the `search_thread` object which waits for the search thread to finish its execution before the main program continues.



`**joinThreads()**`

```cpp
// . . some code

void Gameplay::Collection::StickCollectionContoller::joinThreads()
{
	search_thread.join();			
}

// . . some code
```



> ✅**TODO:** In `StickCollectionController.cpp`

> 

> 1. Implement the `processSearchThreadState()`, which is mainly used to initiate the search operation.

> 2. Implement the `joinThreads()`.





If `joinThreads()` finished successfully, meaning the previous search thread is completed, then it continues with the search.



Now, it's time to discuss the actual linear search function.



## Implementing Linear Search


---

1. Comparison between sticks occurs. Based on the outcome, the color of the sticks changes accordingly.
2. The thread sleeps for a short duration. This allows for visualization of the search comparison happening on each stick.
3. After each pause, the default color is then set to the current stick.



`processLinearSearch()` :-

`processLinearSearch()````cpp
// . . some code

void Gameplay::Collection::StickCollectionContoller::processLinearSearch()
{
	Sound::SoundService* sound_service = Global::ServiceLocator::getInstance()->getSoundService();
	for (int i = 0; i < sticks.size(); i++)
	{


		number_of_array_access += 1;		// keeps track of the number of sticks array is accessed
		number_of_comparisons++;				// keeps track of the number of comparisons made between target stick and another stick

		sound_service->playSound(Sound::SoundType::COMPARE_SFX);				// play the comparision sound
		
		if (sticks[i] == stick_to_search)			// condition to check if the current stick is the target stick
		{
			// if the target stick is found, this line of code sets the fill colour of the target's stick view
			stick_to_search->stick_view->setFillColor(collection_model->found_element_color);	
			stick_to_search = nullptr;			// sets the pointer to null; meaning the search is completed.
			return;
		}
		else
		{
			// sets the fill color of the current stick's view to the processing_element_color; meaning the stick is still being checked
			sticks[i]->stick_view->setFillColor(collection_model->processing_element_color);
			
			//pauses the thread for a small duration to show the searching operation
			std::this_thread::sleep_for(std::chrono::milliseconds(current_operation_delay));
			
			// sets the fill color of the current stick's view back to the default element_color after the pause.
			sticks[i]->stick_view->setFillColor(collection_model->element_color);
		}

	}
}

// . . some code


```



> ✅**TODO:** In `StickCollectionController.cpp`

> 

> 1. Implement the `processLinearSearch()` for the search operation.



At last, don't forget to destroy the thread when your exit the process.



> ✅**TODO:** In `StickCollectionController.cpp`

> 1. Check if `search_thread` is `joinable()`, if it is then `join()` in `destroy()`



Click below for the complete code to ensure you didn't miss out on anything.

`StickCollectionController.h`  ( Click Here!)```cpp
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


            void initializeSticks();
            float calculateStickWidth();

            void updateSticksPosition();
            void shuffleSticks();

            void resetSticksColor();
            void resetVariables();
            void resetSearchStick();

            void processSearchThreadState();
            void joinThreads();
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
	}
}




```



The changes are done!

Let’s see if the search is being visualized properly before moving forward.

Check out the video below:-



![ ](//outscal.github.io/Full-Stack-Game-Development/images/95bbbe07a1fa76ee.gif)





In this lesson, you explored threading for visuals.



But remember, the search itself takes time, depending on how many items are present in the list.



In the next lesson, let's look at the time and space complexity for linear search!
