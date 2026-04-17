# **Chapter 24 - Implementation - Optimal Merge Pattern**

**[ Task ]**

- Implement the **Optimal Merge Pattern** problem.

[Example]

**Input:** n = 3, size = {2, 3, 4} <br>
**Output:** 14 <br>
**Explanation:** There are different ways to combine these files: 

Method 1: Optimal method 
```
  2     3      4
  |_____|      |
     |         |
     5         |
     |_________|
          |
          9
Cost: 5 + 9 = 14
```
Method 2: 
```
  2      3     4
  |      |_____|      
  |         |
  |         7  
  |_________|
       |
       9
Cost: 7 + 9 = 16
```
Method 3:
```
  2     4      3
  |_____|      |
     |         |
     6         |
     |_________|
          |
          9
Cost: 6 + 9 = 15
```

**[Submission]**

- Turn in this assignment with your repl link.