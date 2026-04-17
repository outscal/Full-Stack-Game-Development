# **Chapter 14 - Assignment - 2 - Number of Leaf Nodes (Bonus)**

**[ Task ]**

- Given a tree as an array write a function to convert it into the linked list representation and find the **number of leaf nodes** in it.
- Assume -1 as null.

**Example -**
- **arr = [1,2,3, 4, 5]** represents
        
    ![Untitled](https://outscal.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8af5f442-854f-462a-850e-50b11cb999ae%2FUntitled.png?table=block&id=8cbd200d-b59b-43a0-a45e-b4e040158921&spaceId=8c9f7b97-3438-434a-b8ca-0a53eb7262ea&width=480&userId=&cache=v2)
        


**number of leaf nodes - 3**

- **arr = [1,2,3, -1, 5, -1, 6]** represents
    
![Untitled](https://outscal.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd9b34c33-4543-48ab-b4b7-e12650209f05%2FUntitled.png?table=block&id=8aaaab51-b4f8-43c2-b9a2-d205f4c3dcdc&spaceId=8c9f7b97-3438-434a-b8ca-0a53eb7262ea&width=550&userId=&cache=v2)
    

**number of leaf nodes - 2**

- **Hint - for 0 -based indexed array** <br>
if **'i'** is index of parent node then children are at index **2 * i + 1 & 2 * i + 2.**

**Note -**
- In upcoming assignments binary tree or binary search tree will be given as an array, you should use this code to convert that into a linked list representation tree and then solve the question.
- Also if the tree is not given you must take it as input from the user as an array of integers.

**[Submission]**

- Turn in this assignment with your repl link.