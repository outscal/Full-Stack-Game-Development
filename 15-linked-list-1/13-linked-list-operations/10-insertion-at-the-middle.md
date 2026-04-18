![Insertion at Middle](//outscal.github.io/Full-Stack-Game-Development/images/42cba2bc7ff3ae9c.gif)

***Inserting a Body Part in the Middle***

You need the middle index!

Let's find it!



## Finding the middle Index


---

Yes, finding the middle index!

Isn't that super easy: Just divide the linked list's size by 2!



It is a good approach and easy, but what if you don't know the size of the linked list?!

How will you find the middle then?



**STORY TIME...**

You've heard the Rabbit and Tortoise story. right?

They both started a race, Tortoise was super slow and Rabbit was super fast. But still, the Tortoise won because he was consistent and Rabbit got overconfident and ignored the competition.

Well, Rabbit wouldn't lose if it was a code!

Because code doesn't get overconfident. Code is code, it just works!



Let's say Rabbit took 2 steps in 1 second and Tortoise took 1 step in 1 second

How many steps would they take after 10 seconds?

Tortoise: 10, Rabbit: 20

After 30 seconds?

Tortoise: 30, Rabbit: 60

After 60 seconds?

Tortoise: 60, Rabbit: 120



See, the Rabbit always covers 2 times the distance covered by the Tortoise

How about you apply the same approach to your code?

Take 2 pointers: Fast and Slow

Fast will jump 2 nodes at a time but slow will move only 1 node at a time

Now, when the Fast pointer reaches the last node, the Slow pointer will be in the middle!

Isn't that just pure genius?!



> **TODO:** `SingleLinkedList` 
> ✅ Create and Implement `int SingleLinkedList::findMiddleNode()`: It should apply the 2 pointer approach discussed above and return the index of the middle node



Click here to see the code for `findMiddleNode()` 

```cpp
int SingleLinkedList::findMiddleNode()
{
    Node* slow = head_node;
    Node* fast = head_node;
    int midIndex = 0;  // This will track the index of the middle node.

    // Move fast pointer at 2x speed and slow pointer at 1x speed.
    while (fast != nullptr && fast->next != nullptr) {
        slow = slow->next;
        fast = fast->next->next;
        midIndex++;
    }

    // Now, slow is at the middle node
    return midIndex;
}
```



Good!

Now you have to finally insert the node at the middle!



## Inserting a Node in Middle


---

> **TODO:** `SingleLinkedList` 
> ✅ Create  `void SingleLinkedList::insertNodeAtMiddle()` 
> ✅ Inside it, call `insertNodeAtHead()` if the list empty and then use `findMiddleNode()` and `insertNodeAtIndex()` to insert a node in the middle



Click here to see `insertNodeAtMiddle()` 

```cpp
void SingleLinkedList::insertNodeAtMiddle() 
{
    if (head_node == nullptr) {
        insertNodeAtHead();             // If the list is empty, insert at the head.
        return;
    }

    int midIndex = findMiddleNode();    // Use the existing function to find the middle index
    insertNodeAt(midIndex);             // Use the existing function to insert the node at the found index             
}
```





## CALCULATING THE TIME COMPLEXITY OF INSERTION AT THE MIDDLE


---

To insert a node at the end, you need to:

1. Initialize a new node: O(1)
2. Traverse to the middle node: O(n)
3. Insert the new node at the middle node: O(1)

Therefore,

> **TIME COMPLEXITY for INSERTION AT MIDDLE: O(n)**
