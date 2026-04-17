## DELETION AT THE END


---



In a Singly Linked List (SLL), to remove a node from the end, you had to traverse to the second last node, delete its next node, and set the next pointer to `nullptr`.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_25_2024__16_09_18.gif)



Here's the code to achieve this

```cpp
while (cur_node->next->next != nullptr)
{
    cur_node = cur_node->next;
}
```



You know you could do the same thing.

But.. But. But..

Let's play with the Doubly Linked List! When it has some extra power, why not use it?



Instead of moving to the second last node, you can go directly to the last node, step back to one node, and then delete the last node.

Who doesn't like to push the limits?



Let me show you in code what I mean:

```cpp
Node* cur_node = head_node;

// Traverse the list until reaching the last node
while (cur_node->next != nullptr)
{
    cur_node = cur_node->next;
}

// Retrieve the previous node of the last node using static_cast for type conversion
Node* previous = static_cast<DoubleNode*>(cur_node)->previous;
previous->next = nullptr;    // Set the next pointer of the previous node to nullptr
```



By taking advantage of the bidirectional nature of DLLs, you can make things interesting.



> **TODO: **`**DoublyLinkedList**`
> ✅ Implement `void DoublyLinkedList::removeNodeAtTail()`





**Click here to see**`**DoublyLinkedList**`** 's **`removeNodeAtTail()````cpp
void DoubleLinkedList::removeNodeAtTail()
{
    if (head_node == nullptr) return;
    linked_list_size--;

    Node* cur_node = head_node;

    if (cur_node->next == nullptr)
    {
        removeNodeAtHead();
        return;
    }

    while (cur_node->next != nullptr)
    {
        cur_node = cur_node->next;
    }

    Node* previous = static_cast<DoubleNode*>(cur_node)->previous;
    previous->next = nullptr;
    delete (cur_node);
}
```



5/9 Operations Done ✅
4 more to go. GG!



**See you there in Assignment! 👋🏼**
