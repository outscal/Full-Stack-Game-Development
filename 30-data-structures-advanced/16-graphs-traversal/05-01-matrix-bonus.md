# **Chapter 22 - Assignment - 2 - 01 Matrix** (Bonus)

**[ Task ]**

**Problem**
- Given an m x n binary matrix ***mat***, return the distance of the nearest 0 for each cell.
- The distance between two adjacent cells is 1.

**Input Format**
- First line: m n
- Next m lines: n space-separated integers

**Output Format**
- A m x n matrix containing the answer for each cell.

**Constraints**
- m == mat.length
- n == mat[i].length
- 1 ≤ m, n ≤ 10^4
- 1 ≤ m * n ≤ 10^4
- mat[i][j] is either 0 or 1.
- There is at least one 0 in mat.

**Example - 1**
- **Sample Input -** <br>
    3 3<br>
    0 0 0<br>
    0 1 0<br>
    0 0 0<br>
- **Sample Output -** <br>
    0 0 0<br>
    0 1 0<br>
    0 0 0<br>

**Example - 2**
- **Sample Input -**<br>
    3 3<br>
    0 0 0<br>
    0 1 0<br>
    1 1 1<br>
- **Sample Output -**<br>
    0 0 0<br>
    0 1 0<br>
    1 2 1<br>
    

**[Submission]**

- Turn in this assignment with your repl link.