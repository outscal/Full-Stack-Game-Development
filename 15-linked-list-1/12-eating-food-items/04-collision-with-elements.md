> ***Till now obstacles were nothing but an illusion....***
> ***But now they will become the real threat!***



## How to detect collision with an element or obstacle?


---



To detect collision you will basically check if the Snake's head is at the same location as an element

But...

Do you remember while creating collision detection with `BodyPart`, you checked 2 positions

1. Head's current position
2. Head's next position



For the same reason, you will have to check for collision with both of these locations



## Implementing Collision Detection with Elements


---

Since `ElementService` has the list of all the obstacles, the main collision check will be done inside `ElementService` 



> **TODO: **`**ElementService**`** **
> ✅ Create `bool ElementService::processElementsCollision(LinkedList::Node* head_node)` 
> ✅ Inside it, check for collision of each obstacle with Snake's head. Return `true` when collided else return `false`



Click here to see `ElementService`’s `processElementsCollision()` 

```cpp
bool ElementService::processElementsCollision(LinkedList::Node* head_node)
{
	for (int i = 0; i < obstacle_list.size(); i++)
	{
		if (obstacle_list[i]->getObstaclePosition() == head_node->body_part.getNextPosition() ||
			obstacle_list[i]->getObstaclePosition() == head_node->body_part.getPosition())
		{
			return true;
		}
	}

	return false;
}
```





## Using Element Collision to detect Death


---

Now, you can check if the snake has collided inside `SnakeController` and do the same things that you did when it collided with iteseld

That is, change the state to `DEAD` and play the death sound 



> **TODO: **`**SnakeController**`** **
> ✅ Use `ElementService::processElementsCollision()` inside `SnakeController::processElementsCollision()` to detect collision. If collision happens, change the state to `DEAD` and play the death sound



Click here to see `SnakeController`’s `processElementsCollision()`

```cpp
void SnakeController::processElementsCollision()
{
	ElementService* element_service = ServiceLocator::getInstance()->getElementService();

	if (element_service->processElementsCollision(single_linked_list->getHeadNode()))
	{
		current_snake_state = SnakeState::DEAD;
		ServiceLocator::getInstance()->getSoundService()->playSound(SoundType::DEATH);
	}
}
```





Good!

Now your snake can die in Level 2!



> **TODO: **
> ✅ GO PLAY LEVEL 2!



**In the next section, your Snake will start detecting collisions with food!**🍔🤤
