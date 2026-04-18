![OG Snake Colliding with Itself](/Full-Stack-Game-Development/images/7210c9253ef71dd0.gif)

**OG Snake colliding with itself**



Snake collides with itself when its head overlaps another body part.



To calculate this collision, you need to check if any body part has the same grid position as the head

That should do the trick, right?



Well well well…

There is a catch to it, look at the above illustration carefully. 

The head doesn't actually overlap with a body part, it stops 1 step before the actual collision. That is done for the visual effect.



Let's implement the same feature in your game. Why?

Well, because you are a cool game dev and you do cool things!



## Implementing Body Collision


---

To implement this collision, you need to traverse through the entire linked list and check for each node if that node's next position is the same as the next predicted position of the head.



**How to calculate the next predicted position?** 

You have already created this function: `BodyPart::getNextPosition()` 



This feature will be implemented in `SingleLinkedList`  



> **TODO: **`**SingleLinkedList**`** **
> **✅ **Create `bool SingleLinkedList::processNodeCollision()`  
> ✅ Inside it, compare each node's next position with the head's next position; if they are the same, return true. Else, return false.
> Remember: There is no need to do anything if `head_node` is `nullptr`



Click here to see `SingleLinkedList`'s `processNodeCollision()` 

```cpp
bool SingleLinkedList::processNodeCollision()
{
	if (head_node == nullptr) return false;

	sf::Vector2i predicted_position = head_node->body_part.getNextPosition();

	Node* cur_node = head_node->next;
	while (cur_node != nullptr)
	{
		if (cur_node->body_part.getNextPosition() == predicted_position ) return true;
		cur_node = cur_node->next;
	}

	return false;
}
```





## Checking collision in Snake Controller


---

To check the collision in `SnakeController`, you have already created `processSnakeCollision()`

Just check for collision inside an if condition using `single_linked_list->processNodeCollision()` and set the `current_snake_state` to `DEAD` it true



> **TODO: **`**SnakeController**`** **
> **✅ **Inside `processSnakeCollision()`, check for collision using `single_linked_list->processNodeCollision()`  and if true, set the `current_snake_state` to `DEAD`



Click here to see `SnakeController`'s `processSnakeCollision()` 

```cpp
void SnakeController::processSnakeCollision()
{
	if (single_linked_list->processNodeCollision())
	{
		current_snake_state = SnakeState::DEAD;
	}
}
```





## I have a simple question...


---

```cpp
void SnakeController::delayedUpdate()
{
	elapsed_duration += ServiceLocator::getInstance()->getTimeService()->getDeltaTime();

	if (elapsed_duration >= movement_frame_duration)
	{
		elapsed_duration = 0.f;
		updateSnakeDirection();
		processSnakeCollision();
		moveSnake();
	}
}
```

In this function, what will happen when you detect a collision?

`moveSnake()` is called after `processSnakeCollision()`. This means that even though collision is detected, the snake might still move!

You need to fix it!



> **TODO: **`**SnakeController**`** **
> **✅ **Inside `delayedUpdate()`, after calling `processSnakeCollision()` check if the Snake is `ALIVE` and then only call `moveSnake()`



Nicely done!



In the upcoming sections...

the snake will be DELETED!



… and then respawned
