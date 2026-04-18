**More Food, More Fun!!**



In this section, you'll enhance your gaming experience by spawning random food items at random positions. 



Remember how you placed mines randomly in Minesweeper using C++'s randomization tools? 💥

![](/Full-Stack-Game-Development/images/8dd5d19e6c0e3007.png)

***Randomly Placed Mines in Minesweeper***



Let's apply that same approach to spawn food items!

> 💡**PROTIP: Break down tasks into smaller parts. Together, they form a milestone. **🚀



![8 Steps to Break Down Tasks Into Manageable Pieces · Blog · ActiveCollab](https://activecollab.com/upload/blog/681/cover.png)



## **generate Randomness**


---



To generate random food items, you need to:

- **Generate Random Positions**: Create two random integers, and combine them into a `sf::Vector2i`, and verify the position.
- **Select Random Food Types**: Choose a random food type from a predefined list.



But how will you do this? 🤔



Take a moment, grab some water, and think about these questions:

1. How can you generate random numbers in C++? 
2. What tools or libraries will you use? 
3. Why do you think it's necessary to have both a random engine and a random device?



Please take a minute to think about it...



🕛...🕧...🕐...🕜...🕑...🕝...🕒...



Got your ideas? **Great!** 

Let's discuss the solution!



## **Flow Diagram to generate random food**



![ ](/Full-Stack-Game-Development/images/f831594660444114.png)

***Flow diagram of generating random food***



In the game, `LevelService` initiates food spawning. 

`FoodService` then manages the spawning process, creating random food at valid, unoccupied positions during the game loop. 

This process continues throughout the game.



## **What tools or libraries Will you use? **



Tools that you'll use are **random engine** and **random device**. 

You've already used them in Minesweeper, here's a little recap:

- **Random Device**: Generates a non-deterministic random number, often used to seed the random engine.
- **Random Engine**: Produces a sequence of pseudo-random numbers based on the seed from the random device.

Click [here](https://outscal.com/course/minesweeper-in-c-using-array/array/populating-board/implementing-board-populating-algorithm) for revision.



> **TODO: FoodService**
> **✅ **Create properties of random engine and random device
> `std::default_random_engine random_engine;`
> `std::random_device random_device;`



Create constructor of `FoodService:`

```cpp
FoodService::FoodService() : random_engine(random_device())
{
    current_food_item = nullptr;
}
```



💡**PROTIP:** Why Use the Initializer List?

The use of `random_engine` in the constructor's initializer list might seem unusual, but it's actually a common C++ technique. By initializing `random_engine` with `random_device()` in the initializer list, it ensures that the random number generator is seeded with a high-quality, random value right from the start. This approach is efficient and optimal because it directly initializes `random_engine` with the seed value returned by `random_device()`, ensuring that the generation of random numbers is properly set up for the entire lifespan of the `FoodService` object.



You have set up the random engine and a random device. Now, it's time to use them to generate random positions and food types.

But How?? What properties do you need for random positions?? 🤔



To generate a random position, you need a method that returns a `sf::Vector2i` of two random integers for the x and y positions for the food item within a specified range. 

*Range for x is (0, number_of_columns - 1) & for y is (0, number_of_rows - 1).*

After defining the distributions, random positions for both x and y positions will be created using the `random_engine`.

Simple, right? 😅



> 💡**PROTIP:** Use `std::uniform_int_distribution` to generate a random number within a specified range.



> **✅ TODO:** 
> Create `FoodService::getRandomPosition()`



**Click here to see **`getRandomPosition()````cpp
sf::Vector2i FoodService::getRandomPosition()
{
    // Coordinate distribution for selecting a random position for food
    std::uniform_int_distribution<int> x_distribution(0, LevelModel::number_of_columns - 1);
    std::uniform_int_distribution<int> y_distribution(0, LevelModel::number_of_rows - 1);

    int x_position = x_distribution(random_engine);
    int y_position = y_distribution(random_engine);

    return sf::Vector2i(x_position, y_position);
}

```



## **Generating Random Positions 🌍**


---



Next, to ensure the random position doesn't overlap with the snake or other game elements. You'll need:

1. **Snake Positions**: Fetch the current positions of all snake segments and store them.
2. **Element Positions**: Fetch the positions of obstacles and store them as well.

You'll use these lists to ensure food spawns only on valid, empty spaces.



Let's start with creating methods to access these position lists:



**Snake Positions List** 🐍

You need to know where the snake is to avoid hitting it with food. 

For that create a method `getNodesPositionList()` in`SingleLinkedList` to traverse the linked list to collect the positions of all body parts into a list and return it.



**Click to check the script of **`SingleLinkedList::getNodesPositionList()````cpp
std::vector<sf::Vector2i> SingleLinkedList::getNodesPositionList()
{
	std::vector<sf::Vector2i> nodes_position_list;

	Node* cur_node = head_node;

	while (cur_node != nullptr)
	{
		nodes_position_list.push_back(cur_node->body_part.getPosition());
		cur_node = cur_node->next;
	}

	return nodes_position_list;
}
```



> **TODO: **`**getNodesPositionList()**`
> **✅ **Create `SingleLinkedList::getNodesPositionList()` 
> **✅ **Create helper function `getCurrentSnakePositionList()` in `SnakeController` and `PlayerService`



**Click here to see **`SnakeController::getCurrentSnakePositionList()````cpp
std::vector<sf::Vector2i> SnakeController::getCurrentSnakePositionList()
{
	return single_linked_list->getNodesPositionList();
}
```

**Click here to see **`PlayerService::getCurrentSnakePositionList()````cpp
std::vector<sf::Vector2i> PlayerService::getCurrentSnakePositionList()
{
	return snake_controller->getCurrentSnakePositionList();
}
```



**Element Positions List **🧱

You also need to know where the obstacles are to avoid placing food on them.

Create a method `getElementsPositionList()` in `ElementService` to iterate through the obstacle list, fetch the position and store it in a separate list.



**Click to check the script of  **`ElementService::getElementsPositionList()````cpp
std::vector<sf::Vector2i> ElementService::getElementsPositionList()
{
	std::vector<sf::Vector2i> elements_position_list;

	for (int i = 0; i < obstacle_list.size(); i++)
	{
		elements_position_list.push_back(obstacle_list[i]->getObstaclePosition());
	}

	return elements_position_list;
}
```



> **TODO: **`getElementsPositionList()`
> **✅**Create `ElementService::getElementsPositionList()`
> **✅**Create helper function `sf::Vector2i Obstacle::getObstaclePosition()` that return `grid_position`



**Click here to see **`Obstacle::getObstaclePosition()````cpp
sf::Vector2i Obstacle::getObstaclePosition()
{
	return grid_position;
}
```



Now, with the snake and element positions, ensure the randomly generated food position doesn't overlap. 

Loop through both lists to check if the random position matches any. If it does, **generate a new position**.



> **TODO: **`isValidPosition()`
> **✅**Create `FoodService::isValidPosition(std::vector<sf::Vector2i> position_data, sf::Vector2i food_position)` to return a boolean by checking if the food position matches any in the list.



**Click here to see **`FoodService::isValidPosition()````cpp
bool FoodService::isValidPosition(std::vector<sf::Vector2i> position_data, sf::Vector2i food_position)
{
	for (int i = 0; i < position_data.size(); i++)
	{
		if (food_position == position_data[i]) return false;
	}
	return true;
}
```



Alright, now that you can generate and verify random positions, let's encapsulate this logic. 

Create `getValidSpawnPosition()` that will do the following things:

- Fetch and copy the snake's position list in `std::vector<sf::Vector2i> player_position_data`
- Fetch and copy the elements' position list in `std::vector<sf::Vector2i> elements_position_data`
- Loop to generate random `spawn_position` it until a valid, empty space is found that doesn't overlap with the snake or other elements. (You can use do-while loop)
- Then return this `spawn_position`



> **TODO: **`**getValidSpawnPosition()**`
> **✅**Create `FoodService::getValidSpawnPosition()`



**Click here to see **`FoodService::getValidSpawnPosition()````cpp
sf::Vector2i FoodService::getValidSpawnPosition()
{
	std::vector<sf::Vector2i> player_position_data = ServiceLocator::getInstance()->getPlayerService()->getCurrentSnakePositionList();
	std::vector<sf::Vector2i> elements_position_data = ServiceLocator::getInstance()->getElementService()->getElementsPositionList();
	sf::Vector2i spawn_position;

	do spawn_position = getRandomPosition();
	while (!isValidPosition(player_position_data, spawn_position) || !isValidPosition(elements_position_data, spawn_position));

	return spawn_position;
}
```



**Keep pushing yourself!! You're almost there!!**


![gif](/Full-Stack-Game-Development/images/b308a47d6ad657e3.gif)





## **Generating Random Food Types 🍕🍔🍣**


---



To generate a random food type, you only need a random number between `0` and `FoodItem::number_of_foods - 1`. 

Create a method `getRandomFoodType()` and implement the following:

```cpp
FoodType FoodService::getRandomFoodType()
{
	std::uniform_int_distribution<int> distribution(0, FoodItem::number_of_foods - 1);
	return static_cast<FoodType>(distribution(random_engine));
}
```



> 💡**PROTIP:** The distribution generates a random number, which is cast to the `FoodType` enum, ensuring a random food type is selected.



Now that you have methods to get a valid position and a random food type.

Update the `spawnFood` method to use them:

```cpp
void FoodService::spawnFood()
{
	current_food_item = createFood(getValidSpawnPosition(), getRandomFoodType());
}
```



**Congratulations! You did it! 🎉**

![gif](/Full-Stack-Game-Development/images/a907ef5cf8d8c010.gif)



You have now set up your game to spawn food items at random positions and of random types. 

Every time you start a level, random food will be generated at different locations, adding excitement and unpredictability to your game.



The next exciting challenge will be to spawn food at regular intervals, making the game fair to play. 

 

**See you in the next section! 👋🏼 **

(And remember, the food may be random, but your effort is **consistent**! 👍)
