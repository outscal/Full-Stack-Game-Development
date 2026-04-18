In this lesson, you will implement all the methods you created in the previous lesson.

By the end of it, you will have rendered the sticks to the screen!



Let’s start by implementing all the methods in `**StickCollectionController.cpp**`



## STICKS'S HEIGHT AND WIDTH


---

What is the first thing that comes to your mind when you think of sticks?

Yes, the shape of the sticks! A stick has height and width. 



But how do you intend to set values for these?



![    ](/Full-Stack-Game-Development/images/74f994fc27e62832.png)

*Stick's size*





Will all the sticks be of the same height or different?

- The height of a stick can be dynamically calculated based on its position in the collection. The higher the position in the collection, the taller the stick.
- To do this, you can decide the maximum height for a stick (This variable is already there in the model)
- Then, you need to loop through the sticks vector and divide the position by the number of sticks. 
- Finally, multiply the above value by the maximum stick height variable. 



Think about how the stick's width can be calculated dynamically as well. ( Actually, think before you continue 😡 )



There are a couple of ways to decide the stick's width dynamically.



Let's discuss one of these ways:-

- The width of your screen will be distributed between the spacing between the sticks and the width of the sticks.



![ ](/Full-Stack-Game-Development/images/df3ed3fa6a1104d3.png)

*spacing between the sticks*



- You already have a variable to set the amount of spacing you want as a ratio of the overall screen space available. (`**space_percentage**`)
- You also have a variable for the number of sticks you want. 
- You can use both the above values to calculate the amount of the remaining space that is left over for the sticks.
- You can then divide the remaining space by the number of sticks. This will give you the width of a single stick!



Let's briefly discuss how the  `**space_percentage**` affects the width of the sticks.



Imagine the `**space_percentage**` value is `**0.1**`; this means that 10% of the total width will be reserved for spacing between the sticks.





![ ](/Full-Stack-Game-Development/images/3d7c523735891b3e.png)

*sticks when the space percentage is high (0.5)*





![ ](/Full-Stack-Game-Development/images/8e2a6b5cf71a3a8b.png)

*sticks when the space percentage is low (0)*



You can see from the above images to what extent the space percentage affects the stick's width!

Seems quite interesting, right?



Let's finally look at the code for initializing the sticks:-

`initializeSticks()`This method ensures that each stick is properly initialized with the calculated width and height and given the appropriate visual properties.



```cpp
void Gameplay::Collection::StickCollectionContoller::initializeSticks()
		{
			float rectangle_width = calculateStickWidth();			// calculate width


			for (int i = 0; i < collection_model->number_of_elements; i++)    // loop over the vector of sticks
			{
				float rectangle_height = calculateStickHeight(i); 	// calculate height ( assigning the returned value from the calculateStickHeight() method to the variable rectangle_height) 

				sf::Vector2f rectangle_size = sf::Vector2f(rectangle_width, rectangle_height); 	// create a 2D vector 'rectangle_size' to store width and height of rectangle

				// Initialize each stick at 0,0 with the default color 
				// You will update the position of sticks later
				// You will change the color of the sticks later to visually show the search algorithm taking place.
				sticks[i]->stick_view->initialize(rectangle_size, sf::Vector2f(0, 0), 0, collection_model->element_color);		
			}
		}

```



`calculateStickWidth()` `calculateStickWidth()` calculates the width of each stick based on the total available space and the spacing requirements and ensures that the sticks fit within the allocated space with the specified spacing between them.



```cpp
float Gameplay::Collection::StickCollectionContoller::calculateStickWidth()
		{
			// to get the width of the game window
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

```



`calculateStickHeight()``calculateStickHeight()` calculates the height of a stick based on its position (`array_pos`) within a collection of elements.



```cpp
	float Gameplay::Collection::StickCollectionContoller::calculateStickHeight(int array_pos)		// calculate the stick height based on its position in the array
	{
		// scaling its position to a range of 0.0 to 1.0 and multiplying by the maximum element height.
		return (static_cast<float>(array_pos + 1) / collection_model->number_of_elements) * collection_model->max_element_height;
	}

```





> **✅TODO :** **StickCollectionController**

> 

> 1. Implement all methods discussed above.



You have now initialized the height and width of the stick.

