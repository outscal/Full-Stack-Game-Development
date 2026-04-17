**Time to Delete All Nodes!!**

In your game, there are times when all the snake nodes need to be removed (deleted) before it is respawned.

This operation ensures the list is completely cleared, leaving no nodes behind.



## **DELETE ALL NODES**


---



To remove all nodes from a Doubly Linked List (DLL), you can use a similar approach to what you used in a Singly Linked List (SLL).

The idea is to keep removing the head node until the list is empty.



Why the head? 

Because it takes O(1) time! 

We need it quickly, right? 

Why make the player wait?



> **TODO: **`**DoublyLinkedList**`
> ✅ Implement `void DoublyLinkedList::removeAllNodes()`



**Click here to see**`**DoublyLinkedList**`** 's **`removeAllNodes()`

```cpp
void DoubleLinkedList::removeAllNodes()
{
    if (head_node == nullptr) return;

    while (head_node != nullptr)
    {
        removeNodeAtHead();
    }
}
```





7/9 Operations Done ✅

Only 2 more to go! 🔥 GG!

**See you in the assignment! 👋🏼**
