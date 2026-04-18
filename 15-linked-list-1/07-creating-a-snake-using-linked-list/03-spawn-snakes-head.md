You are all set to spawn your first snake!

But before you see your complete Snake, you must spawn the head first.

Think of the head as the first node of the linked list.



To spawn a head, you need a method to create a head node. 

And for that, we present you `createHeadNode()` but be aware it will expire soon. 🫡



`createHeadNode()` creates the `head_node` and initialize the node's body part.


Your `createHeadNode()` should look like this inside `SingleLinkedList` class

```cpp
void createHeadNode()
{
	head_node = createNode();
	head_node->body_part.initialize(node_width, node_height, default_position, default_direction);
	return;	
	}
```



> **TODO: **`**SingleLinkedList.cpp**`
> ✅ Create and implement `void createHeadNode()`



As we discussed before, the snake will use a linked list to represent all its body parts. 

But for that to happen, the snake will need a reference to a linked list that uses the Snake's Body Part as data.

(Refer to the block diagram in the previous material)

So go ahead and give your snake a Linked List to play with!



> **TODO : **`**SnakeController.h**`
> ✅ Add the following property and method and namespace of `LinkedList`:

> `using namespace LinkedList;`
> `LinkedList::SingleLinkedList* single_linked_list`
> `void createLinkedList();`



Ready to spawn your snake (snake's head)? 

Call the method you created at the beginning of this section; don't ask me where. 



> **TODO : **`**SnakeController.cpp**`
> ✅ Update the `SnakeController` constructor to initialize `single_linked_list` as `nullptr` and then call `createLinkedList()`

> ✅ Call  `single_linked_list->render()` in `render()` 
> ✅ Call `single_linked_list->createHeadNode()` in `spawnSnake()`



**Click here to see **`SnakeController.cpp`** **```cpp
#include "Player/SnakeController.h"
#include "Global/ServiceLocator.h"
#include "Level/LevelService.h"

namespace Player
{
	using namespace LinkedList;
	using namespace Global;
	using namespace Level;

	SnakeController::SnakeController()
	{
		single_linked_list = nullptr;
		createLinkedList();
	}

	SnakeController::~SnakeController()
	{
		destroy();
	}

	void SnakeController::createLinkedList()
	{
		single_linked_list = new SingleLinkedList();
	}

	void SnakeController::initialize()
	{
		float width = ServiceLocator::getInstance()->getLevelService()->getCellWidth();
		float height = ServiceLocator::getInstance()->getLevelService()->getCellHeight();

		single_linked_list->initialize(width, height, default_position, default_direction);
	}

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

	void SnakeController::render()
	{
		single_linked_list->render();
	}

		void SnakeController::processPlayerInput() { }
	
	void SnakeController::updateSnakeDirection() { }

	void SnakeController::moveSnake() { }

	void SnakeController::processSnakeCollision() { }

	void SnakeController::handleRestart() { }

	void SnakeController::spawnSnake()
	{
		single_linked_list->createHeadNode();
	}

	void SnakeController::reset() { 
	}

	void SnakeController::respawnSnake() { }

	void SnakeController::setSnakeState(SnakeState state)
	{
		current_snake_state = state;
	}

	SnakeState SnakeController::getSnakeState()
	{
		return current_snake_state;
	}

	void SnakeController::destroy()
	{
		delete (single_linked_list);
	}
}
```



> **TODO: **`**SingleLinkedList.cpp**`
> ✅ Call `head_node->body_part.render()` in `render()`



**Click here to see **`SingleLinkedList.cpp`** **```cpp
#include "LinkedList/SingleLinkedList.h"
#include "Player/BodyPart.h"
#include "Level/LevelView.h"
#include <iostream>

namespace LinkedList
{
	SingleLinkedList::SingleLinkedList()
	{
		head_node = nullptr;
	}
	SingleLinkedList::~SingleLinkedList() = default;
	void SingleLinkedList::initialize(float width, float height, sf::Vector2i position, Direction direction)
	{
		node_width = width;
		node_height = height;
		default_position = position;
		default_direction = direction;
	}
	void SingleLinkedList::render()
	{
		head_node->body_part.render();
	}
	void SingleLinkedList::createHeadNode()
	{
		head_node = createNode();
		head_node->body_part.initialize(node_width, node_height, default_position, default_direction);
		return;
	}
	Node* SingleLinkedList::createNode()
	{
		return new Node();
	}
}
```



woah! Now, you will be able to see the head of your Snake.

![Image](/Full-Stack-Game-Development/images/45895f25a3751212.png)

***Snake's Head***



In the upcoming section, you will give your snake its body.

**See you in the next section!👋🏼**