What do you think comes next? Think about it.... ( **Don't look below** 😡 )

Answer

You need to update the position of the sticks !!!

Currently, all the sticks are initialized at `0,0`



You will also need to make sure that the spacing between the sticks is applied correctly.







## STICK'S POSITION


---

Now, the main method `updateSticksPosition` that updates the position of each stick based on its index and spacing, ensuring that each stick is positioned correctly in the game window.



This method iterates through each stick in the `sticks` vector.

Then calculate:

- **X Position:**
- - By adding (i + 1)th times elements_spacing to the with of that stick.
  - This ensures each stick is spaced correctly based on its width and the specified spacing between sticks.
- **Y Position:**
- - By decreasing the height of that stick to the `element_y_position`
  - This positions the stick's bottom edge at the fixed `element_y_position`, ensuring the stick is correctly oriented and not upside down.



Finally, set the position of each stick using `x_position` & `y_position` in the visualizer.



`updateSticksPosition()`

```cpp
	void Gameplay::Collection::StickCollectionContoller::updateSticksPosition()
		{
			for (int i = 0; i < sticks.size(); i++)
			{
				// to calculate x_position of the current stick based on its index, width and spacing between them
				float x_position = (i * sticks[i]->stick_view->getSize().x) + ((i + 1) * collection_model->elements_spacing);	
				
				// to calculate y_position of the current stick based on fixed element_y_position and stick's height
				float y_position = collection_model->element_y_position - sticks[i]->stick_view->getSize().y;

				// to set the position of stick view
				sticks[i]->stick_view->setPosition(sf::Vector2f(x_position, y_position));
			}
		}

```





> **✅TODO :** **StickCollectionController**

> 

> 1. Implement `updateSticksPosition()`



The search process on sticks will occur when they(sticks) are initially set up.

Create a method for it, which will be called whenever a new game starts (during initialization).



> **✅TODO :** **StickCollectionController**

> 

> 1. Implement the `void initializeSticksArray()` method to initialize sticks based on the number of elements in the collection model as :

> -> Iterate through `collection_model->number_of_elements`.

> -> Create a new `Stick` object for each iteration.

> -> Add each `Stick` object to the `sticks` vector.

> 2. Call  `initializeSticksArray()` within the constructor of `StickCollectionContoller`



And finally, implement the `resetSticksColor()`, that integrate through all the sticks and set the colour of each stick to 

`element_color`.



```cpp
void Gameplay::Collection::StickCollectionContoller::resetSticksColor()
{
	for (int i = 0; i < sticks.size(); i++)
		sticks[i]->stick_view->setFillColor(collection_model->element_color);
}
```



> **✅TODO :** **StickCollectionController**

> 

> 1. Create and implement `resetSticksColor()`
> 2. Call `resetSticksColor()` and `updateSticksPosition()` in reset()
> 3. Call `reset()` during initialization.
> 4. Call `update()` and `render()` of each stick's `stick_view` in `StickCollectionController`'s `update()` and `render()`
> 5. Dont forget to delete the sticks and other properties.



Have a look at what the rendered sticks would look like!

![ ](/Full-Stack-Game-Development/images/b74530ec6f21a934.png)





You can run your code after this lesson and check it out for yourself.



Please take a look at the final code below to make sure that you didn’t miss anything!

`StickCollectionController.h`

```cpp
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

            Collection::SearchType search_type;


            void initializeSticks();
            float calculateStickWidth();

            void updateSticksPosition();

            void resetSticksColor();
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

            int getNumberOfSticks();
        };
    }
}
```



`StickCollectionController.cpp````cpp
#include "Gameplay/StickCollection/StickCollectionController.h"
#include "Gameplay/StickCollection/StickCollectionModel.h"
#include "Gameplay/StickCollection/StickCollectionView.h"
#include "Gameplay/StickCollection/Stick.h"
#include "Gameplay/GameplayService.h"
#include "Global/ServiceLocator.h"
#include <iostream>

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

		void Gameplay::Collection::StickCollectionContoller::resetSticksColor()
		{
			for (int i = 0; i < sticks.size(); i++)
				sticks[i]->stick_view->setFillColor(collection_model->element_color);
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
			
			initializeSticks();
						reset();
		}

		void Gameplay::Collection::StickCollectionContoller::update()
		{

			for (int i = 0; i < sticks.size(); i++)
				sticks[i]->stick_view->update();
		}

		void Gameplay::Collection::StickCollectionContoller::render()
		{
			for (int i = 0; i < sticks.size(); i++)
				sticks[i]->stick_view->render();
		}

		void Gameplay::Collection::StickCollectionContoller::reset()
		{
			updateSticksPosition();
			resetSticksColor();
		}

		void Gameplay::Collection::StickCollectionContoller::searchElement(SearchType search_type)
		{
		}

		SearchType Gameplay::Collection::StickCollectionContoller::getSearchType()
		{
			return search_type;
		}

		int Gameplay::Collection::StickCollectionContoller::getNumberOfSticks()
		{
			return collection_model->number_of_elements;
		}
	}
}




```







So, the sticks are being rendered on the screen now.

In the next chapter, you will start applying the search algorithm on the sticks, and then you'll finally see the visual representation of the algorithm through sticks.

Get ready for it!
