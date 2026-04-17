Let's say you have a Linked List: `A->B->C->D->nullptr` 

Now you have to delete the tail node 

You can just traverse till the last node, and delete it. But the issue would be, you have to make sure: `C->nullptr` 

For this to happen, you have to stop at `C` and then delete `D` and then set `C->nullptr` 



Now, `C` is the second-last node, when you want to check for the last node, you check `cur_node->next == nullptr` and similarly, to check for the second-last node, you can use: `cur_node->next->next != nullptr` 



> **TODO: **`**SingleLinkedList**`** **
> ✅ Create `void SingleLinkedList::removeNodeAtTail()` 
> ✅ Inside it,

> If the head node is `nullptr`, simply return
> If there is only 1 node, call `removeNodeAtHead()` 
> If there is more than 1 node, then travel till the second last node, delete the last node and set the new last node's `next = nullptr` 
> Decrement `linked_list_size` when you delete a node



Click here to see `SingleLinkedList`'s `removeNodeAtTail()` 

```cpp
void SingleLinkedList::removeNodeAtTail()
{
    if (head_node == nullptr) return;
    linked_list_size--; //Decrement linked list size when you are deleting a node

    Node* cur_node = head_node;

    if (cur_node->next == nullptr) //If there is only 1 node in the linked list
    {
        removeNodeAtHead();
        return;
    }

    while (cur_node->next->next != nullptr) //If there is more than 1 node in the linked list
    {
        cur_node = cur_node->next;
    }

    delete (cur_node->next);
    cur_node->next = nullptr; //Set the new tail node's next pointer to nullptr
}
```





## CALCULATING THE TIME COMPLEXITY OF DE**LETION **AT THE TAIL


---

To insert a node at the end, you need to:

1. Traverse to the tail node: O(n)
2. Delete the Tail Node: O(1)
3. Initialize the last node's next with `nullptr`: O(1)

Therefore,

> **TIME COMPLEXITY for DELETION AT TAIL: O(n)**
