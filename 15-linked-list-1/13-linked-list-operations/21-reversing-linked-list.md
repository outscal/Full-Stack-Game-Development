What is reversing the link list?

What is reversing the linked list in the context of this game?



Well...

Snake moves, the snake drinks alcohol, and suddenly the tail node becomes the head node and snake starts moving in the opposite direction!

This is reversing!



![Snake Reverse](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__12_33_02.gif)

***Snake Reversed after consuming Alcohol***



## How to reverse A linked list


---

Have you reversed an array before?

To reverse an array, you pick the elements from 1 end and replace them with the elements from the other end.

So in an int array of size 5, data at index 0 will exchange positions with data at index 4, 1 with 3 and so on.



But with a linked list, you don't have to do this exchange of data. You only need to change, which node is pointing to which node.



![reversing in 2 nodes](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/664c357050602831d2c379d3/05_30_2024__12_23_35.gif)

***Reversing Linked List with 2 Nodes*** 

You see, initially, A was pointing at B, and B was pointing at NULL

After reversing, B is pointing at A, and A is pointing at NULL



Let's see how this can be implemented.



## Implementing LL Reversal using 3-POINTErs


---



![reversing LL](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/664c357050602831d2c379d3/05_30_2024__12_25_26.gif)

***Reversing a Linked List using 3 pointers ***



Look carefully at the image, there are 3 pointers

`cur_node`: Node which is being reversed

`next_node`: Node next to `cur_node`

`prev_node`: Node behind `cur_node`



Assume a LL: `A->B->C->D->NULL` 

Initially, the state of points will be:

```text
cur_node = head_node
prev_node = nullptr
next_node = nullptr
```



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_07_2024__11_24_59.png)





Logically, to reverse, the "*Current Node's Next Pointer*" should be set as "*Previous Node*" :



```text
cur_node->next = prev_node
```



But before doing this, 
you need to store the "*Next Node*" so that you don't lose it



```text
next_node = cur_node->next 
cur_node->next = prev_node
```



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_07_2024__11_46_21.gif)





**Current Node is Reversed!⬆️**



Now,

Since you have updated the next pointer of the current node (`cur_node->next`), you need to update the next node and move to the next node.

This can be done by:

```text
prev_node = cur_node
cur_node = next_node
```



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_07_2024__11_32_45.png)



Now, when you implement this approach in a loop, you can reverse the entire Linked List

Here is the code:

```cpp
Direction SingleLinkedList::reverse()
{
    Node* cur_node = head_node;
    Node* prev_node = nullptr;
    Node* next_node = nullptr;

    while (cur_node != nullptr)
    {
        next_node = cur_node->next;
        cur_node->next = prev_node;

        prev_node = cur_node;
        cur_node = next_node;
    }

    head_node = prev_node;

    //UPDATE THE DATA TO MATCH REVERSAL
    //RETURN THE NEW DIRECTION OF MOVEMENT
}
```



Here are some things to notice in the above code:

1. You need to return the new direction of movement
2. You need to reverse the direction of movement for each body part



## Reversing Direction of Movement


---

To understand how to reverse the direction of movement, you need to revise how movement works!

```cpp
void SnakeController::delayedUpdate()
{
		//...some other code
		updateSnakeDirection();
		processSnakeCollision();

		if(current_snake_state != SnakeState::DEAD)
			moveSnake();
		//....some other code
	}
}
```



![Direction->Collision->Move](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_10_2024__06_26_12.png)



In every frame, the direction is updated first, then the collision is detected, and at the end, the snake moves.

This cycle will play an important role in reversing the direction.

Let's see it frame by frame...



![Reversing: Frame 0](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_10_2024__05_37_22.png)

**FRAME 0**: *Snake is 1 step away from food*



![Reversing: Frame 1](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_10_2024__05_38_23.png)

**FRAME 1:** *Snake's head overlaps the food*



In **FRAME 2**, 

3 things will happen:

1. ![Reversing: Frame 2a](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_10_2024__05_40_29.png)
  
  **FRAME 2a:** *Direction will update*
2. ![ll](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/06_10_2024__07_55_19.png)
  
  **FRAME 2b:** *Collision will be detected with *`*ALCHOHOL*`*, *
  *which will reverse the Linked List and snake's direction*
3. ![Reversing: Frame 2c](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/06_10_2024__05_47_06.png)
  
  **FRAME 2c:** *The snake will move in the reverse direction*



Now, Look carefully at Image **2a)** again: 

Look at node `C` in this frame below:

![ll](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/06_10_2024__07_58_19.png)



If you directly reverse this Node's direction, it'll move in a wrong direction. 



All right, so you cannot ***directly reverse the current direction of ***all Body Parts.

How will you then correctly reverse the direction of all body parts in such a way that snake starts to move in the in the reverse direction? 

What you basically want is to change all the node directions in **Frame 2a** to **Frame 2b**.



Now look carefully at **Frame 1** 

If you directly reverse the direction of all body parts in **Frame 1**, then the snake will move in the correct direction!



So, if you have to move the snake in the current frame, then **you have to reverse its direction from the LAST FRAME!** 

Which means that **you have to reverse the PREVIOUS DIRECTION of all Body Parts!**



## Storing Previous Direction


---

Every `BodyPart` will store it's previous direction!



> **TODO: BodyPart** 
> ✅ Create `Direction previous_direction` in `BodyPart.h` 
> ✅ Create a getter function: `Direction getPreviousDirection()` 
> ✅ Inside `setDirection()`, before updating `direction`, store the `direction` in `previous_direction`



Click here to see `BodyPart`'s updated `setDirection()` 

```cpp
void BodyPart::setDirection(Direction direction)
{
	previous_direction = this->direction;
	this->direction = direction;
}
```





## Implementing Reverse Direction


---

Every `BodyPart` has its `previous_direction` 

Now, you need a way to calculate the opposite of this `previous_direction` 



> **TODO: SingleLinkedList** 
> ✅ Create `Direction SingleLinkedList::getReverseDirection(Direction reference_direction),` and inside it, return the opposite direction of `reference_direction`



Finally, to reverse direction, you have to traverse through all `Node`s and for each `BodyPart`, take its previous direction, reverse it and set it as the new direction



> **TODO: SingleLinkedList** 
> ✅ Create and implement `void SingleLinkedList::reverseNodeDirections()`, inside it, traverse through all `Node`s and for each `BodyPart`, take its `previous_direction`, reverse it using `getReverseDirection()` and set it as the new direction
> ✅ Inside `reverse()`,  call `reverseNodeDirections()` and return `head_node->body_part.getDirection()`



Click here to see `SingleLinkedList`'s `reverseNodeDirections()` 

```cpp
void SingleLinkedList::reverseNodeDirections()
{
    Node* curr_node = head_node;
    
    while (curr_node != nullptr) 
    {
        curr_node->body_part.setDirection(getReverseDirection(curr_node->body_part.getPreviousDirection()));
        curr_node = curr_node->next;
    }
}
```





Click here to see `SingleLinkedList`'s `reverse()` 

```cpp
Direction SingleLinkedList::reverse()
{
    Node* cur_node = head_node;
    Node* prev_node = nullptr;
    Node* next_node = nullptr;

    while (cur_node != nullptr)
    {
        next_node = cur_node->next;
        cur_node->next = prev_node;

        prev_node = cur_node;
        cur_node = next_node;
    }

    head_node = prev_node;

    reverseNodeDirections();
    return head_node->body_part.getDirection();
}
```





Woah!

You've made a lot of progress in this chapter...

In the next and last, you will bring these functionalities to life by calling them when food is consumed!

**See you there👋🏼!**
