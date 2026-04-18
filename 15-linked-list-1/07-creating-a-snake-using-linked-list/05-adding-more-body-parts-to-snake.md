**Building Snake's Body!!**



So, you've got a head, but a head alone does not make a snake. 🐍 

Let's add more body parts to bring your snake to life!



> **🔄 Recap Time! **

> ✅ You have `**BodyPart**` class that can create the individual segments of your snake (you used it to create the head, and now you'll use it to add more body parts).

> ✅ You have `**SingleLinkedList**` class that creates the body part and also manages it.

> ✅ You have `**SnakeController**` class that handles all snake-related and player-related tasks.



In this section, you'll create and implement all the necessary methods to add nodes (body parts) to the snake to spawn a complete snake.



When we say adding a body part, the question that comes to mind is, "*Where should the new node be added?*"

Think it logically that whenever a snake eats food, the body of the snake should increase but in which side?

Obviously, it would be on the opposite side of the head. The opposite side of the head of the snake is the tail.

So, the body should increase from the tail. Which means you have to **insert more nodes at the tail** of the snake.



## insert node at tail : The beginning


---



So, how does inserting a node at the tail work?

You should first know a few basic terms related to linked list:

- **Tail**: The "tail" in a linked list refers to the last node in the list, which is the opposite end of the linked list from the head.
- **Traversal: **It means visiting each node one by one, starting from the head or any node to the node you want to reach. This is similar to looping to all the elements of the array.


You know your snake is not just a single-element creature; it has multiple nodes connected to each other.

To insert a node at the end of the linked list, you first have to reach the end from the head.

To do so, you have to visit each node!

Starting from the head... all the way to the tail... hopping from node to node
one by one until you reach the end!

And that is called... TRAVERSAL🏃🏼‍♀️!



## TAIL


---

It is basically the node whose next pointer will always be `**nullptr**`.

If any node whose next pointer is not `**nullptr**` can never be referred to as the tail.



![Image](/Full-Stack-Game-Development/images/654f639298ccc52a.png)



In the above linked list, you can easily identify which node is the **Tail**.



## traversal


---

Node's next pointer can point to other nodes as well, so to reach till the tail you need to traverse the list from head till the tail.

To understand it have a look at this code snippet:

```cpp
cur_node = head_node;     // copy head_node to cur_node
while (cur_node->next != nullptr) {   // Traverse the list using cur_node
			cur_node = cur_node->next;
}
```



This loop visits each node from the head to the node whose next pointer is `**nullptr**`. Let's break it down:



![Image](/Full-Stack-Game-Development/images/0208b9359413092a.gif)



Look at the above video, 

- You begin at the head node (`cur_node = head_node`).
- In each iteration, `cur_node` copies the reference of its `next`.
- The loop continues until it finds the last node, whose `next` is `nullptr`.



> **💡Pro Tip:** 
>   Using a copy of the `head_node` (i.e., `cur_node`) ensures that the original `head_node` remains unchanged, preserving the reference
>   to the start of the linked list.



This whole operation takes **O(N)** time complexity by visiting each node, just like array.



## joining two node


---

Insertion, in other words, means joining. But how does joining in a linked list work?

Imagine you have two nodes **A** & **B**. Both are pointing to `**nullptr**` right now.



![Image](/Full-Stack-Game-Development/images/178eef2d71099152.png)



You can easily join two nodes by just pointing to the `next` of node **A** to the reference of node **B**.

i.e. `**A->next = B**`

This connects node **A** to node **B**, creating a sequence in the linked list. 



![Image](/Full-Stack-Game-Development/images/12d99700f73e38a4.png)



This operation takes only **O(1)** time complexity.



## insert node at tail : part two


---

Now, you are ready to create a method that inserts a node at the tail.

You know the drill: create a new node, reach till the end, then point it to the new node. 



This is how it looks:

![Image](/Full-Stack-Game-Development/images/c66ef8ef0cdb73db.gif)

***Insertion at the Tail***



This method should:

- Create a new node (body part).
- Check whether the head is present (If not, update the head node to the newly created node, then initialize it according to default values).
- If the head is present, traverse till the end and join the new node. 
- Then, initialize it according to the position of the last node.



Okay, the first three points are simple, but what does the fourth one mean?

To do that, you need to go on another trip. (Ahh!! Still not making the `insertNodeAtTail()` method 😫)



## get new node's position


---

Every new node you add needs a position and direction!

And for that, you need a reference node!

Reference Node is a node that is used to calculate the Position and Direction of a new node.

It is the neighbour node! It connects the new node with the entire snake!





**Here's the code snippet:**

```cpp
sf::Vector2i SingleLinkedList::getNewNodePosition(Node* reference_node)
{
	// Extract direction and position for new node calculation
	Direction reference_direction = reference_node->body_part.getDirection();
	sf::Vector2i reference_position = reference_node->body_part.getPosition();

 // Calculate new position based on reference node's direction
	switch (reference_direction)
	{
	case Direction::UP:
		return sf::Vector2i(reference_position.x, reference_position.y - 1);     //Decreases the y-coordinate by 1 (moves up)
		break;
	case Direction::DOWN:
		return sf::Vector2i(reference_position.x, reference_position.y + 1);     //Increases the y-coordinate by 1 (moves down)
		break;
	case Direction::LEFT:
		return sf::Vector2i(reference_position.x + 1, reference_position.y);    //Increases the x-coordinate by 1 (moves left).
		break;
	case Direction::RIGHT:
		return sf::Vector2i(reference_position.x - 1, reference_position.y);  //Decreases the x-coordinate by 1 (moves right).
		break;
	}

	return default_position;
}
```



> **TODO: **`**SingleLinkedList**`
> ✅ Create and implement `getNewNodePosition()` as above



## insert node at tail : the final chapter


---

Without any delay, start creating the `insertNodeAtTail()` method.



#### Here's the code snippet:

```cpp
void SingleLinkedList::insertNodeAtTail() {
    Node* new_node = createNode();
    Node* cur_node = head_node;

    if (cur_node == nullptr) {       // If the list is empty, set the new node as the head
        head_node = new_node;
        new_node->body_part.initialize(node_width, node_height, default_position, default_direction);
        return;
    }

    // Traverse to the end of the list 
    while (cur_node->next != nullptr) {
        cur_node = cur_node->next;
    }

    // Attach the new node at the end
    cur_node->next = new_node;
    new_node->body_part.initialize(node_width, node_height, getNewNodePosition(cur_node), cur_node->body_part.getDirection());
}
```



> `cur_node->body_part.getDirection()` retrieves the current node's direction, which also becomes the new node's direction. This maintains the direction of the snake's movement.



Although adding a node to the tail is a simple **O(1)** operation, reaching the tail itself takes **O(N)** time due to traversal. 

So, what is the overall time complexity of adding at the tail? Yep, **O(N)** it is.



Here, you are creating the head as well, so there is no need for `createHeadNode()` method.



> **TODO: **`**SingleLinkedList**`
> ✅ Create and impelement `insertNodeAtTail()` 
> ✅ Remove `createHeadNode()`





## spawning whole snake


---

To spawn the whole snake at the start of the game.

Loop till `initial_snake_length` and start inserting node at the tail.



#### Here's the code snippet:

```cpp
void SnakeController::spawnSnake() {
    for (int i = 0; i < initial_snake_length; i++) {
        single_linked_list->insertNodeAtTail();     // Insert nodes at tail to create the initial snake
    }
}
```



> **TODO: **`**SnakeController**`
> ✅ Update `spawnSnake()` as above





**TEST YOUR CODE!!**

Test these changes in the code to ensure everything works correctly. Make sure the snake head and all body parts are **rendered**.

Umm... rendered? 🤔

Update this code in `render()`:

```cpp
void SingleLinkedList::render() {
    Node* cur_node = head_node;

    while (cur_node != nullptr) {     // Traverse through the linked list and render each node's body part
        cur_node->body_part.render();
        cur_node = cur_node->next;
    }
}

```



> **TODO: **`**SingleLinkedList**`
> ✅ Update `render()` as above



Now, you should see your snake with its body. 🤭



![Image](/Full-Stack-Game-Development/images/6f70a59fd0c9f2b5.gif)

***Inserting Node At Tail: Minion Edition *****😁**



**See you in the next section!👋🏼**
