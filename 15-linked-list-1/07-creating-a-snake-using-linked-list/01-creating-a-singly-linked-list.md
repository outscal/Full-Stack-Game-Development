You've levelled up on Linked List knowledge, and now it's time to build your very own single linked list. 
Excited??



You've learned about nodes and and the basics of Linked Lists.

But guess what? You're just getting started! 💪



## **Building A Single Linked List**


---



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_24_2024__10_31_04.png)

***LinkedList Architecture ***



First things first, let's set the stage for your linked list:



> **TODO**
> ✅ Create an empty `SingleLinkedList` class inside `LinkedList` folder and create `namespace LinkedList` inside it
> ✅ Move the `Node.h` file in `LinkedList` folder and create nested `namespace` inside it.



Now that you have a class `SingleLinkedList`, what properties should it include?



**Understanding your **`**SingleLinkedList**`** properties:**

1. Most wanted,** **`**head_node**`**: **This pointer will keep track of the first node in your linked list, serving as an entry point to access the entire list.
2. `**node_width**`**, **`**node_height**`**:** These properties define the dimensions of each node in a linked list, which is crucial at the time of rendering your game.
3. `**default_position**`**:** A vector representing the default position for any node of the linked list.
4. `**default_direction**`**:** An `Enum` representing the default direction of movement for nodes.

> **TODO: **`**SingleLinkedList**`
> ✅ Create the following properties:

> `Node* head_node;`
> `float node_width;`
> `float node_height;`
> `sf::Vector2i default_position;`
> `Direction default_direction;`



Now that you have your properties in place let's discuss the methods you'll need in your `SingleLinkedList` class.



**Understanding your **`**SingleLinkedList**`** methods:**

1. `**Constructor**` to set the `head_node` as `nullptr` and `**Destructor**` will be default.
2. `**render():**`** **To render the whole list on the screen. 
3. `**initialize(float width, float height, sf::Vector2i position, Direction direction)**`**:** This will be used to initialize the properties of a single linked list node according to the parameter it gets.



> **TODO**`SingleLinkedList`
> ✅ Create following lifecycle methods:

> `public:`
> `SingleLinkedList();`
> `~SingleLinkedList();`
> `void initialize(float width, float height, sf::Vector2i position, Direction direction);`
> `void render();`



But still, one question: how can you create a linked list without creating a node?

So, create a method `createNode()` that makes a new body part (`**Node**`) for the snake and return its reference.



> **TODO**`SingleLinkedList`
> ✅ Create a `private`  methods `Node* createNode()`



**Click here to see **`SingleLinkedList.h`** **```cpp
#pragma once
#include <SFML/System/Vector2.hpp>
#include "LinkedList/Node.h"

namespace LinkedList
{
	class SingleLinkedList
	{
	private:
		Node* head_node;

		float node_width;
		float node_height;

		sf::Vector2i default_position;
		Direction default_direction;

		Node* createNode();

	public:
		SingleLinkedList();
		~SingleLinkedList();

		void initialize(float width, float height, sf::Vector2i position, Direction direction);
		void render();
	};
}
```



> **TODO: **`**SingleLinkedList**`
> ✅Initialize the `head_node` as `nullptr` in the constructor.
> ✅Implement the `createNode()` and `initialize()` as discussed.



**Click here to see **`SingleLinkedList.cpp`** **```cpp
#include "LinkedList/SingleLinkedList.h"
#include "Player/BodyPart.h"
#include "Level/LevelView.h"

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

	void SingleLinkedList::render() { }

	Node* SingleLinkedList::createNode()
	{
		return new Node();
	}
}
```



In the next section, you'll be spawning head for your linked list. Are you excited to create your first `**Node**`?



**See you in the next section!👋🏼**
