**BORGIRRR!! 🍔**



Keep your goal simple for this section: spawn a delicious burger every time the player starts the level. 🍔



![Burgir GIF - Burgir - Discover & Share GIFs](https://media.tenor.com/ldZ8NBLf7bMAAAAM/borger-borgir.gif)



To make this happen, you need a `FoodItem`, its dimensions, and its position. You'll figure out the position on the go. 

For now, create the properties for `FoodItem`, set up its dimensions, and call the lifecycle functions.



> **TODO: FoodService**
> **✅ **Create file for `class FoodService` inside `Food` folder and use `namespace Food`
> **✅ **Create properties:

> `FoodItem* current_food_item `
> `float cell_width `
> `float cell_height` 
> **✅** Create empty lifecycle functions 
> **✅ **Initialize `current_food_item` with `nullptr` in constructor 
> **✅ **update, render and delete `current_food_item` but make sure it is not null.



Click here to see `FoodService.h````cpp
#pragma once
#include <SFML/System/Vector2.hpp>
#include <vector>

namespace Food
{
	enum class FoodType;
	class FoodItem;

	class FoodService
	{
	private:
		
				FoodItem* current_food_item;

		float cell_width;
		float cell_height;

		void destroyFood();
		void reset();

	public:
		FoodService();
		~FoodService();

		void initialize();
		void update();
		void render();
	};
}
```

Click here to see `FoodService.cpp````cpp
#include "Food/FoodService.h"
#include "Global/ServiceLocator.h"
#include "Food/FoodItem.h"
#include "Level/LevelModel.h"
#include "Player/PlayerService.h"

namespace Food
{
	using namespace Time;
	using namespace Global;
	using namespace Level;
	using namespace Player;

	FoodService::FoodService()
	{
		current_food_item = nullptr;
	}

	FoodService::~FoodService()
	{
		destroyFood();
	}

	void FoodService::initialize()
	{
		//Yet to implement
	}

	void FoodService::update()
	{
		if (current_food_item) current_food_item->update();
	}

	void FoodService::render()
	{
		if (current_food_item) current_food_item->render();
	}
	
		void FoodService::destroyFood()
	{
		if (current_food_item) delete(current_food_item);
	}
}
```



## Spawning the Food


---



We've already discussed that `FoodService` need control to start and stop food spawning. 

Once the food spawning starts, you need to spawn a random food at a random position. 

You will handle the randomness in the next sections. For now, create a predefined food at predefined position.



**Starting Food Spawning (**`startFoodSpawning()`**)**

Set the cell’s dimensions when starting food-spawning. This function will get more responsible as we progress.



> **TODO: FoodService**
> 
> **✅**Create `void FoodService::startFoodSpawning()`, inside it, set `cell_width` and `cell_height` using `LevelService`



**Spawning and Creating Food**

To spawn food, you need to create it and store it in `current_food_item`

To create food, you need its position and type. You can take these values as arguments, create a new pointer to `FoodItem`, and return it.



> **TODO: FoodService**

> **✅** Create `FoodItem* FoodService::createFood(sf::Vector2i position, FoodType type)`

> **✅** Inside it, create new object of `FoodItem`, initialize it with `position`, `cell_width`, `cell_height` and `type` and finally return this new pointer.

> **✅** Create `void FoodService::spawnFood()`

> **✅** Inside it, call `current_food_item = createFood(sf::Vector2i(4, 6), FoodType::BURGER)`

> **✅** Call it inside `FoodService::startFoodSpawning()`





Click here to see `FoodService.h````cpp
#pragma once
#include <SFML/System/Vector2.hpp>
#include <random>
#include <vector>

namespace Food
{
	enum class FoodType;
	class FoodItem;

	class FoodService
	{
	private:
		FoodItem* current_food_item;

		float cell_width;
		float cell_height;

		FoodItem* createFood(sf::Vector2i position, FoodType type);
		void spawnFood();

		void destroyFood();

	public:
		FoodService();
		~FoodService();

		void initialize();
		void update();
		void render();

		void startFoodSpawning();
	};
}
```

Click here to see `FoodService.cpp````cpp
#include "Food/FoodService.h"
#include "Global/ServiceLocator.h"
#include "Food/FoodItem.h"
#include "Level/LevelModel.h"
#include "Player/PlayerService.h"

namespace Food
{
	using namespace Time;
	using namespace Global;
	using namespace Level;
	using namespace Player;

	FoodService::FoodService()
	{
		current_food_item = nullptr;
	}

	FoodService::~FoodService()
	{
		destroyFood();
	}

	void FoodService::initialize()
	{
		//Yet to implement
	}

	void FoodService::update()
	{
		if (current_food_item) current_food_item->update();
	}

	void FoodService::render()
	{
		if (current_food_item) current_food_item->render();
	}
	
		void FoodService::startFoodSpawning()
	{
		cell_width = ServiceLocator::getInstance()->getLevelService()->getCellWidth();
		cell_height = ServiceLocator::getInstance()->getLevelService()->getCellHeight();
		spawnFood();
	}
	
		FoodItem* FoodService::createFood(sf::Vector2i position, FoodType type)
	{
		FoodItem* food = new FoodItem();
		food->initialize(position, cell_width, cell_height, type);
		return food;
	}
	
		void FoodService::spawnFood()
	{
		current_food_item = createFood(sf::Vector2i(4, 6), FoodType::BURGER);
	}
	
		void FoodService::destroyFood()
	{
		if (current_food_item) delete(current_food_item);
	}
}
```



Now, it is time to integrate `FoodService` with `ServiceLocator`.



> **TODO:** `**ServiceLocator**` 
> **✅** Integrate `FoodService` with `ServiceLocator`. (Remember `FoodService` should only be updated and rendered when the game’s state is `GAMEPLAY`)



Finally, you need to start food spawning, and that’ll be done in `LevelService`



> **TODO: **`**LevelService**`

> **✅** Create `void LevelService::spawnFood()`, inside it, call `FoodService`’s `startFoodSpawning()` through `ServiceLocator`

> **✅** Call `spawnFood()` inside `createLevel()`



At this point, you should see a burger on the screen. But a single food item is boring. 

Let's randomize the food item and its position in the next section.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_05_2024__08_22_13.png)

***Game So Far***



**See you there!👋🏼**
