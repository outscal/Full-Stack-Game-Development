# **Chapter 22 - Assignment - 3 - Max Area of Island** (Bonus)

**[ Task ]**

**Problem**
- Given an m x n binary matrix ***grid***.
- An island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical).
- You may assume all four edges of the grid are surrounded by water.
- The **area** of an island is the number of cells with a value of 1 in the island.
- Find the maximum area of an island in the grid. If there is no island, print 0.
    
![maxarea1-grid.jpg](https://outscal.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F716db05a-d53d-46ac-b9a4-a15ea9643225%2Fmaxarea1-grid.jpg?table=block&id=fa455386-dab3-4e0e-9db9-42186c123874&spaceId=8c9f7b97-3438-434a-b8ca-0a53eb7262ea&width=2000&userId=&cache=v2)
    
**Input Format**
- First line: m n
- Next m lines: n space-separated integers

**Output Format**
- Print the maximum area of an island in the grid. If there is no island, print 0.

**Constraints**
- m == grid.length
- n == grid[i].length
- 1 ≤ m, n ≤ 50
- grid[i][j] is either 0 or 1.

**Example - 1**
- **Sample Input -**<br> 
    3 3<br>
    0 0 0<br>
    0 1 0<br>
    0 0 0<br>
- **Sample Output -**<br>
    1<br>

**Example - 2**
- **Sample Input -**<br>
    3 3<br>
    0 0 0<br>
    0 1 0<br>
    1 1 1<br>
- **Sample Output -** <br>
    4 <br>
    
**[Submission]**

- Turn in this assignment with your repl link.