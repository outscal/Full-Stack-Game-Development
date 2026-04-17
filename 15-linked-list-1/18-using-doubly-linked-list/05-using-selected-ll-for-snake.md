Now it is time to use both the Linked Lists to play the game.

In this section, you will write the complete code to use the UI Menus to select the Level Number and Linked List type and play the game.



## How to Select a Linked List?


---

![Flow- Creating Desired Linked List](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__10_49_54.png)

***Flow for creating desired Linked List***



1. After selecting a Linked List Type in the Linked List Selection UI Screen, `LevelService` will be informed about the type of linked list to use
2. Level Service will tell `PlayerService` to spawn the player according to the linked list type
3. `PlayerService` will use `SnakeController` to create the `LinkedList` and Spawn the snake



Let's go the bottom-up approach and start with Snake Controller



## Snake Controller


---

![Linked List Inheritance Tree](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__10_50_36.png)

***Linked List Inheritance Tree***



To use both the LLs, you can create properties of both `SingleLinkedList` and `DoubleLinkedList` 

But, in future, what if you had seven different types of Linked Lists? Will you create properties for all of them and then write separate code to handle all of them?



Here is where the power of Inheritance kicks in!



Since all the functions are declared in the base class, you can easily use a single property of base class to handle both types of Linked Lists!

How?

This is how!

```cpp
void SnakeController::createLinkedList(LinkedListType level_type)
{
	switch (level_type)
	{
	case LinkedListType::SINGLE_LINKED_LIST:
		linked_list = new SingleLinkedList();
		break;
	case LinkedListType::DOUBLE_LINKED_LIST:
		linked_list = new DoubleLinkedList();
		break;
	}
}
```



But see, to implement this, you need a property of the base class and the old property `single_linked_list` is useless!

So, your code will break, but fixing it is not a mammoth of a task, you can easily fix it!



> **TODO: **`**SnakeController**` 
> ✅ Create a new property `LinkedList* linked_list` and delete the old `single_linked_list` 
> ✅ Modify the `createLinkedList()` function according to the above code
> ✅ Remove `createLinkedList()` call from the constructor
> ✅ Replace all instances of using `single_linked_list`  with `linked_list`



See, earlier you were calling `createLinkedList()` in constructor, so the Linked List was always created before calling `initialize()` but now you'll call `createLinkedList()` manually, so you need to make sure the initialization of the Linked List happens after the creation.

What is the solution for this? Well...



> **TODO: **`**SnakeController**` 
> ✅ Create a new function  `void SnakeController::initializeLinkedList()` and move all the functionality of initializing the Linked List from `initialize()` to `initializeLinkedList()` 
> ✅ Call `initializeLinkedList()` at the end of `createLinkedList()` 
> ✅ `initialize()` should be empty



Click here to see `SnakeController`'s `initializeLinkedList()` 

```cpp
void SnakeController::initializeLinkedList()
{
	float width = ServiceLocator::getInstance()->getLevelService()->getCellWidth();
	float height = ServiceLocator::getInstance()->getLevelService()->getCellHeight();

	reset();
	linked_list->initialize(width, height, default_position, default_direction);
}
```



Click here to see `SnakeController`'s `createLinkedList()` 

```cpp
void SnakeController::createLinkedList(LinkedListType level_type)
{
	switch (level_type)
	{
	case LinkedListType::SINGLE_LINKED_LIST:
		linked_list = new SingleLinkedList();
		break;
	case LinkedListType::DOUBLE_LINKED_LIST:
		linked_list = new DoubleLinkedList();
		break;
	}

	initializeLinkedList();
}
```



Click here to see `SnakeController`'s `initialize()` 

```cpp
void SnakeController::initialize() { }
```





`**SnakeController**`**: DONE ✅** 



## Player Service


---

`spawnPlayer()` needs to be updated, it needs to be aware of the type of Linked List that has to be created 



`**OLD spawnPlayer()**` 

```cpp
void PlayerService::spawnPlayer()
{
	snake_controller->spawnSnake();
}
```



This needs to be updated, you are created `SnakeController::createLinkedList(LinkedListType level_type)` 

You need to call it inside  

`PlayerService::spawnPlayer()` but then it should be modified to:

 `**PlayerService::spawnPlayer(LinkedListType level_type)**` 



> **TODO: **`**PlayerService**` 
> ✅ Update `spawnPlayer()` by `**LinkedListType level_type**` taking  as a parameter
> ✅ Inside it, call `snake_controller->createLinkedList(level_type)` before calling `snake_controller->spawnSnake()`



Click here to see how `PlayerService`'s `spawnPlayer()` should look 

```cpp
void PlayerService::spawnPlayer(LinkedListType level_type)
{
	snake_controller->createLinkedList(level_type);
	snake_controller->spawnSnake();
}
```





