Till now in both Array Jumper and Minesweeper, all services have acted like a communication bridge between Controller and ServiceLocator

But now things are about to change in this project!



In this project, Level Service will handle more responsibilities like communicating with other services. 

It is nothing but just a central component for managing all Level-related things in our game.



Before diving into the creating level, let's do the basic drill of connecting `LevelController` with `LevelService` 



> **TODO: LevelService**
> ✅ Create a property `LevelController* level_controller` 
> ✅ Call all lifecycle methods of `level_controller` 
> ✅ Don't forget to delete `level_controller`




Now, LevelService needs to know the `LevelNumber` of the current Level.
Why?
Well, because to create a level, LevelService has to communicate with the controller and other classes. And inform them about which level is being created.



> **TODO: LevelService**
> ✅ Create a property  `LevelNumber current_level`  
> ✅ Create `void createLevel(LevelNumber level_to_load)` and inside it, set `current_level = level_to_load`





Click here to see `LevelService.h` 

```cpp
#pragma once

namespace Level
{
    class LevelController;

    class LevelService
    {
    private:
        LevelController* level_controller;
        LevelNumber current_level;

        void createLevelController();
        void destroy();

    public:
        LevelService();
        ~LevelService();

        void initialize();
        void update();
        void render();

        void createLevel(LevelNumber level_to_load);
    };
}
```



Click here to see `LevelService.cpp` 

```cpp
#include "Level/LevelService.h"
#include "Level/LevelController.h"

namespace Level
{
	using namespace Global;

	LevelService::LevelService()
	{
		level_controller = nullptr;

		createLevelController();
	}

	LevelService::~LevelService()
	{
		destroy();
	}

	void LevelService::createLevelController()
	{
		level_controller = new LevelController();
	}

	void LevelService::initialize()
	{
		level_controller->initialize();
	}

	void LevelService::update()
	{
		level_controller->update();
	}

	void LevelService::render()
	{
		level_controller->render();
	}

	void LevelService::createLevel(LevelNumber level_to_load)
	{
		current_level = level_to_load;
	}

	void LevelService::destroy()
	{
		delete level_controller;
	}
}
```





Further logic for creating the level will be built as you create the controller and other services

Before that, let's just quickly integrate the `LevelService` with the `ServiceLocator` 



> **TODO: ServiceLocator**
> ✅ Integrate `LevelService` into `ServiceLocator` by creating its property, calling all its lifecycle functions, creating a getter function, and finally deleting it. Remember: only update and render the `LevelService` when the game's state is `GameState::GAMEPLAY`



**See you in the next section👋🏼**
