To move the snake, you need to move every body part, and every body part updates its position based on its direction so basically you need to update the entire linked list



![SnakeController and Single Linked List Movement Flow Chart](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_09_2024__12_21_31.png)



Here, `SnakeController` will take the input and update the `SingleLinkedList` with the latest direction and update the position.

`SingleLinkedList` will update the entire Linked List, i.e. all `BodyPart`s and each `BodyPart` will move itself.



## Updating Direction


---

On every step forward the snake takes, the `head` will move in the direction of user input and rest of the `BodyPart` will follow the `BodyPart` ahead of them.

For example: `A->B->C-NULL` 

![Body Part Frame Movement](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_04_2024__13_53_33.png)

***Snake Moving***

If `A` is moving LEFT, `B`'s is `UP,` and `C`'s `UP` 

In the next frame, `A` will move to `LEFT`, `B` will move `LEFT,` and C will move to `UP.` 

And in the next frame, each `BodyPart` will move to `LEFT.` 



The `HEAD` Node moves in the direction of Input, and the rest of the nodes follow the node ahead of them.



> **TODO: **`**SingleLinkedList**`` `
> ✅ Create `void SingleLinkedList::updateNodeDirection(Direction direction_to_set)`: Inside it, write the logic such that the HEAD node updates with the direction of input, i.e. `direction_to_set` and the rest nodes are updated with the direction of the node ahead of them



Click here to see `SingleLinkedList`'s `updateNodeDirection()` 

```cpp
void SingleLinkedList::updateNodeDirection(Direction direction_to_set)
{
	Node* cur_node = head_node;

	while (cur_node != nullptr)
	{
		Direction previous_direction = cur_node->body_part.getDirection();
		cur_node->body_part.setDirection(direction_to_set);
		direction_to_set = previous_direction;
		cur_node = cur_node->next;
	}
}
```





## Updating  Position


---

Finally, this is where the snake moves!



> **TODO: **`**SingleLinkedList**`` `
> ✅ Create `void SingleLinkedList::updateNodePosition()`: Inside it, write the logic to traverse through all nodes and call `updatePosition()` of each `BodyPart`



Click here to see `SingleLinkedList`'s `updateNodePosition()` 

```cpp
void SingleLinkedList::updateNodePosition()
{
	Node* cur_node = head_node;

	while (cur_node != nullptr)
	{
		cur_node->body_part.updatePosition();
		cur_node = cur_node->next;
	}
}
```





## Moving in Snake Controller


---

Current `SnakeController`'s `update()` 

```cpp
void SnakeController::update()
	{
		switch (current_snake_state)
		{
		case SnakeState::ALIVE:
			processPlayerInput();
			updateSnakeDirection();
			processSnakeCollision();
			moveSnake();
			break;

		case SnakeState::DEAD:
			handleRestart();
			break;
		}
	}
```



You already have the structure; let's use it!



> **TODO: SnakeController** 
> ✅ Call `SingleLinkedList`'s `updateNodeDirection()` inside `SnakeController::updateSnakeDirection()` and pass `current_node_direction`  as an argument
> ✅ Call `SingleLinkedList`'s `updateNodePosition()` inside `SnakeController::moveSnake()`
