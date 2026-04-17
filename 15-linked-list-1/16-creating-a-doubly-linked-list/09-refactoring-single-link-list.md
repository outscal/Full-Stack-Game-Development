# **Tasks**


---



## Refactoring of SingleLinkedList


---

## [IN SingleLinkedList]



1. Shift `SingleLinkedList` in `SingleLinked` folder, and take care of namespaces.
2. Inherit the base `LinkedList` class and add `**override**` keyword to all virtual methods.
3. Change access specifier from `private` to `protected`
4. Update the constructor and destructor to default.
5. Make sure to implement all functions you implemented in `SinglyLinkedList` in previous branches
6. Remove all methods that have been implemented in the base `LinkedList` class.



Here is the Header file for `SingleLinkedList`. Use it as a guide to implement the class.

```cpp
#pragma once
#include <SFML/System/Vector2.hpp>
#include "LinkedListLib/Node.h"
#include "LinkedListLib/LinkedList.h"

namespace LinkedListLib
{
	namespace SingleLinked
	{
		class SingleLinkedList : public LinkedList
		{
		protected:
			virtual Node* createNode() override;

		public:
			SingleLinkedList();
			~SingleLinkedList();


			void insertNodeAtTail() override;
			void insertNodeAtHead() override;
			void insertNodeAtMiddle() override; 
			void insertNodeAtIndex(int index, Node* new_node);

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
			void reverseNodeDirections();
		};
	}
}
```







# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-5-Doubly-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-5-Doubly-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
