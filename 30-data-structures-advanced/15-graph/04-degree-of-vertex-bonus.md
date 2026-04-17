# **Chapter 21 - Assignment - 1 - Degree of Vertex** (Bonus)

**[ Task ]**

**Problem**
- Given an undirected graph G as an adjacency matrix representation and a vertex v, find the degree of the vertex v in the graph.

**Input Format**
- First Line: N - maximum number of vertices graph can have
- Next N lines: N space-separated integers elements of the adjacency matrix
- Last line: v, vertex whose degree is to be found

**Output Format**
- The required degree of vertex v

**Constraints**
- 1 ≤ N ≤ 500
- 1 ≤ v ≤ N - 1
- graph[i][j] = 1 → if there is an edge between i and j
- graph[i][j] = 0 → if there is not any edge between i and j

**Example - 1**
- **Sample Input -**<br> 
    4<br>
    0 1 1 1<br>
    1 0 0 1<br>
    1 0 0 1<br>
    1 1 1 0<br>
    3<br>
- **Sample Output -**<br>
    3

**Example - 2**
- **Sample Input -** <br>
    4<br>
    0 1 1 1<br>
    1 0 0 1<br>
    1 0 0 1<br>
    1 1 1 0<br>
    1<br>
- **Sample Output -**<br>
    2<br>
    

**[Submission]**

- Turn in this assignment with your repl link.