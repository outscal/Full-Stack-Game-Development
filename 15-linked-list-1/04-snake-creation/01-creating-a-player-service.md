> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your main branch called → [ `**Feature-2-Linked-List**` ]

> 

> Let’s start working on the new feature now!




---



**SO YOU HAVE YOUR LEVELS NOW!! GREAT!! **

But what's missing???



Your **Snake, **or call it your **Player, **as it is the main protagonist in your game, right?

From this chapter, you'll be making your boring and empty levels filled with your snake, roaming here and there!



![Image](/Full-Stack-Game-Development/images/a71e0c74e904bd72.gif)

**Have a look at your game**.



You create a snake, which is controlled by Player, but how?

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8c9f7b97-3438-434a-b8ca-0a53eb7262ea/0ac260ff-5451-432a-a8d7-c58765073efd/Untitled.png)

![](https://file.notion.so/f/f/8c9f7b97-3438-434a-b8ca-0a53eb7262ea/0ac260ff-5451-432a-a8d7-c58765073efd/Untitled.png?id=bc6e41b1-5651-4645-aa1d-3c9b710741c4&table=block&spaceId=8c9f7b97-3438-434a-b8ca-0a53eb7262ea&expirationTimestamp=1714953600000&signature=bvIjyQMIoQMb6mXSwVzbe1HfWe081epM3dgf9rr_rmk&downloadName=Untitled.png)


Have a look at the player architecture.

**PLAYER ARCHITECTURE**


---


![Image](/Full-Stack-Game-Development/images/9d05be7b55e402c5.png)

***Player Architecture***



To control the Snake game, you'll create a `SnakeController`. It can be seen as the **brain** of the Snake MVC.

But which Service should `SnakeController` be part of?

As you know, Player controls the Snake, so `PlayerService` would be a good choice.

`SnakeController` controls the snake and `PlayerService` controls everything that should be controller by the player. 🐍



> **TODO: PlayerService, SnakeController**
> **✅ **Create files for `SnakeController` and `PlayerService`. Follow proper folder structure and use `namespace Player` 
> ✅ Create empty lifecycle methods inside `SnakeController` and `PlayerService`




There are so many functionalities for your snake that you will be implementing, 
like moving 🚶, eating food 😋, passing through the border 🚶🧱🚶 , dying 💀, etc., which will be covered in details later.



For now, prioritize the initial step: spawning the snake on your screen. 



You'll start by connecting the `SnakeController` with `PlayerService`. 

In the `PlayerService`, you'll add a function specifically for spawning your player. This function should be triggered immediately after a level is loaded by `LevelService`.



> **TODO: PlayerService**
> ✅ Create a property `SnakeController* snake_controller` 
> ✅ Create a `private` method `void createController()`in `PlayerService` which will create an instance of `SnakeController` (Encapsulation😎) 
> ✅ Call all lifecycle methods of `snake_controller` 
> ✅ Don't forget to delete `snake_controller` 
> ✅ Create a `public` empty method `void spawnPlayer()`



## spawn player


---

Do you remember how you spawned your player in Space Invader?

When you click on play, your player should be spawned, but in Snake Game, the game actually starts when you choose your level.

This means the player should get spawned when you create your level.

In which method did you create your level in the previous chapter? 

`createLevel()` of `LevelService` right?

Now you know the drill, call `spawnPlayer()` from `createLevel()`



> **TODO: LevelService**
> ✅ Create an empty `private` method `void spawnPlayer()` and call it from `createLevel()`
> ✅ Call `PlayerService`'s `spawnPlayer()` from `LevelService`'s `spawnPlayer()`





Click here to see `LevelService`'s `spawnPlayer()````cpp
void LevelService::spawnPlayer()
{
	ServiceLocator::getInstance()->getPlayerService()->spawnPlayer();
}
```

**Click here to see **`PlayerService.h`** **```cpp
#pragma once

namespace Player
{
	class SnakeController;

	class PlayerService
	{
	private:
		SnakeController* snake_controller;

		void createController();
		void destroy();

	public:
		PlayerService();
		~PlayerService();

		void initialize();
		void update();
		void render();

		void spawnPlayer();
	};
}
```

**Click here to see **`PlayerService.cpp`** **```cpp
#include "Player/PlayerService.h"
#include "Player/SnakeController.h"

namespace Player
{
	PlayerService::PlayerService()
	{
		snake_controller = nullptr;

		createController();
	}

	PlayerService::~PlayerService()
	{
		destroy();
	}

	void PlayerService::createController()
	{
		snake_controller = new SnakeController();
	}

	void PlayerService::initialize()
	{
		snake_controller->initialize();
	}

	void PlayerService::update()
	{
		snake_controller->update();
	}

	void PlayerService::render()
	{
		snake_controller->render();
	}

	void PlayerService::spawnPlayer() { }

	void PlayerService::destroy()
	{
		delete (snake_controller);
	}
}
```



Further logic for spawning snakes will be covered later.

Before that, quickly integrate the `PlayerService` with the `ServiceLocator` 



> **TODO: ServiceLocator**
> ✅ Integrate `PlayerService`into `ServiceLocator` by creating its property
> ✅ Call all lifecycle methods of `PlayerService`.
> ✅ Create a getter function for `PlayerService`
> ✅ Delete the instance of `PlayerService` inside `destroy()`
> **Remember:** `update()` and `render()` of the `PlayerService` will be called only when the game state is `GAMEPLAY`



**See you in the next section👋🏼**
