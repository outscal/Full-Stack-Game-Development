In this lesson, you'll explore the time complexity of linear search.



Imagine you're cleaning your messy room and need to find your favourite lost T-shirt (target element).



You can linearly search for your t-shirt in the following way:

1. **Start at the pile:** You move to the giant mountain of clothes on your chair (the list of elements).
2. **Check each item:** You pick up the first piece of clothing (checking the first element). Is it your favourite T-shirt? Nope? Keep it back on the pile and grab the next one.
3. **Keep digging:** You keep picking up clothes one by one, hoping to find your favourite T-shirt.
4. **Reaching the bottom:** You keep digging until you reach the bottom of the clothing pile (the end of the list). Still didn't find your favourite T-shirt?
5. **Not found:** If you get all the way through without finding your favourite T-shirt, then it must be hiding somewhere else (the element isn't in the list).



That's basically linear search! It goes through each item in a list, one by one, until it finds what you're looking for.



But do you know how long it took to complete the search process?

To understand this, let's learn about time complexity. 



## Time complexity


---



Time complexity measures how long an algorithm takes to run as the size of the input data increases. 

It's not about the actual time in seconds or milliseconds, but rather the **growth rate** of the time it takes as the input gets bigger.



Let's consider the same scenario of you finding your favourite T-shirt.

**Best Case (O(1)):** In the best case scenario, your T-shirt might be the first thing you pick up which is like finding what you need right away in the list. 

**Worst Case (O(N)):** But what if your favourite T-shirt is deep inside the pile of clothes? You might have to dig through almost everything before you find it or maybe the T-shirt isn't there at all. This is like the worst-case scenario for linear search, where it has to check every single item in the list.

**Average Case (O(N)):** You might not find it right away, but you won't need to search everything, either. You can find it halfway through the whole pile of clothes.



You should also have an idea about the time complexity of the search algorithm that you're applying to your project.

So, why don't you add time complexity to your project as well?

Great idea, isn't it? 



Let's go then !!!!



> ✅**TODO: In **`**StickCollectionController.h**`

> 

> 1. Declare a string type variable for time complexity.

> 2. Declare a getter method named `getTimeComplexity`




Checkout the code below:-

`StickCollectionController.h````cpp
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
            sf::String time_complexity;								// declared time_complexity variable


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
            sf::String getTimeComplexity();				//declared getTimeComplexity()
        };
    }


}




```



You should also assign value to the time complexity variable that you created for Linear search.



The code snippet is given below. You can go through it!

```cpp
// . . some code


		void Gameplay::Collection::StickCollectionContoller::searchElement(SearchType search_type)
		{
			this->search_type = search_type;

			switch (search_type)
			{
			case Gameplay::Collection::SearchType::LINEAR_SEARCH:
				time_complexity = "O(n)";											// assigned "O(n)" to 'time_complexity'
				current_operation_delay = collection_model->linear_search_delay;
				search_thread = std::thread(&StickCollectionContoller::processLinearSearch, this);
				break;
			}
		}


//. . some code
```



> ✅**TODO: In **`**StickCollectionController.cpp**`

> 

> 1. Assign the string value "O(n)" to the `time_complexity` variable.



Click here for the complete source code!

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

		sf::String Gameplay::Collection::StickCollectionContoller::getTimeComplexity()
		{
			return time_complexity;
		}

	}
}







```



Time complexity must be clear to you by now. 

But do you know the amount of extra memory/space Linear search consumed?

That's the space complexity.



## **Space Complexity**


---

The space complexity of linear search is O(1). This means that the algorithm's memory usage does not increase with the size of the input list. You only need constant extra space for variables used in the algorithm.



You've completed the Linear Search portion of the project.



In the upcoming assignment, you'll be creating the `GameplayUIController` from scratch. 

It will display various UI elements to visualize the search process, which includes:-

- **Search Type Text:** This displays the type of search algorithm being used (in this case, "Linear Search").
- **Array Access Text:** This displays the index of the currently accessed element during the search.
- **Comparisons Text:** This displays the number of comparisons made so far during the search.
- **Delay (ms)**: This displays the delay for each search visualization.
- **Time Complexity**: This displays the time complexity of the search algorithm.
- **Main Menu Button:** This button allows users to return to the main menu.



From the video, you can easily see the UI elements that are present on the screen.



![ ](//outscal.github.io/Full-Stack-Game-Development/images/ea55c0dc0ea9292e.gif)



Having explored Linear Search, you will continue with the remaining concepts of the project.



In the next chapter, you'll explore a more efficient search algorithm: Binary Search!



See you there!
