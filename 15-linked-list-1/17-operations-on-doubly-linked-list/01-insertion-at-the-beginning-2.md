Alright, let's switch gears and get serious!

We're dealing with the big brother now, the Doubly Linked List (DLL). 💪



In this chapter, you’ll understand the operations of Doubly Linked Lists and explore how they differ from Singly Linked Lists (SLL). 



In the first round, we'll focus on inserting a node at the beginning of the list.



## Insertion at the Beginning


---



Just like with your Singly Linked List (SLL), you'll need to implement the `createNode()` function and initialize node. 

This is a great example of **Polymorphism **in action.



```cpp
Node* DoubleLinkedList::createNode()
{
    return new DoubleNode();
}
```



**Inserting Node at the Head**

Finally, implement the function to insert a new node at the beginning of the Doubly Linked List. 

You already know how to do this in a Singly Linked List—it's quite similar here! 

The key difference is that you also need to set the `previous`. 



So how does it happen? 🤔

Think of creating a new `**DoubleNode**` (let's call it `**n**`)

Your first task is to point `**next**` of the new node `**n**` to to the current `**head**`. If there is no head, this new node becomes your head.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/1f683c4f5f318c26.png)



Then, you'll point `**previous**` of the current head to the new node `**n**`.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/7fb7e19985c4a230.png)



At last, you'll make the new node `**n**` the **new head** of the linked list.

And just like that, you've added a new node at the beginning of your Doubly Linked List! 

After this the `**linked_list_size**` will also increase by one value.


> **💡Pro Tip:** when dealing with `**previous**` pointer of `**DoubleNode**` in your Snake Game, use `**static_cast<DoubleNode*>**` for proper **type conversion**.



Why to use `static_cast<DoubleNode*>` ?`**static_cast<DoubleNode*>**` is used to convert a pointer from the base class `**Node**` to the derived class `**DoubleNode**`, allowing access to unique properties like `**previous**` specific to DoubleNode.



> **TODO: **`**DoublyLinkedList**` 
> ✅ Implement `void DoublyLinkedList::insertNodeAtHead()` as explained



**Click here to see**`**DoublyLinkedList**` **'s **`insertNodeAtHead()`** **```cpp
void DoubleLinkedList::insertNodeAtHead()
{
    linked_list_size++;
    Node* new_node = createNode();

    if (head_node == nullptr)
    {
        head_node = new_node;
        static_cast<DoubleNode*>(new_node)->previous = nullptr;
        initializeNode(new_node, nullptr, Operation::HEAD);
        return;
    }

    initializeNode(new_node, head_node, Operation::HEAD);

    new_node->next = head_node;
    static_cast<DoubleNode*>(head_node)->previous = new_node;

    head_node = new_node;
}
```



1/9 Operations Done ✅

8 more to go. Keep up the great work! 💪 GG!



**See you in the next section!👋🏼**
