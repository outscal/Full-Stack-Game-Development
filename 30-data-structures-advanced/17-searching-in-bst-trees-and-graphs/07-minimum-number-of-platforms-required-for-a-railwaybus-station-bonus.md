# **Chapter 24 - Assignment - 2 - Minimum Number of Platforms Required for a Railway/Bus Station (Bonus)**

**[ Task ]**

**Problem**
- You are given the arrival and departure times of all trains that reach a railway station.
- Find the minimum number of platforms required for the railway station so that no train waits.
- We are given two arrays that represent the arrival and departure times of trains that stop..

**Input Format**
- First line: N → number of trains
- Second line: N space-separated strings denoting arrival time of the ith train.
- Third line: N space-separated strings denoting departure time of the ith train.
- Note - time is given HH:MM format.

**Output Format**
- Single Integer denoting the **minimum number of platforms**

**Example**
- **Sample Input -** <br>
    6<br>
    9:00 9:40 9:50 11:00 15:00 18:00<br>
    9:10 12:00 11:20 11:30 19:00 20:00<br>
- **Sample Output -**<br>
    3
- **Explanation -** <br>
    There are at-most three trains at a time (time between 9:40 to 12:00)
    
- **Note - Your algorithm should be able to solve even if trains are not sorted by arrival or departure time.**
    
    

**[Submission]**

- Turn in this assignment with your repl link.