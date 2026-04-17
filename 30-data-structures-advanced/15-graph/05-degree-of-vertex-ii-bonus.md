# **Chapter 21 - Assignment - 2 - Degree of Vertex II** (Bonus)

**[ Task ]**

**Problem**
- Given an undirected graph G as an adjacency matrix representation and an integer Q denoting the number of queries.
- In each query, you will be given a vertex and you have to print the degree of the vertex v in the graph.

**Input Format**
- First Line: N - maximum number of vertices graph can have
- Next N lines: N space-separated integers elements of the adjacency matrix
- Next line: Q, number of queries
- Next Q lines: v, vertex whose degree is to be found

**Output Format**
- The required degree of vertex v

**Constraints**
- 1 ≤ N ≤ 1000
- 1≤ Q ≤ N
- 1 ≤ v ≤ N - 1
- graph[i][j] = 1 → if there is an edge between i and j
- graph[i][j] = 0 → if there is not any edge between i and j

**Example - 1**
- **Sample Input -** <br>
    4<br>
    0 1 1 1<br>
    1 0 0 1<br>
    1 0 0 1<br>
    1 1 1 0<br>
    2<br>
    3<br>
    1<br>

- **Sample Output -**<br>
    3<br>
    2<br>
    
- **Follow up - What if the graph is given as an adjacency list? Think🤔🤔.**
    
    

**[Submission]**

- Turn in this assignment with your repl link.