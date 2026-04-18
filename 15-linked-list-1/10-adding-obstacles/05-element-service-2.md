**Spawn Obstacles!! 🪨**

Brainstorm the best approach to spawning obstacles before coding. 



Step-by-step process: 

`LevelService` will be called after the player selects the level.

`LevelService` ask the `LevelModel` to provide the element data list for that level.

`LevelService` will call the `ElementService` to create obstacles for that level.

`ElementService` will call necessary functions of `Obstacles` to bring everything to life. 



![gif](//outscal.github.io/Full-Stack-Game-Development/images/57adada380875f03.gif)

***As Simple As That***

Sounds like a plan, right? 

Let's visualize this with a diagram:

![Image](//outscal.github.io/Full-Stack-Game-Development/images/64507c84563bce5d.png)

***Flow diagram of Initialization of Obstacles***



The flow to get the obstacles on the screen will go like this:

- Process starts with the player choosing the Level in Level Selection UI Screen.
- Then, the player's input is passed to `LevelService` from `LevelSelectionUIController` to create the level.
- `LevelService` updates the `current_level` and then calls the `ElementService` passing necessary fields to spawn obstacles.
- `ElementService` then start spawning obstacles according to the position and dimensions it gets from `LevelService`.



## element service


---

> **TODO: **`**ElementService**`

> ✅ Create `ElementService.h` and `ElementService.cpp` and follow namespace `Element`
> ✅ Create empty lifecycle functions.



`ElementService` is not the place that holds the data about the Level.

But it is the place that holds the data about Obstacles.

Whatever obstacles will be spawned on the screen must be stored somewhere to enable easy access whenever required (obviously during a collision).

So, for that, you need a place to store your obstacles. 



> **TODO: **`**ElementService**`
> ✅ Add the following properties:

> `std::vector<Obstacle*> obstacle_list;`



This `obstacle_list` will store all the obstacles you spawn in our game.



The `EventService` will be responsible for spawning obstacles and then calling their lifecycle functions like `initialize`, `update`, and `render`.



> **TODO: **`**ElementService**`
> ✅ Call `obstacle_list` in a loop in `update()` and `render()`



## spawn obstacles


---

Since there are multiple obstacles, you can use a `for-loop` to spawn them efficiently. 

You need a method for creating a new obstacle, setting its position, and initializing it with the given dimensions.



```cpp
void spawnObstacle(sf::Vector2i position, float cell_width, float cell_height)
```



This function will use the position, cell width, and cell height as parameters to create and initialize an obstacle. 

Then, the newly created obstacles will be stored in `obstacle_list`.



```cpp
void ElementService::spawnObstacle(sf::Vector2i position, float cell_width, float cell_height)
{
    Obstacle* obstacle = new Obstacle();
    obstacle->initialize(position, cell_width, cell_height);
    obstacle_list.push_back(obstacle);
}
```



> **TODO: **`**ElementService**`

> ✅ Create and implement `spawnObstacle()`



## spawn Elements


---

You also need a method to loop through the list of element data and spawn each element accordingly. 



```cpp
const void spawnElements(std::vector<ElementData>& element_data_list, float cell_width, float cell_height)
```



It is initialized as `**const**`** **to ensure it doesn't modify any member variables of the class.

This function will iterate over the `element_data_list` and call `spawnObstacle` for each element.



You will be creating `element_data_list` in the next section. In brief `element_data_list` is the list of elements at a specific level. 



```cpp
const void ElementService::spawnElements(std::vector<ElementData>& element_data_list, float cell_width, float cell_height)
{
    for (int i = 0; i < element_data_list.size(); i++)
    {
        switch (element_data_list[i].element_type)
        {
            case Element::ElementType::OBSTACLE:
                spawnObstacle(element_data_list[i].position, cell_width, cell_height);
                break;
        }
    }
}
```



> **TODO: **`**ElementService**`

> ✅ Create and implement `spawnElements()`



**Click here to see **`**ElementService.h**`** **```cpp
#pragma once
#include <vector>
#include <SFML/System/Vector2.hpp>

namespace Element
{
	class Obstacle;
	struct ElementData;

	class ElementService
	{
	private:
		std::vector<Obstacle*> obstacle_list;

		void spawnObstacle(sf::Vector2i position, float cell_width, float cell_height);

	public:
		ElementService();
		~ElementService();

		void initialize();
		void update();
		void render();

		const void spawnElements(std::vector<ElementData>& element_data_list, float cell_width, float cell_height);
	};
}
```

**Click here to see **`**ElementService.cpp**````cpp
#include "Element/ElementService.h"
#include "Level/LevelModel.h"
#include "Global/ServiceLocator.h"
#include "Level/LevelController.h"
#include "Element/Obstacle.h"
#include "Level/LevelModel.h"

namespace Element
{
	ElementService::ElementService() = default;

	ElementService::~ElementService() = default;

	void ElementService::initialize() { }

	void ElementService::update()
	{
		for (int i = 0; i < obstacle_list.size(); i++)
		{
			obstacle_list[i]->update();
		}
	}

	void ElementService::render()
	{
		for (int i = 0; i < obstacle_list.size(); i++)
		{
			obstacle_list[i]->render();
		}
	}

	const void ElementService::spawnElements(std::vector<ElementData>& element_data_list, float cell_width, float cell_height)
	{
		for (int i = 0; i < element_data_list.size(); i++)
		{
			switch (element_data_list[i].element_type)
			{
			case::Element::ElementType::OBSTACLE:
				spawnObstacle(element_data_list[i].position, cell_width, cell_height);
				break;
			}
		}
	}

	void ElementService::spawnObstacle(sf::Vector2i position, float cell_width, float cell_height)
	{
		Obstacle* obstacle = new Obstacle();

		obstacle->initialize(position, cell_width, cell_height);
		obstacle_list.push_back(obstacle);
	}
}
```



And that's it! You've successfully created an `ElementService` to manage the spawning and lifecycle of your `Obstacle`. 


Next, you'll integrate it with other classes to get obstacles in action. 



**See you in the next section! 👋🏼**