## Level Service


---

**CODE from **`**LevelSelectionUIController**`** **

```cpp
void LevelSelectionUIController::levelOneButtonCallback()
{
    ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::BUTTON_CLICK);
    GameService::setGameState(GameState::GAMEPLAY);
    ServiceLocator::getInstance()->getLevelService()->createLevel(Level::LevelNumber::ONE);
}
```



See, in the above function, `LevelService::createLevel()` function only needed to know the `LevelNumber` 

But now, there is `LevelNumber` and `LinkedListType`. Also, this data has to be extracted from 2 different menus: `LevelSelectionUI` and `LinkedListSelectionUI` 

The best practise is to break it down

1. Function for storing current level number
2. Function for creating Level by taking `LinkedListType` as an argument



> **TODO: **`**LevelService**` 
> ✅ Create a property: `LinkedListType current_linked_list_type` 
> ✅ Create `void LevelService::setCurrentLevelNumber(LevelNumber level_to_load)` 
> ✅ Inside it, set `current_level = level_to_load` 
> 
> ✅ Modify `createLevel()` to take `LinkedListTypelinked_list_type` 
> ✅ Inside it, set `current_linked_list_type = linked_list_type` and call rest of the function as they were



Click here to see `LevelService`'s `setCurrentLevelNumber()` and `createLevel()` 

```cpp
void LevelService::setCurrentLevelNumber(LevelNumber level_to_load)
{
	current_level = level_to_load;
}

void LevelService::createLevel(LinkedListType linked_list_type)
{
	current_linked_list_type = linked_list_type;
	spawnLevelElements(current_level);
	spawnFood();
	spawnPlayer();
}
```





## Level Selection UI Controller


---

**OLD CODE**

```cpp
void LevelSelectionUIController::levelOneButtonCallback()
{
    ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::BUTTON_CLICK);
    GameService::setGameState(GameState::GAMEPLAY);
    ServiceLocator::getInstance()->getLevelService()->createLevel(Level::LevelNumber::ONE);
}
```



See this old code, needs 2 changes

1. The `GameState` after Level Selection will be `LINKED_LIST_SELECTION` 
2. Rather than calling `LevelService::createLevel()`, `LevelService::setCurrentLevelNumber()` needs to be called



> **TODO: **`**LevelSelectionUIController**` 
> ✅ Update the level button callback functions for both Level 1 and 2 to change the `GameState` to  `LINKED_LIST_SELECTION` and instead of calling `LevelService::createLevel()`call `LevelService::setCurrentLevelNumber()`



Click here to see `LevelSelectionUIController`'s  level button callback functions

```cpp
void LevelSelectionUIController::levelOneButtonCallback()
{
    ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::BUTTON_CLICK);
    GameService::setGameState(GameState::LINKED_LIST_SELECTION);
    ServiceLocator::getInstance()->getLevelService()->setCurrentLevelNumber(Level::LevelNumber::ONE);
}

void LevelSelectionUIController::levelTwoButtonCallback()
{
    ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::BUTTON_CLICK);
    GameService::setGameState(GameState::LINKED_LIST_SELECTION);
    ServiceLocator::getInstance()->getLevelService()->setCurrentLevelNumber(Level::LevelNumber::TWO);
}
```





## Linked List Selection UI Controller


---

You see, you must have created empty functions in `LinkedListSelectionUIController`:  `singleLinkedListButtonCallback()` and `doubleLinkedListButtonCallback()` 



Inside these functions, you have to do 3 things:

1. Play button click sound
2. Change `GameState` to `GAMEPLAY` 
3. Call `LevelService`'s `createLevel()` and has the correct `LinkedListType` 



> **TODO: **`**LinkedListSelectionUIController()**`** ** 
> ✅ Implement `singleLinkedListButtonCallback()` and `doubleLinkedListButtonCallback()` as discussed above



Click here to see `**LinkedListSelectionUIController**`'s `singleLinkedListButtonCallback()` and `doubleLinkedListButtonCallback()` 

```cpp
void LinkedListSelectionUIController::singleLinkedListButtonCallback()
{
    ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::BUTTON_CLICK);
    GameService::setGameState(GameState::GAMEPLAY);
    ServiceLocator::getInstance()->getLevelService()->createLevel(LinkedListType::SINGLE_LINKED_LIST);
}

void LinkedListSelectionUIController::doubleLinkedListButtonCallback()
{
    ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::BUTTON_CLICK);
    GameService::setGameState(GameState::GAMEPLAY);
    ServiceLocator::getInstance()->getLevelService()->createLevel(LinkedListType::DOUBLE_LINKED_LIST);
}
```





**DONE!**
