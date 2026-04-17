Refactored Singly Linked List? Good.

**Time for double fun with Doubly Linked List!! ** Ready??



First, you'll set up your files and namespaces for `DoubleLinkedList`.



> **TODO:** **DoubleLinkedList**
> **✅** Create `DoubleLinkedList` class inside `DoubleLinked` folder. Make sure to add the nested namespace of `LinkedListLib` and `DoubleLinked`



You'll start with the basics.



> **TODO:** **DoubleLinkedList**
> **✅** Implement constructor and destructor to default



Remember the drill? 

Inheriting from the base `LinkedList` class to your `DoubleLinkedList` class and then override all virtual methods in `DoubleLinkedList`, just like you did in `SingleLinkedList`.

 

> **TODO:** **DoubleLinkedList**
> **✅** Inhertit the base `LinkedList` class. 
> **✅** Create and override all virtual methods of base `LinkedList` class.



Time to enhance your `DoubleLinkedList` with some key functions.

Understand each function one by one:


1. `**shiftNodesAfterInsertion(Node* new_node, Node* cur_node, Node* prev_node)**`**:** After adding `new_node`, shift the rest body parts to backwards to make space for `new_node`.
2. `**removeNodeAtIndex(int index)**`**:** To remove a body part from a specific `index`.
3. `***shiftNodesAfterRemoval(Node* cur_node)***`***: ***After removing a body part (`cur_node`), the rest of the body part must be shifted to the front. 



These functions play crucial roles in managing a `DoubleLinkedList`'s structure.

Time to add them to your structure!!



> **TODO:** **DoubleLinkedList.h**
> **✅** Add above discussed methods in `**DoubleLinkedList.h**`



**Click here to see **`DoubleLinkedList.h````cpp
#pragma once
#include "LinkedListLib/LinkedList.h"

namespace LinkedListLib
{
	namespace DoubleLinked
	{
		class DoubleLinkedList : public LinkedList
		{
		protected:
			virtual Node* createNode() override;

		public:
			DoubleLinkedList();
			~DoubleLinkedList();


			void insertNodeAtTail() override;
			void insertNodeAtHead() override;
			void insertNodeAtMiddle() override;
			void insertNodeAtIndex(int index) override;
			void shiftNodesAfterInsertion(Node* new_node, Node* cur_node, Node* prev_node);

			void removeNodeAtTail() override;
			void removeNodeAtHead() override;
			void removeNodeAtMiddle() override;
			void removeNodeAt(int index) override;
			void removeNodeAtIndex(int index);
			void removeAllNodes() override;
			void removeHalfNodes() override;
			void shiftNodesAfterRemoval(Node* cur_node);

			Direction reverse() override;
		};
	}
}
```


**See you there in the next chapter! 👋**
