Ready for the next move?

It's time to implement the logic of adding the last minion to the minion train! 🚂

![Image](//outscal.github.io/Full-Stack-Game-Development/images/6f70a59fd0c9f2b5.gif)





## Insertion at the End


---



It's recall time, what you did in Singly Linked List (SLL).



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



Inserting a node at the end of a Singly Linked List is a straightforward process. 

First, increase the size of the list to accommodate the new node. 

Then, create the new node and traverse the list to the last node.

Now, set the last node's **next** pointer to point to the new node, joining it at the end of the list. 

Easy peasy, right?



Now, the only twist when dealing with a Doubly Linked List (DLL) is each new node's `previous` points to the last node as well.

First, point the last node's `next` to `new_node`.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/9fd47c4293440756.png)



Then. the`previous` of `new_node` to the last node.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/fac5b43a50636b07.png)



And that's it! 

Not too much change, just a little extra connection to keep track of the `previous`. Simple, isn't it? 



> **TODO: **`**DoublyLinkedList**` 
> ✅ Implement `void DoublyLinkedList::insertNodeAtTail()`



**Click here to see**`**DoublyLinkedList**`** 's **`insertNodeAtTail()`** **```cpp
void DoubleLinkedList::insertNodeAtTail()
{
    linked_list_size++;
    Node* new_node = createNode();
    Node* cur_node = head_node;

    if (cur_node == nullptr)
    {
        head_node = new_node;
        static_cast<DoubleNode*>(new_node)->previous = nullptr;
        initializeNode(new_node, nullptr, Operation::TAIL);
        return;
    }

    while (cur_node->next != nullptr)
    {
        cur_node = cur_node->next;
    }

    cur_node->next = new_node;
    static_cast<DoubleNode*>(new_node)->previous = cur_node;
    initializeNode(new_node, cur_node, Operation::TAIL);
}
```



2/9 Operations Done ✅
7 more to go. Keep that momentum going! 💪 GG!



**See you there in Assignment! 👋🏼**
