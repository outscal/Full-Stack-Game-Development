Here is the old function you created:

```cpp
void SingleLinkedList::removeNodeAtHead()
{
    Node* cur_node = head_node;
    head_node = head_node->next;

    cur_node->next = nullptr;
    delete (cur_node);
}
```



Now, you only have to decrease the size of the linked list.



> **TODO: **`**SingleLinkedList**` 
> ✅  Inside `removeNodeAtHead()`, decrement `linked_list_size`



## CALCULATING THE TIME COMPLEXITY OF DELETION AT THE HEAD


---

**Pseudo Code** for Deletion at Head

```cpp
Node* cur_node = head_node;
head_node = head_node->next;
cur_node->next = nullptr;
delete (cur_node);
```

This is a simple 4-step process, which is `O(1)` time complexity



You have direct access to the head node, so you don't have to do any traversal.

Therefore,

> **TIME COMPLEXITY for DELETION AT HEAD: O(1)**
