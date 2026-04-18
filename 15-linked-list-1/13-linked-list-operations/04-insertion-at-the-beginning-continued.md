This is the pseudo-code for adding a new node at the head

```text
Create a new_node
new_node→next = head node
head node = new_node
```


But things aren't that simple, there can be 2 cases:

1. Normal, when you simply need to create a new node and use it as the new head node
2. When there is NO head node, in that case, you need to create a new node and then use it as the current head node



Before implementing this function, you need to keep track of the Linked List's size, this can be used in multiple situations like checking for win-lose conditions



> **TODO: **`**SingleLinkedList**` 
> ✅ Create `int linked_list_size` and set it to `0` in `initialize()` method



## Continuing inserting head node...


---

![Flow- Inserting at Head](//outscal.github.io/Full-Stack-Game-Development/images/f1667dea3cd6dee2.png)

***Flow for Inserting at Head***



> **TODO: **`**SingleLinkedList**` 
> ✅ Create and implement `void SingleLinkedList::insertNodeAtHead()` as explained in the above flow diagram



Click here to see`SingleLinkedList`'s `insertNodeAtHead()` 

```cpp
void SingleLinkedList::insertNodeAtHead()
{
    linked_list_size++;
    Node* new_node = createNode();

    if (head_node == nullptr)
    {
        head_node = new_node;
        initializeNode(new_node, nullptr, Operation::HEAD);
        return;
    }

    initializeNode(new_node, head_node, Operation::HEAD);
    new_node->next = head_node;
    head_node = new_node;
}
```





## CALCULATING THE time complexity of insertion at THE head


---

**Pseudo Code** for Insertion at Head

```cpp
Node* new_node = new Node();
new_node->next = head_node;
head_node = new_node;
```

This is a simple 3-step process, which is `O(1)` time complexity

The rest of the code in `insertNodeAtHead()` is also a constant and therefore `O(1)`



You have direct access to the head node, so you don't have to do any traversal.

Therefore,

> **TIME COMPLEXITY for INSERTION AT HEAD: O(1)**
