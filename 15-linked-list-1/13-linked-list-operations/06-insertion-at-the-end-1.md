You have already created a function for this...

```cpp
void SingleLinkedList::insertNodeAtTail()
	{
		Node* new_node = createNode();
		Node* cur_node = head_node;

		if (cur_node == nullptr) //If there is no head, then create a new head node
		{
			head_node = new_node;
			new_node->body_part.initialize(node_width, node_height, default_position, default_direction);
			return;
		}

		while (cur_node->next != nullptr)
		{
			cur_node = cur_node->next;
		}

		cur_node->next = new_node;
		new_node->body_part.initialize(node_width, node_height, getNewNodePosition(cur_node), cur_node->body_part.getDirection());
	}
```



You already have function `initializeNode()` specifically for initializing the node, so update this code and use that function to initialize the new node (body_part).

And one more thing, you'll need to update the linked list's size too.



> **TODO: **`**SingleLinkedList**` 
> ✅ Inside `insertNodeAtTail`, increment `linked_list_size` 
> ✅ Use `initializeNode()` to initialize the new node



Click here to see the new `insertNodeAtTail()` 

```cpp
void SingleLinkedList::insertNodeAtTail()
{
    linked_list_size++;
    Node* new_node = createNode();
    Node* cur_node = head_node;

    if (cur_node == nullptr)
    {
        head_node = new_node;
        initializeNode(new_node, nullptr, Operation::TAIL);
        return;
    }

    while (cur_node->next != nullptr)
    {
        cur_node = cur_node->next;
    }

    cur_node->next = new_node;
    initializeNode(new_node, cur_node, Operation::TAIL);
}
```





**DONE!**



## CALCULATING THE TIME COMPLEXITY OF INSERTION AT THE Tail


---

To insert a node at the end, you need to:

1. Initialize a new node: **O(1)**
2. Traverse to the tail node: **O(n)**
3. Insert the new node at the tail node: **O(1)**

Therefore,

> **TIME COMPLEXITY for INSERTION AT TAIL: O(n)**
