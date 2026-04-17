Inserting at the beginning, and inserting at the end is done. It is time for the last trick!

Insert a node wherever you want!



## Inserting a Node at an index


---



Inserting a node in at any index is not very difficult,

You just need to traverse to that index and change some `*next*` pointers.

But we are not just working on a Linked List but on a Snake.

![placeholder](https://outscal.com/EditLMS/snake/linked-list-1/linked-list-operations/undefined)

![Insertion at Middle](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__12_51_03.gif)

***Inserting a Body Part at index = 2***



Notice in this visual that when a new `BodyPart` is added to a Linked List, all the `BodyPart`s behind it are moved back. This is important to make space for the new `BodyPart`.



Let's take an example Linked List `A->B->C->nullptr` 

If you want to insert a new node `D` at index `2`, then the steps would be:

1. Traverse to the node at `index-1`, i.e. `2-1 = 1`, i.e. `B`
2. Keep a reference of both `B` and `C` 
3. Point `B`'s `next` to `D`
4. Point `D`'s `next` to `C`

Now, the updated Linked List will be: `A->B->D->C->nullptr` 



You can create this functionality inside a new function: `void SingleLinkedList::insertNodeAtIndex(int index)` 

To implement this, you need to do the following things:

1. Make sure that the `index` is valid
2. If the `index = 0,` you can insert a new node at the `head` 
3. Create a new node
4. Insert the new node at the index as discussed above
5. Initialize the node using `initializeNode()` 
6. Increment `linked_list_size` 



> **TODO:** `SingleLinkedList` 
> ✅ Create and Implement `void SingleLinkedList::insertNodeAtIndex(int index)`, it should work like discussed in the above.



Click here to see `SingleLinkedList`'s `insertNodeAtIndex()` 

```cpp
void SingleLinkedList::insertNodeAtIndex(int index)
{
    if (index < 0 || index >= linked_list_size) return;

    if (index == 0)
    {
        insertNodeAtHead();
        return;
    }

    Node* new_node = createNode();
    
    int current_index = 0;
    Node* cur_node = head_node;
    Node* prev_node = nullptr;

    while (cur_node != nullptr && current_index < index)
    {
        prev_node = cur_node;
        cur_node = cur_node->next;
        current_index++;
    }

    prev_node->next = new_node;
    new_node->next = cur_node;
    initializeNode(new_node, prev_node, Operation::TAIL);
    linked_list_size++;

}
```





## Shifting nodes after inserting a new node


---

To shift all the nodes behind, you have to do 2 things:

1. Every node should take the position of the node behind it
2. The last should be initialised as if it is being added to the tail



```cpp
void SingleLinkedList::shiftNodesAfterInsertion(Node* new_node, Node* cur_node, Node* prev_node)
{
    Node* next_node = cur_node;
    cur_node = new_node;

    while (cur_node != nullptr && next_node != nullptr)
    {
        cur_node->body_part.setPosition(next_node->body_part.getPosition());
        cur_node->body_part.setDirection(next_node->body_part.getDirection());

        prev_node = cur_node;
        cur_node = next_node;
        next_node = next_node->next;
    }

    initializeNode(cur_node, prev_node, Operation::TAIL);
}
```



> **TODO:** `SingleLinkedList` 
> ✅ Create and Implement `void SingleLinkedList::shiftNodesAfterInsertion(Node* new_node, Node* cur_node, Node* prev_node)` like in the above code
> ✅ Call it at the end inside `void SingleLinkedList::insertNodeAtIndex(int index)`



Now, you can use these functions to insert a node wherever you want!
