**Insertions are done, Time for Deletion!!**

Time for the 4th operation! 🎸



## Deletion at the Beginning


---



In a Singly Linked List (SLL), removing a node from the beginning is as simple as this code snippet:

```cpp
void SingleLinkedList::removeNodeAtHead() {
    Node* cur_node = head_node;
    head_node = head_node->next;

    cur_node->next = nullptr;
    delete cur_node;
}
```



You update the `head_node` to point to the next node, removing the first node from the list.

And guess what? 

It's the same here in the Doubly Linked Lists (DLL) too!



The twist? if `head_node` is not `nullptr`, you need to set `head_node → previous` to `nullptr`. This will help to avoid memory leaks.

And just like that, you've easily removed the node at the head! 



> **TODO: **`**DoublyLinkedList**`
> ✅ Implement `void DoublyLinkedList::removeNodeAtHead()`




**Click here to see**`**DoublyLinkedList**`** 's **`removeNodeAtHead()````cpp
void DoubleLinkedList::removeNodeAtHead() {
		linked_list_size--;
		
    Node* cur_node = head_node;
    head_node = head_node->next;

    if (head_node != nullptr) {
        static_cast<DoubleNode*>(head_node)->previous = nullptr;
    }

    cur_node->next = nullptr;
    delete cur_node;
}
```



4/9 Operations Done ✅
5 more to go. GG!



**See you in the next section!👋🏼**
