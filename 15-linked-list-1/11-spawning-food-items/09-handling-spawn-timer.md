**FOOD ON TIME!!**



Just like in a real kitchen, timing is everything! 

To keep your game dynamic and challenging, you need food to spawn at regular intervals. 

This requires a method to control when to start and stop generating food, much like flipping an hourglass to measure time.



![gif](/Full-Stack-Game-Development/images/e1b92b4856587cad.gif)



Recall from Space Invaders, where powerups or enemies appeared at set intervals. It's a bit like that here. You'll need to create a mechanism that periodically spawns food items, much like clockwork.



To achieve this, you can rely on `deltaTime` from `TimeService`. This handy tool measures the time between frames. When the timer hits a certain mark, it resets, triggering an event—like food spawning!



> **TODO:**` FoodService`
> **✅** Add the following properties:
> `const float spawn_duration = 4.f;`
> `float elapsed_duration;`
> **✅** Inside `initialize()` method set `elapsed_duration` = `spawn_duration`
> **✅** Inside `reset()` method set `elapsed_duration = 0.f`
> **✅** Create a method `updateElapsedDuration()`



Now, why do you need to update `elapsed_duration`? 

Well, `elapsed_duration` keeps track of how much time has passed since the last food spawn. 

By updating it with the `deltaTime` at each frame, you ensure that you accurately measure the time between food spawns. 

It's like constantly ticking off seconds on a stopwatch! ⏱️

While your seconds are equal to `deltaTime`.



