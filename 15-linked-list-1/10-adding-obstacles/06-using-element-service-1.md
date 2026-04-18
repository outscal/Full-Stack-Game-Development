**Communication Between Services Through **`**ServiceLocator**`**!!**



I'll walk you through the process step-by-step, ensuring everything is clear and engaging.



> **TODO: ServiceLocator **

> ✅ Integrate `ElementService` with `ServiceLocator`, by creating its property, calling all its lifecycle functions, creating a getter function and finally deleting it. Remember: only update and render the `ElementService` when the game's state is `GameState::GAMEPLAY`



**Done with this? **

Great! Let's move on to the next step.



## Updating `LevelData`


---

Next, you'll update `LevelData` to store information about the elements (like obstacles) in each level.

Why???

Cause you need to keep track of all the elements in each level to know where and what type they are.



You'll modify `LevelData` to include a list of element data. (the one you used to Spawn Elements in `ElementService`).



> **TODO: Update **`**LevelData.h**`
> ✅ Add `std::vector<Element::ElementData>element_data_list` to `LevelData`
> ✅ Pass the `std::vector<Element::ElementData>* data_list` to `LevelData` constructor and update the `element_data_list`



**Click here to see **`**LevelData.h**`** **```cpp
#pragma once
#include "Level/LevelService.h"
#include "Element/ElementData.h"

namespace Level
{
    struct LevelData
    {
        LevelData(LevelNumber ind, std::vector<Element::ElementData>* data_list)
        {
            level_index = ind;
            element_data_list = data_list;
        }

        LevelNumber level_index;
        std::vector<Element::ElementData>* element_data_list;
    };
}
```



Done with this as well?** Awesome! **

Let's move on to the next step.



`LevelData` will get the information about elements through `LevelModel`. 

In your game, **Level Two** will resemble the OG snake’s level 2....🐍



The `LevelModel` class should handle the creation and initialization of `LevelData` objects for each level.

It builds blueprints (`LevelData`) for each level, storing details like object types and positions and storing these objects internally for efficient access.



> **TODO: Update **`**LevelModel**`

> ✅Add following properties in `**LevelModel.h**`**:**
>         `std::vector<Element::ElementData> level_one_element_list;`
>         `std::vector<Element::ElementData> level_two_element_list;`
>         `std::vector<LevelData> level_configurations;`
> ✅Create a `private` method `void initializeLevelData()`
> ✅Create a following getter for element data list in `LevelModel` & `LevelController` to maintain MVC architecture
>     `const std::vector<Element::ElementData>& getElementDataList(int level_to_load)`





## initialize level data


---

Inside `initializeLevelData()` , push the `LevelData` for both the levels inside `level_configurations`.

Here's the code snippet:

```cpp
void LevelModel::initializeLevelData()
	{
		level_configurations.push_back(LevelData(Level::LevelNumber::ONE, &level_one_element_list));
		level_configurations.push_back(LevelData(Level::LevelNumber::TWO, &level_two_element_list));
	}
```



> **TODO:  **`**LevelModel**`
> ✅Implement `initializeLevelData()` as above.



**Click here to see **`**LevelModel.cpp**````cpp
#include "Level/LevelModel.h"
#include "Level/LevelService.h"
#include "Element/ElementService.h"

namespace Level
{
	using namespace Element;

	LevelModel::LevelModel() = default;

	LevelModel::~LevelModel() = default;

	void LevelModel::initialize(int width, int height)
	{
		cell_width = static_cast<float>(width) / static_cast<float>(number_of_columns);
		cell_height = static_cast<float>(height) / static_cast<float>(number_of_rows);

		initializeLevelData();
	}

	void LevelModel::initializeLevelData()
	{
		level_configurations.push_back(LevelData(Level::LevelNumber::ONE, &level_one_element_list));
		level_configurations.push_back(LevelData(Level::LevelNumber::TWO, &level_two_element_list));
	}

	const std::vector<ElementData>& LevelModel::getElementDataList(int level_to_load)
	{
		return *level_configurations[level_to_load].element_data_list;
	}

	float LevelModel::getCellWidth()
	{
		return cell_width;
	}

	float LevelModel::getCellHeight()
	{
		return cell_height;
	}
}
```

Click here to see `LevelController`'s `getElementDataList()````cpp
const std::vector<ElementData>& LevelController::getElementDataList(int level_to_load)
{
	return level_model->getElementDataList(level_to_load);
}
```



**You are a pro now!!**



Finally, update `LevelService` to spawn the level elements using the data you've set up.

You need to ensure that obstacles and other elements are created and positioned correctly when a level is loaded.

You'll create a method to spawn level elements and call it inside `createLevel()`.



> **TODO: Update **`**LevelService**`

> ✅Create `spawnLevelElements(LevelNumber level_to_load)` and call it from `createLevel()`
> ✅Call `spawnElements(element_data_list, cell_width, cell_height)` from `spawnLevelElements()`





Click here to see `**LevelService**````cpp
void LevelService::createLevel(LevelNumber level_to_load)
{
	current_level = level_to_load;
	spawnLevelElements(level_to_load);
	spawnPlayer();
}

void LevelService::spawnLevelElements(LevelNumber level_to_load)
{
	float cell_width = level_controller->getCellWidth();
	float cell_height = level_controller->getCellHeight();

	std::vector<ElementData> element_data_list = level_controller->getElementDataList((int)level_to_load);
	ServiceLocator::getInstance()->getElementService()->spawnElements(element_data_list, cell_width, cell_height);
}
```



Now that you have connected everything. Great!!



![i am restraining from freaking out quite admirably — Well, that's what will  happen if you open the red...](/Full-Stack-Game-Development/images/4c9fcbe7da0be717.gif)



But wait! You still have to fill  `level_two_element_list` with elements. 

**Be Ready For Level 2!!!**



**See you in the next section! 👋🏼**
