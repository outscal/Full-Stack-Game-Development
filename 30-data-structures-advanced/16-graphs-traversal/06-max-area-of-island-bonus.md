# **Chapter 22 - Assignment - 3 - Max Area of Island** (Bonus)

**[ Task ]**

**Problem**
- Given an m x n binary matrix ***grid***.
- An island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical).
- You may assume all four edges of the grid are surrounded by water.
- The **area** of an island is the number of cells with a value of 1 in the island.
- Find the maximum area of an island in the grid. If there is no island, print 0.
    
![maxarea1-grid.jpg](//outscal.github.io/Full-Stack-Game-Development/images/dbc0746577e3f82b.jpg)
    
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