![Timer - Lineal - Wired - Lordicon](https://lordicon.com/icons/wired/lineal/46-timer-stopwatch.gif)



Now let's integrate the timer to handle food spawning. 

In your game, the `handleFoodSpawning()` function ensures food appears at regular intervals. 

When the elapsed time reaches the spawn duration, it destroys the current food, resets the timer, and spawns new food. 


> **TODO:**` FoodService`
> **✅** Create a method `handleFoodSpawning()`



Click here to check `handleFoodSpawning()````cpp
void FoodService::handleFoodSpawning()
{
	if (elapsed_duration >= spawn_duration)
	{
		destroyFood();
		reset();
		spawnFood();
	}
}
```



**Done That?? Great!**

Just like a chef, who decides when to start serving food and when to stop, you need to have similar control over when food appears and disappears in your game.



![Open The Door For Guests GIF | GIFDB.com](/Full-Stack-Game-Development/images/3d891fc3f0e2f340.gif)



To maintain this control, let's introduce an enum to handle the food spawning status. This will allow you to easily switch between active and inactive states, like opening and closing the doors of a restaurant. 



`enum FoodSpawningStatus`

```cpp
enum FoodSpawningStatus
{
	ACTIVE,
	IN_ACTIVE,
};
```



How to integrate `FoodSpawningStatus` in your game?

You need 3 methods: `startFoodSpawning()`, `update()` & `stopFoodSpawning()`

- **startFoodSpawning():** This method sets the `current_spawning_status` to `ACTIVE`, signalling the start of food spawning.
- **update():** You'll control food spawning based on the current status. When ACTIVE, this method handles the spawning process.
- **stopFoodSpawning():** This method sets the `current_spawning_status` to `IN_ACTIVE`, signalling to stop food spawning. Then, destroy the food and reset the timer.



> **TODO: FoodService **
> ✅ Create `enum FoodSpawningStatus`
> ✅ Add a property : `FoodSpawningStatus current_spawning_status`
> ✅ Update `startFoodSpawning()` and `update()`
> ✅ Create `stopFoodSpawning()`



Click here to see `FoodService.h````cpp
#pragma once
#include <SFML/System/Vector2.hpp>
#include <random>
#include <vector>

namespace Food
{
	enum class FoodType;
	class FoodItem;

	enum FoodSpawningStatus
	{
		ACTIVE,
		IN_ACTIVE,
	};

	class FoodService
	{
	private:
		const float spawn_duration = 4.f;

		float elapsed_duration;

		FoodSpawningStatus current_spawning_status;
		FoodItem* current_food_item;

		float cell_width;
		float cell_height;

		// To generate random values.
		std::default_random_engine random_engine;

		// To give random seed to generator.
		std::random_device random_device;

		FoodItem* createFood(sf::Vector2i position, FoodType type);
		void spawnFood();

		sf::Vector2i getValidSpawnPosition();
		sf::Vector2i getRandomPosition();
		FoodType getRandomFoodType();

		bool isValidPosition(std::vector<sf::Vector2i> position_data, sf::Vector2i food_position);

		void destroyFood();
		void updateElapsedDuration();
		void handleFoodSpawning();
		void reset();

	public:
		FoodService();
		~FoodService();

		void initialize();
		void update();
		void render();

		void startFoodSpawning();
		void stopFoodSpawning();
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

	FoodService::FoodService() : random_engine(random_device())
	{
		current_food_item = nullptr;
	}

	FoodService::~FoodService()
	{
		destroyFood();
	}

	void FoodService::initialize()
	{
		elapsed_duration = spawn_duration;
	}

	void FoodService::update()
	{
		if (current_spawning_status == FoodSpawningStatus::ACTIVE)
		{
			updateElapsedDuration();
			handleFoodSpawning();
		}

		if (current_food_item) current_food_item->update();
	}

	void FoodService::render()
	{
		if (current_food_item) current_food_item->render();
	}

	void FoodService::startFoodSpawning()
	{
		current_spawning_status = FoodSpawningStatus::ACTIVE;

		cell_width = ServiceLocator::getInstance()->getLevelService()->getCellWidth();
		cell_height = ServiceLocator::getInstance()->getLevelService()->getCellHeight();
	}

	void FoodService::stopFoodSpawning()
	{
		current_spawning_status = FoodSpawningStatus::IN_ACTIVE;
		destroyFood();
		reset();
	}

	FoodItem* FoodService::createFood(sf::Vector2i position, FoodType type)
	{
		FoodItem* food = new FoodItem();
		food->initialize(position, cell_width, cell_height, type);
		return food;
	}

	void FoodService::spawnFood()
	{
		current_food_item = createFood(getValidSpawnPosition(), getRandomFoodType());
	}

	sf::Vector2i FoodService::getValidSpawnPosition()
	{
		std::vector<sf::Vector2i> player_position_data = ServiceLocator::getInstance()->getPlayerService()->getCurrentSnakePositionList();
		std::vector<sf::Vector2i> elements_position_data = ServiceLocator::getInstance()->getElementService()->getElementsPositionList();
		sf::Vector2i spawn_position;

		do spawn_position = getRandomPosition();
		while (!isValidPosition(player_position_data, spawn_position) || !isValidPosition(elements_position_data, spawn_position));

		return spawn_position;
	}

	sf::Vector2i FoodService::getRandomPosition()
	{
		// Co-ordinate distribution i.e. selecting random position for food.
		std::uniform_int_distribution<int> x_distribution(0, LevelModel::number_of_columns - 1);
		std::uniform_int_distribution<int> y_distribution(0, LevelModel::number_of_rows - 1);

		int x_position = static_cast<int>(x_distribution(random_engine));
		int y_position = static_cast<int>(y_distribution(random_engine));

		return sf::Vector2i(x_position, y_position);
	}

	FoodType FoodService::getRandomFoodType()
	{
		std::uniform_int_distribution<int> distribution(0, FoodItem::number_of_foods - 1);

		return static_cast<FoodType>(distribution(random_engine));
	}

	bool FoodService::isValidPosition(std::vector<sf::Vector2i> position_data, sf::Vector2i food_position)
	{
		for (int i = 0; i < position_data.size(); i++)
		{
			if (food_position == position_data[i]) return false;
		}
		return true;
	}

	void FoodService::destroyFood()
	{
		if (current_food_item) delete(current_food_item);
	}

	void FoodService::updateElapsedDuration()
	{
		elapsed_duration += ServiceLocator::getInstance()->getTimeService()->getDeltaTime();
	}

	void FoodService::handleFoodSpawning()
	{
		if (elapsed_duration >= spawn_duration)
		{
			destroyFood();
			reset();
			spawnFood();
		}
	}

	void FoodService::reset()
	{
		elapsed_duration = 0.f;
	}
}
```



**Fantastic job!** Now your kitchen is running smoothly, serving food at the right intervals. 🍽️⏳ 

But don't close up too soon because your customer, the snake, isn't eating yet.



![Wont Eat GIFs - Find & Share on GIPHY](/Full-Stack-Game-Development/images/c6dac29f9b1b9688.gif)



Don't worry, you'll handle that in the next chapter.



**See you there! 👋🏼**
