# **Chapter 24 - Assignment - 3 - Connect n ropes with minimum cost (Bonus)**

**[ Task ]**

**Problem**
- You are given n ropes of different lengths, we need to connect these ropes into one rope.
- The cost to connect two ropes is equal to the sum of their lengths.
- Find the minimum cost to connect all ropes.

**Input Format**
- First line: N → number of ropes
- Second line: N space-separated strings denoting the length of the ith rope.

**Output Format**
- Single Integer denoting the **minimum cost.**

**Example**
- **Sample Input -** <br>
    4<br>
    4 3 2 6<br>
- **Sample Output -**<br>
    29<br>
- **Explanation -** 
We can connect the ropes in the following ways.
1. First, connect ropes of lengths 2 and 3. Now we have three ropes of lengths 4, 6, and 5.
2. Now connect ropes of lengths 4 and 5. Now we have two ropes of lengths 6 and 9.
3. Finally, connect the two ropes and all ropes have connected.
        
    Total cost for connecting all ropes is 5 + 9 + 15 = 29
        

**[Submission]**

- Turn in this assignment with your repl link.