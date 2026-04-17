![Half-Half](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__10_16_29.gif)

***Snake Half-Half***



Eating poison reduces the snake's length to half. 



## Understanding Splitting in Half


---

![Splitting in Half Index Calculations](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__11_31_32.png)

***Splitting in Half Index Calculations***



See, when the length is 4, then `4/2 = 2`, all nodes from Index 2 will be deleted

When the length is 5, then 5`/2 = 2.5 = 2` (assume dividing `int`), all nodes from Index 2 will be deleted

When the length is 7, then 7`/2 = 3.5 = 3` (assume dividing `int`), all nodes from Index 3 will be deleted



Let's assume a Linked List: `A->B->C->D->E` 

This has 5 nodes, so 3 nodes will be deleted. 

Assuming the indexing begins at 0, you will delete all the nodes from index 2, i.e. `***C***`

And `***'B'***`*** ***will be the new tail node.

So basically you need a reference to node `***'B'***` and what is the index of `***'B'***`?

1!



Are you confused?

Look at this formula and life will become simple!

```text
New Tail Node Index = (Linked List Length / 2 ) -1
```

  Want to test it?



```text
Size 4: New Tail Node Index = 4/2 - 1 = 2 - 1 = 1 (2nd Node)
Size 5: New Tail Node Index = 5/2 - 1 = 2 - 1 = 1 (2nd Node)
Size 7: New Tail Node Index = 7/2 - 1 = 3 - 1 = 2 (3rd Node)
Size 10: New Tail Node Index = 10/2 - 1 = 5 - 1 = 5 (5th Node)
```



## Discussing the architecture for splitting the snake


---

When the snake eats the poison, something should happen. 

Something to start the process. First, calculate the new tail index and then remove every node after the new tail index should be deleted.

Let's follow the architecture in the image:

![Flow- Snake Splitting](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__10_17_28.png)

***Flow- Splitting Snake***



`findNodeAtIndex()`: It will give you the reference of the node you want, in this case, the new tail node node

`removeHalfNodes()`: In this, you will delete all nodes after the new tail node. 



> **TODO: **`**SingleLinkedList**` 
> ✅ Create `Node* SingleLinkedList::findNodeAtIndex(int index)`: Use a loop to traverse to the node at index `index` and return that node.





## `removehalfnodes()`


---

We have discussed above the formula to find the index of the new tail node, now you have to use that index and get a reference to the new tail node using `findNodeAtIndex()` and delete all the nodes after it and set the next pointer of the new tail node to `nullptr`. And don't forget to update the `linked_list_size` with every node you delete.



> **TODO: **`**SingleLinkedList**` 
> ✅ Create `void SingleLinkedList::removeHalfNodes()`: Use the above-discussed approach to implement the function



Click here to see `SingleLinkedList`'s `removeHalfNodes()` 

```cpp
void SingleLinkedList::removeHalfNodes()
{
    if (linked_list_size <= 1) return;
    int half_length = linked_list_size / 2;
    int new_tail_index = half_length - 1;

    Node* prev_node = findNodeAtIndex(new_tail_index);
    Node* cur_node = prev_node->next;

    while (cur_node != nullptr)
    {
        Node* node_to_delete = cur_node;
        cur_node = cur_node->next;

        delete (node_to_delete);
        linked_list_size--;
    }

    prev_node->next = nullptr;
}
```
