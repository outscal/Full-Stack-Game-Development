Remember **STL**?

C++'s **Standard Template Library**!

You can have a revision [here](https://outscal.com/course/minesweeper-in-c-using-array/array/stl-minesweeper/intro-to-stl)



## List in STL


---

***List*** is an implementation of a ***Doubly Linked List*** in the STL library.

It can be used using: `**std::list**` 



**Formally:**

In C++'s Standard Template Library (STL), a list is a sequence container that allows insertion and deletion of elements at any point in the container quickly. It is implemented internally as a doubly linked list.



**Characteristics of **`**std::list**`** are:**

1. **Bidirectional Iteration:** it is possible to traverse through a List using bidirectional iterators. But unlike vectors, it doesn't allow direct access by an offset from the current position.
2. **No Reallocation on Modification:** Unlike `std::vector`, `std::list` does not need to reallocate memory when elements are added or removed, since each element is allocated individually and linked via pointers.
3. **Dynamic Size:** The size of a std::list can dynamically change as elements are added or removed. It does not have a fixed size or a capacity it needs to manage, unlike static arrays or vectors with a capacity.



## When to use `std::list`?


---

1. **Frequent Insertions and Deletions**: If your application involves frequent insertion and deletion of elements at positions other than the end, `**std::list**` can be a more efficient choice compared to `**std::vector**`. These operations in a list do not require elements to be contiguous in memory, which avoids the overhead of shifting elements.
2. **Large Elements**: When dealing with large elements, moving or copying them (as would be necessary in a vector during resizing or insertion at middle positions) can be costly. `**std::list**`, with its non-contiguous storage, avoids these costs.
3. **Unknown Size**: If the number of elements is not known beforehand and changes frequently, using a `**std::list**` avoids the repeated reallocation and copying that might occur with a `**std::vector**`.
