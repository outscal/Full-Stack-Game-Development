## **Linked List**


---

A data structure created with a collection of nodes, where each node contains data and a reference (or link) to the next node in the sequence. This structure allows for efficient insertion and deletion.



## **Doubly Linked List**


---



A type of linked list where each node contains two links: one pointing to the next node and one to the previous node. This allows for bidirectional traversal.



## **Circular Linked List**


---

A linked list where the last node points back to the first node, making the list circular. This can be implemented as singly or doubly circular linked lists.



## **Time Complexity of Linked List Operations**


---



![Image](//outscal.github.io/Full-Stack-Game-Development/images/61c04a868c978681.jpg)





## **Important Characteristics**


---

- **Efficiency**: Linked lists are ideal for applications where manipulation (insertion/deletion) of data is frequent and random access is less frequent.
- **Memory Overhead**: Each node in a linked list requires extra memory for the pointer(s) along with the actual data, which can be a consideration in memory-sensitive applications.
- **Random Access is not possible**: If your application requires frequent access to elements at arbitrary positions, `std::list` is not suitable because accessing an element by index requires O(n) time.



## **STL → Lists**


---

- `**std::list**`: Implemented as a doubly linked list, offering bidirectional iterators and O(1) time complexity for insertions and deletions anywhere within the list.
- **Usage**: Include the header `**<list>**` and use `**std::list<T>**` where `**T**` is the type of elements stored. Example: `**std::list<int> myList;**`
- **Common Methods**:
- - `**push_back(value)**`: Adds a value at the end.
  - `**push_front(value)**`: Adds a value at the beginning.
  - `**pop_back()**`: Removes the last element.
  - `**pop_front()**`: Removes the first element.
  - `**sort()**`: Sorts the list.
  - `**reverse()**`: Reverses the list order.
  - `**begin(), end()**`: Return iterators to the start and one past the end of the list.
  - `**insert(iterator, value)**`: Inserts a value at the position specified by the iterator.
  - `**erase(iterator)**`: Removes the element at the position specified by the iterator.
- **Best Practices**: Use `**std::list**` when you need frequent insertions and deletions. Prefer `**std::vector**` for faster access and better cache locality.
