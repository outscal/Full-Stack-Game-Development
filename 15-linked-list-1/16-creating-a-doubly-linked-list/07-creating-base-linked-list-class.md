It's time to create the base `LinkedList` class.



> **TODO:** 
> **✅** Create `LinkedList` class inside`LinkedListLib` folder.



Your base class will look a lot like the Singly Linked List (SLL) class, but it will not implement most of its functionalities. 

Instead, it will provide a common structure and shared functionalities that can be inherited and customized by other linked list classes.



Just like in SLL, your base linked list class will need an `Operation` enum to handle different operations.

**Enum **`**Operation**`

```cpp
enum class Operation
{
    HEAD,
    MID,
    TAIL,
};
```



> **TODO:** **LinkedList.h**
> **✅** Create `Operation` enum in  `LinkedList`





## Properties


---



Your base class will require properties similar to those of the SLL. These properties will help to manage the nodes and their attributes. 



> **TODO:** **LinkedList.h**
> **✅** Add the following properties in `protected` access specifier:
> `Node* head_node; `
> `float node_width; `
> `float node_height; `
> `sf::Vector2i default_position; `
> `Direction default_direction; `
> `int linked_list_size;`





## Functions


---



Now, let's outline the functions that your base class will have. 

We'll list these functions below, and of course, we trust that you're already familiar with their purposes. 

After all, why wouldn't we trust your knowledge? 



```cpp
class LinkedList
{
//...some other code
protected:
	virtual Node* createNode() = 0;
	sf::Vector2i getNewNodePosition(Node* reference_node, Operation operation);
	Direction getReverseDirection(Direction reference_direction);
	
		Node* findNodeAtIndex(int index);
	 void initializeNode(Node* new_node, Node* reference_node, Operation operation);
	 
	public:
	LinkedList();
	virtual ~LinkedList();
	
		void initialize(float width, float height, sf::Vector2i position, Direction direction);
	void render();
	
		virtual void insertNodeAtTail() = 0;
		virtual void insertNodeAtHead() = 0;
virtual void insertNodeAtMiddle() = 0;
virtual void insertNodeAtIndex(int index) = 0;

virtual void removeNodeAtTail() = 0;
virtual void removeNodeAtHead() = 0;
virtual void removeNodeAtMiddle() = 0;
virtual void removeNodeAt(int index) = 0;
virtual void removeAllNodes() = 0;
virtual void removeHalfNodes() = 0;

virtual Direction reverse() = 0;

virtual void updateNodePosition();
virtual void updateNodeDirection(Direction direction_to_set);

Node* getHeadNode();
int getLinkedListSize();
bool processNodeCollision();
void reverseNodeDirections();

std::vector<sf::Vector2i> getNodesPositionList();
	//...some other code
}
```



Don’t worry, we’ll still give you a brief overview to make sure we’re on the same page.

Let’s break down why these functions are important:

- `**createNode()**`**:** This function creates nodes specific to the type of linked list.
- `**getNewNodePosition()**`**:** Calculates the position of a new node relative to a reference node and an operation type.
- `**getReverseDirection()**`: 
- `**updateNodePosition() & updateNodeDirection()**`**:** Updates the position and direction of nodes, which is essential for moving elements in the linked list.
- `**findNodeAtIndex()**`**: **Finds a node at a specific index in the linked list.
- `**initializeNode()**`: Initializes a new node based on a reference node and an operation.
- `**initialize(), render()**`**:** Basic lifecycle functions to set up and render the linked list.
- **Pure Virtual Insert and Remove Functions:** These virtual functions must be implemented by derived classes to handle inserting and removing nodes at various positions.
- `**reverse()**`**:** A function to reverse the linked list.
- `**processNodeCollision()**`**:** Handles collision detection among nodes.
- `**reverseNodeDirections()**`**:** Helper function to reverse the direction of node according to previous node's previous direction.
- **Getters:** Functions to retrieve the head node, the linked list size, and all nodes' positions.



Some functions in our base class are marked as `virtual`. 
What does it mean??



> **💡 PROTIP:** The `virtual` keyword allows a function to be overridden in any derived class. This is crucial for creating flexible and reusable code. Refer to Space Invaders **Method Overriding** content to know more about `virtual` function.



Implement one more function, which requires discussion before declaration.

It is none other than `findMiddleNode()` , finding the middle node is a common operation that can be efficiently implemented in the base class.



```cpp
int LinkedList::findMiddleNode()
{
    Node* slow = head_node;
    Node* fast = head_node;
    int midIndex = 0;  // This will track the index of the middle node.

    // Move fast pointer at 2x speed and slow pointer at 1x speed.
    while (fast != nullptr && fast->next != nullptr) {
        slow = slow->next;
        fast = fast->next->next;
        midIndex++;
    }

    // Now, slow is at the middle node
    return midIndex;
}
```



The `findMiddleNode()` function uses two pointers, `slow` and `fast`, starting at the head. `slow` moves one node at a time, and `fast` moves two nodes at a time. When `fast` reaches the end, `slow` is at the middle. The function returns the middle node's index, tracked by `midIndex`, finding the middle efficiently in one pass.



> **TODO:** **LinkedList.h**
> **✅** Create all functions listed above.
> **✅** Create the `findMiddleNode()` in the base class.



You are all set with your `**LinkedList**` base class. 



**Click here to see **`LinkedList.h````cpp
#pragma once
#include <SFML/System/Vector2.hpp>
#include "LinkedListLib/Node.h"
#include <vector>

namespace LinkedListLib
{
	enum class Operation
	{
		HEAD,
		MID,
		TAIL,
	};

	class LinkedList
	{
	protected:
		Node* head_node;

		float node_width;
		float node_height;

		sf::Vector2i default_position;
		Direction default_direction;

		int linked_list_size;

		virtual Node* createNode() = 0;
		sf::Vector2i getNewNodePosition(Node* reference_node, Operation operation);
		Direction getReverseDirection(Direction reference_direction);

		int findMiddleNode();
		Node* findNodeAtIndex(int index);
		void initializeNode(Node* new_node, Node* reference_node, Operation operation);

	public:
		LinkedList();
		virtual ~LinkedList();

		void initialize(float width, float height, sf::Vector2i position, Direction direction);
		void render();

		virtual void insertNodeAtTail() = 0;
		virtual void insertNodeAtHead() = 0;
		virtual void insertNodeAtMiddle() = 0;
		virtual void insertNodeAtIndex(int index) = 0;

		virtual void removeNodeAtTail() = 0;
		virtual void removeNodeAtHead() = 0;
		virtual void removeNodeAtMiddle() = 0;
		virtual void removeNodeAt(int index) = 0;
		virtual void removeAllNodes() = 0;
		virtual void removeHalfNodes() = 0;

		virtual Direction reverse() = 0;

		virtual void updateNodePosition();
		virtual void updateNodeDirection(Direction direction_to_set);

		Node* getHeadNode();
		int getLinkedListSize();
		bool processNodeCollision();
		void reverseNodeDirections();

		std::vector<sf::Vector2i> getNodesPositionList();
	};
}
```



Now that you understand your base `**LinkedList**` class, it's time for an assignment section. Where you will implement all these methods, you can take reference from `**SingleLinkedList**` class as all the base class methods have the same logic as Single Linked List.



**Happy coding! 👋**
