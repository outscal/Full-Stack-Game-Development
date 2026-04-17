All the functionalities you have created in this chapter...

It is time to call them now!



![Food Items with Functions](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__10_45_33.png)

***Food Functions***



> **TODO: **`**SnakeController**` 
> ✅ Update `SnakeController`'s `OnFoodCollected()` by calling the respective functions for each food. 
> While reversing direction, store the new direction in `current_snake_direction`



Click here to see `SnakeController`'s `OnFoodCollected()` 

```cpp
void SnakeController::OnFoodCollected(FoodType food_type)
{
	switch (food_type)
	{
	case FoodType::PIZZA:
		//Insert at TAIL
		single_linked_list->insertNodeAtTail();
		break;

	case FoodType::BURGER:
		//Insert at HEAD
		single_linked_list->insertNodeAtHead();
		break;

	case FoodType::CHEESE:
		//Insert at MIDDLE
		single_linked_list->insertNodeAtMiddle();
		break;

	case FoodType::APPLE:
		//Delete at HEAD
		single_linked_list->removeNodeAtHead();
		break;

	case FoodType::MANGO:
		//Delete at MIDDLE
		single_linked_list->removeNodeAtMiddle();
		break;

	case FoodType::ORANGE:
		//Delete at TAIL
		single_linked_list->removeNodeAtTail();
		break;

	case FoodType::POISION:
		//Delete half nodes
		single_linked_list->removeHalfNodes();
		break;

	case FoodType::ALCOHOL:
		//Reverse Direction
		current_snake_direction = single_linked_list->reverse();
		break;
	}
}
```





Finally!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

The chapter ends!



I understand that this chapter can be exhausting

But the good thing is... you have made it through!

Go out and celebrate!



You have a lot more to build!

Devs don't stop💪🏼🎮!
