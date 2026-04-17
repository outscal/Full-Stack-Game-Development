# **Chapter 24 - Assignment - 1 - Activity Selection Problem (Bonus)**

**[ Task ]**

**Problem**
- You are given n activities with their start and finish times.
- Find the maximum number of activities that can be performed by a single person, assuming that a person can only work on a single activity at a time.
**Input Format**
- First line: N → number of activities
- Second line: N space-separated integers denoting start time of ith activity.
- Third line: N space-separated integers denoting finish time of ith activity.

**Output Format**
- Single Integer denoting **maximum number of activities**

**Example**
- **Sample Input -** <br>
    3<br>
    10 12 20<br>
    20 25 30<br>

- **Sample Output -**<br>
    2<br>

- **Explanation -** <br>
    A person can perform at most two activities. The maximum set of activities that can be executed is {0, 2} [ These are indexes in start[] and finish[] ]
- **Note - Your algorithm should be able to solve even if activities are not sorted by start or finish time.**  

**[Submission]**

- Turn in this assignment with your repl link.