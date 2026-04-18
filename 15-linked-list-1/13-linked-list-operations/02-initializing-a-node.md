```cpp
void BodyPart::initialize(float width, float height, sf::Vector2i pos, Direction dir)
	{
		bodypart_width = width;
		bodypart_height = height;
		direction = dir;
		grid_position = pos;

		initializeBodyPartImage();
	}
```



Remember this code from `**BodyPart.cpp**`?



You need to call this function when creating a new node.

`Width` and `Height` are readily available, as they are static, the same for all `BodyPart`s



**How will you calculate the position and direction?**



## Calculating Position of a new node


---

![Healthy Food](/Full-Stack-Game-Development/images/63fec6a4063d2290.png)

***Junk Food (It will make your Snake fat)***



According to the game design, New Nodes can be added to the Snake's

1. Head
2. Tail
3. In-Between: Any other positions between Head and Tail

 

Now, how does this affect your code?



**Inserting at Head:** If you insert a node at the head, then the new Node's position will be the current Head's Next Position

**Inserting at Tail:** If you insert a node at the tail, then the new Node's position will be the current Head's previous position  

**Inserting In-between:** If you insert a node in-between then you'll have to move all the nodes to fit the new node in-between. If you want to insert a node at index 4, then the new node's position will be the same as the position of the node that is already at index 4 and then you'll shift the rest of the nodes.



To know where the operation is being done, you can create an Enum:

```cpp
enum class Operation
{
	HEAD,
	MID,
	TAIL,
};
```



> **TODO: **`**SingleLinkedList**` 
> ✅ Create the above `enum class Operation` inside `SingleLinkedList.h`



The signature for the function to calculate the new position should look like this: 

```cpp
sf::Vector2i SingleLinkedList::getNewNodePosition(Node* reference_node, Operation operation) { }
```



**Why do you need a Reference Node?**

Reference node is basically your neighbour node!'

If you are inserting a new node at the head, then the current head node will be passed as a reference node.

Similarly, if you are inserting at index 4, then the current node at index 4 will be passed as a reference node.



Also,

Didn't you create a function with the same name in **Creating a Snake Using Linked List?!** 

Of course, you did!

Well, it is of no use now. We are about to create something better.

You can just delete the old method! We are about to update it here!



Inside this new function, depending on the `Operation`, you have to return the following positions:

`**HEAD**`: Reference Node's Next Position

`**TAIL**`: Reference Node's Previous Position 



You already have a function to calculate the next position of a body part: `body_part.getNextPosition()` 

You have to create a function to calculate the previous position of the body part



## CALCULATING Previous position of a body part


---

If the Body Part is at `(10,10)` and it is moving in Right Direction, then what will be the next position?

`(10+1,10) = (11,10)` 

Now, the Body Part is at `(11,10)` and it is moving in the Right Direction, what will be the previous position?

`(10,10)`! 

and if the Body Part is at `(11,10)` and it is moving in the Left Direction, what will be the next position?

`(10,10)`! 



Think for a second...



Isn't the previous position the *'next position'* but in the opposite direction?

Is it hard to digest?

If yes, then take a moment, think of more examples, you'll see the pattern. 



Considering this logic, you can create the function to calculate the previous position of a body part.



> **TODO: **`**BodyPart**` 
> ✅ Create `sf::Vector2i BodyPart::getPrevPosition()` while considering the logic that previous position is the next position but in the opposite direction



Click here to see `BodyPart`'s `getPrevPosition()`

```cpp
sf::Vector2i BodyPart::getPrevPosition()
{
	switch (direction)
	{
	case Direction::UP:
		return getNextPositionDown();
	case Direction::DOWN:
		return getNextPositionUp();
	case Direction::RIGHT:
		return getNextPositionLeft();
	case Direction::LEFT:
		return getNextPositionRight();
	default:
		return grid_position;
	}
}
```





## Continuing Calculating THE Position of a new node


---



> **TODO: **`**SingleLinkedList**`  
> ✅ Create `sf::Vector2i SingleLinkedList::getNewNodePosition(Node* reference_node, Operation operation)` such that it returns Node's next position when Operation is at `HEAD` and returns Node's previous position when Operation is at `TAIL`. Ignore `MID` and return `default_position` as default
> ✅ Replace all uses of the old `**getNewNodePosition()**` with this new function and delete the old function



Click here to see `SingleLinkedList`'s `getNewNodePosition()` 

```cpp
sf::Vector2i SingleLinkedList::getNewNodePosition(Node* reference_node, Operation operation)
{
    switch (operation)
    {
    case Operation::HEAD:
        return reference_node->body_part.getNextPosition();
    case Operation::TAIL:
        return reference_node->body_part.getPrevPosition();
    }

    return default_position;
}
```



 



## Initializing a new node


---

To initialize a new node, you need to know where it is being added, so you can use `Enum Operation`

and you also need a reference node to know where to add the new node!

And you need a reference to the new node itself!



This is how the function for initializing the node should look:

```cpp
void SingleLinkedList::initializeNode(Node* new_node, Node* reference_node, Operation operation)
{
    //... code yet to be written
}
```



Inside this, you have to call: 

`new_node->body_part.initialize(/*Width*/, /*Height*/, /*Position*/, /*Direction*/)` 



You already have the variables for Width and Height: `node_width`, `node_height` 

For direction, you can directly pass the direction of the `reference_node` because each new node will just move in the direction of its reference node

And for the position, you have already created the function to calculate the position for a new node: `getNewNodePosition()`



But what if the reference node is `NULL`? It can definitely be a possibility, your code should always be prepared to handle null cases

What will you do in that case?

Well. in that case you can't use the reference node to know the new position or the direction, in that case you can directly pass the `default_position` and `default_direction` 



> **TODO: **`**SingleLinkedList**` 
> ✅ Create and implement `void SingleLinkedList::initializeNode(Node* new_node, Node* reference_node, Operation operation)` as discussed above



Click here to see `SingleLinkedList`'s `**initializeNode()**` 

```cpp
void SingleLinkedList::initializeNode(Node* new_node, Node* reference_node, Operation operation)
{
    if (reference_node == nullptr)
    {
        new_node->body_part.initialize(node_width, node_height, default_position, default_direction);
        return;
    }

    sf::Vector2i position = getNewNodePosition(reference_node, operation);

    new_node->body_part.initialize(node_width, node_height, position, reference_node->body_part.getDirection());
}
```





Done till here?

Good Job!



Now you have everything to insert a new node in the beginning, 
**So let's get to it!💪🏼**
