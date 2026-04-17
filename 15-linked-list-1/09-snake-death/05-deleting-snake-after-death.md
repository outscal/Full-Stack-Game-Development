When the snake dies, you have to delete it. That is not the big question.

The big question is, how?



You'll have to delete every individual node.

This can be done in `SingleLinkedList` 

To remove all nodes, you can delete the head node, then there will be a new head node, and then you can delete it too

Repeat this until `head_node` gets equal to `nullptr` 



## Removing Head Node


---

Get away from the screen!

Take a 5-minute break and think...

You have to remove the head node, what will you need to do to do it correctly

Take your time and think🤔💭…



**Here is what you need to do:** 



You are storing the head node's reference already, you need to set the new `head_node` to `head_node->next`

and then delete the old head node form using `delete()` 



> **TODO: **`**SingleLinkedList**`** **
> ✅ Implement `void SingleLinkedList::removeNodeAtHead()` where you replace the head node with `head_node->next` and delete the old head node



Click here to see `SingleLinkedList`'s `removeNodeAtHead()` 

```cpp
void SingleLinkedList::removeNodeAtHead()
{
	Node* cur_node = head_node;
	head_node = head_node->next;

	cur_node->next = nullptr;
	delete (cur_node);
}
```





## Removing All Nodes


---

To remove all nodes, you can just keep removing the head node in a loop till head node becomes a null pointer



> **TODO: **`**SingleLinkedList**`** **
> ✅ Create `void SingleLinkedList::removeAllNodes()` 
> ✅ Inside it, keep deleting head node using `removeNodeAtHead()` till head node becomes a null pointer



Click here to see `SingleLinkedList`'s `removeAllNodes()` 

```cpp
void SingleLinkedList::removeAllNodes()
{
	if (head_node == nullptr) return;

	while (head_node != nullptr)
	{
		removeNodeAtHead();
	}
}
```





Are you sad that now the snake can be deleted?

Well, don't worry my child, because in the next section...

The snake will be resurrected again👼🏼!
