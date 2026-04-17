## Understanding Food Collision


---

Collision with food is almost the same as collision with elements, but the difference is that different foods can have different effects

When the snake collides with obstacle, it DIES!

But when snake collides with a food, who knows what happens?

It can grow, it can shrink, it can be halved or it can even get drunk

Who know...



Since food can have so many different effects on the snake, the `SnakeController` needs to know which food it has collided with

And then it will act accordingly

The flow for this will look like this:

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__09_34_35.png)

`***SnakeController***`*** and ***`***FoodService***`*** Communication for Food Collision***



The question is, how will you implement this flow?

You need to check 2 things:

1. If the Snake's head has collided with a food
2. If yes, then what food type it has collided with



## Let's do some brainstorming...


---

**How will you implement the above flow?**



**APPROACH 1:** If the snake has collided with a then the food service can return the food type, and return null if there was no food, 
Then you can use a null check to check if there was a food and act according to the food's type.
But don't you think this is a little messy? This will make the code unreadable!



**APPROACH 2:** Create 2 different functions, 1 to check if collision is done, and another to check collision with which element. 
This approach works, and the code is also readable, but this can still be improved with just 1 function!



**HOW?**



Do you remember Passing Parameters with reference in a function? 

You have learnt this in Space Invaders



> 💡PROTIP: Pass by Reference 
> In C++, passing arguments by reference allows functions to directly modify the original values of variables, rather than working with copies. For example, to swap two integers:
> `void swap(int &a, int &b) { std::swap(a, b); }`



**APPROACH 3:** Create a function that returns a bool to tell if there was a collision, but it also takes a reference value of `FoodType` and it sets this value if there was a collision



The code for 3rd approach will look like this:

```cpp
bool FoodService::processFoodCollision(LinkedList::Node* head_node, FoodType& out_food_type)
{
	if (current_food_item && current_food_item->getFoodPosition() == head_node->body_part.getPosition())
	{
		out_food_type = current_food_item->getFoodType();
		return true;
	}

	return false;
}
```



> **TODO: **`**FoodService**`** **
> ✅ Create and implement `processFoodCollision()` using above code



## Handling Food Collision inside `SnakeController`


---



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/664c357050602831d2c379d3/05_31_2024__13_32_05.png)

***Flow for collision with food***



You can implement this logic using 2 functions in `SnakeController`:

1. `processFoodCollision()`: To detect food collision
2. `OnFoodCollected(FoodType food_type)`: To apply the effects of the food



This is how these functions will look:

```cpp
void SnakeController::processFoodCollision()
{
	FoodService* food_service = ServiceLocator::getInstance()->getFoodService();
	FoodType food_type;

	if (food_service->processFoodCollision(single_linked_list->getHeadNode(), food_type))
	{
		ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::PICKUP);

		food_service->destroyFood();
		OnFoodCollected(food_type);
	}
}

void SnakeController::OnFoodCollected(FoodType food_type)
{
	switch (food_type)
	{
	case FoodType::PIZZA:
		//Insert At Tail
		break;

	case FoodType::BURGER:
		//Insert At Head
		break;

	case FoodType::CHEESE:
		//Insert in Middle
		break;

	case FoodType::APPLE:
		//Delete at Head
		break;

	case FoodType::MANGO:
		//Delete at Middle
		break;

	case FoodType::ORANGE:
		//Delete at Tail
		break;

	case FoodType::POISION:
		//Delete half the snake
		break;

	case FoodType::ALCOHOL:
		//Reverse the snake
		break;
	}
}
```



> **TODO: **`**SnakeController**`** **
> ✅ Create and implement `processFoodCollision()` and `OnFoodCollected(FoodType food_type)` using above code



In the next chapter, you'll start implementing the code for all these effects!

**See you there!👋🏼**
