# **Chapter 14 - Assignment - 1 - Linked List Representation (Bonus)**

**[ Task ]**

- Given a tree as an array write a function to convert it into the linked list representation and print it.
- Assume -1 as null.

**Example**
- **arr = [1,2,3, 4, 5]** represents
        
    ![Untitled](https://outscal.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8af5f442-854f-462a-850e-50b11cb999ae%2FUntitled.png?table=block&id=8c1f9440-bda0-4f74-a6ae-be2a9f14fba7&spaceId=8c9f7b97-3438-434a-b8ca-0a53eb7262ea&width=480&userId=&cache=v2)
        

- **arr = [1,2,3, -1, 5, -1, 6]** represents
    
    ![Untitled](https://outscal.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd9b34c33-4543-48ab-b4b7-e12650209f05%2FUntitled.png?table=block&id=a250a817-0641-4718-ad1b-d57b9a2704d4&spaceId=8c9f7b97-3438-434a-b8ca-0a53eb7262ea&width=550&userId=&cache=v2)
    

**Hint - for 0 -based indexed array**
    
- if **'i'** is index of parent node then children are at index **2 * i + 1 & 2 * i + 2.**

**Note to Remember**

- In upcoming assignments binary tree or binary search tree will be given as an array, you should use this code to convert that into a linked list representation tree and then solve the question.
- Assume -1 as null if given in the array.
- Also if the tree is not given you must take it as input from the user as an array of integers.

**[Submission]**

- Turn in this assignment with your repl link.