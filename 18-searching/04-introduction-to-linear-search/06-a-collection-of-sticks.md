Although you have created the structure for a single stick, you still need to manage a collection of them for the visualization part.

In this lesson, you will create the classes that are necessary for stick collection and finally visualize them in the next lesson.



Without any further delay, let's get started!

Starting with the Model and View.



## StickcollectionModel and Stickcollectionview


---

As like any other Model, `StickCollectionModel` also handles the data related to the sticks that are common for the whole collection like:

- The upper limit for the height of any stick in the collection.
- The actual amount of spacing between the sticks. As the spacing can defer based on the game window, you need a setter as well. 
- The percentage of the screen space allocated to spacing.
- Different colours to represent the state of the stick.
- The total number of sticks in the collection.
- Constant delay between each step in the search algorithm to visualize the process.
- And one more that represents the vertical position where the sticks will be rendered in the window.



`StickCollectionModel` also handles the `enums` for different types of `SearchType`

```cpp
enum class SearchType
{
    LINEAR_SEARCH,
    BINARY_SEARCH,
};
```



> ✅ **TODO: StickCollectionModel**
> 
> 1. Create `StickCollectionModel` with empty constructor, destructor, `initialize()` & `update()`. Add nested namespace `Collection` and `Gameplay`
> 2. Add the following properties as public:

> `const float max_element_height = 820.f;`
> `float elements_spacing = 25.f;`
> `const float element_y_position = 1020.f;`
> `float space_percentage = 0.50f;`
> 
> `const sf::Color element_color = sf::Color::White;`
> `const sf::Color search_element_color = sf::Color::Blue;`
> `const sf::Color found_element_color = sf::Color::Green;`
> `const sf::Color processing_element_color = sf::Color::Red;`
> 
> `int linear_search_delay = 120;`
> `int number_of_elements = 100;`

> 3. Create a public method `void setElementSpacing(float space)` and set `elements_spacing` as `space` in it.
> 4. Create `enum class SearchType` as above.



`StickCollectionModel.h````cpp
#pragma once
#include <SFML/Graphics.hpp>

namespace Gameplay
{
    namespace Collection {

        enum class SearchType
        {
            LINEAR_SEARCH,
            BINARY_SEARCH,
        };

        class StickCollectionModel {

        public:
            const float max_element_height = 820.f;
            float elements_spacing = 25.f; //acttual amount of spacing between sticks
            const float element_y_position = 1020.f;
            float space_percentage = 0.50f; //the percentage of the screen space allocated to spacing (0 - 1)

            const sf::Color element_color = sf::Color::White;
            const sf::Color search_element_color = sf::Color::Blue;
            const sf::Color found_element_color = sf::Color::Green;
            const sf::Color processing_element_color = sf::Color::Red;

            int linear_search_delay = 120;


            int number_of_elements = 100;

            StickCollectionModel();
            ~StickCollectionModel();

            void initialize();
            void update();

            void setElementSpacing(float space);

        };

    }
}
```



As such, everything related to UI is handled by `GameplayView` so, nothing important for `StickCollectionView`.



> ✅ **TODO: StickCollectionView**
> 
> 1. Create `StickCollectionView` with empty lifecycle methods. Add nested namespace `Collection` and `Gameplay`



That was all for Model and View. 

Now it's time for the boss, who controls the majority of elements within the visualization.



## Stickcollectioncontroller


---

The `StickCollectionController` handles everything related to the sticks, from their creation to modification and rendering. It oversees all actions involving the stick collection.



> ✅**TODO:**

> 

> 1. Create `StickCollectionController` with empty lifecycle methods and follow nested `namespace Collection` & `Gameplay`



`StickCollectionController` stores all the `Stick` in `vector` and controls all of them.



But what control does it have for the collection of sticks?

Despite each stick being independent in holding its height, width, and other properties, the controller manages various aspects such as:

- **Creation**: Initializes the collection of sticks, setting their initial properties.
- **Modification**: Updates the properties of sticks, such as height, colour, and position, during various operations.
- **Rendering**: Ensures all sticks are correctly displayed on the screen, maintaining visual consistency.
- **Resetting**: Resets the sticks to their default state, preparing them for new operations.
- **Searching**: Implements algorithms to search for specific sticks within the collection, managing search operations and visual feedback.
- Getter and setter for the properties of sticks and UI properties.
- And much more



As these things, sticks can't do their own. 

These functions will be implemented in the next lesson, but first, create a structure of what `StickCollectionController` will look like.

And after that, you take your time to make your views on what these functions would be for.



> ✅**TODO:** **StickCollectionController.h**
> 
> 1. Create `StickCollectionController` with empty lifecycle methods.
> 2. Add the following properties as private:

> `StickCollectionView* collection_view;`
> `StickCollectionModel* collection_model;`
> `std::vector<Stick*> sticks;`
> `Collection::SearchType search_type;`

> 3. Take care of the forward declaration of `StickCollectionView`, `StickCollectionModel` , `Stick` & `SearchType`
> 4. Getter for `search_type` and `number_of_elements`
> 5. Create the following properties private methods:

> `void initializeSticks();`
> `float calculateStickWidth();`
> `void updateSticksPosition();`
> `void resetSticksColor();`
> `void initializeSticksArray();`
> `float calculateStickHeight(int array_pos);`

> 6. Create an empty public method `void searchElement(SearchType search_type)`



This `StickCollectionController.h` provides a framework for visualizing and managing a collection of sticks and implementing operations like searching.



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

            SearchType getSearchType();

            int getNumberOfSticks();
        };
    }
}
```

          



## Connecting Stickcollectioncontroller to gameplayservice


---

Now comes the final step to be performed.

Lastly, you have to connect the `StickCollectionController` to the `GameplayService` because the `GameplayService` initializes the `StickCollectionController.`



> ✅**TODO:** **In GameplayService.h**

> 

> 1. Integrate `StickCollectionController` into `GameplayService` to manage the collection of sticks within the gameplay.

> 2. Add the following properties as private:

> `GameplayController* gameplay_controller;`
> `StickCollectionContoller* collection_controller;`

> 3. Create a method `void searchElement(Collection::SearchType search_type)` that calls the `searchElement()` of  `StickCollectionController` .

> 4.. Also, create its getter method.



When the linear search button gets clicked on the main menu, the `GameplayService` should call this created method in `StickCollectionController`. 

This acts as a service layer that coordinates the gameplay-related functionalities like initialization, updating, rendering, and searching the elements. 



Click below for the code.

`GameplayService.h````cpp
#pragma once
#include <SFML/System/String.hpp>
#include "Gameplay/StickCollection/StickCollectionModel.h"
#include "Gameplay/StickCollection/StickCollectionController.h"

namespace Gameplay
{
	using namespace Collection;
	class GameplayController;
	enum class SearchType;

	class GameplayService
	{
	private:
		GameplayController* gameplay_controller;
		StickCollectionContoller* collection_controller;


	public:
		GameplayService();
		~GameplayService();

		void initialize();
		void update();
		void render();

		void reset();
		void searchElement(Collection::SearchType search_type);

		Collection::SearchType getCurrentSearchType();
		
		int getNumberOfSticks();
	
	};
}
```



In this lesson, you have created the structure for the `StickCollectionController`



In the next lesson, you will implement these functions and get your sticks visualized.

During the implementation, you will learn about each method and get an understanding of how the visualizer will work.



See you there!
