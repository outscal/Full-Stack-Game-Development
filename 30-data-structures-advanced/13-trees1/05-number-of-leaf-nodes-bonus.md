# **Chapter 14 - Assignment - 2 - Number of Leaf Nodes (Bonus)**

**[ Task ]**

- Given a tree as an array write a function to convert it into the linked list representation and find the **number of leaf nodes** in it.
- Assume -1 as null.

**Example -**
- **arr = [1,2,3, 4, 5]** represents
        
    ![Untitled](//outscal.github.io/Full-Stack-Game-Development/images/7320d974077596f5.png)
        


**number of leaf nodes - 3**

- **arr = [1,2,3, -1, 5, -1, 6]** represents
    
![Untitled](//outscal.github.io/Full-Stack-Game-Development/images/3cc61bcc22b6d75e.png)
    

**number of leaf nodes - 2**

- **Hint - for 0 -based indexed array** <br>
if **'i'** is index of parent node then children are at index **2 * i + 1 & 2 * i + 2.**

**Note -**
- In upcoming assignments binary tree or binary search tree will be given as an array, you should use this code to convert that into a linked list representation tree and then solve the question.
- Also if the tree is not given you must take it as input from the user as an array of integers.

**[Submission]**

- Turn in this assignment with your repl link.