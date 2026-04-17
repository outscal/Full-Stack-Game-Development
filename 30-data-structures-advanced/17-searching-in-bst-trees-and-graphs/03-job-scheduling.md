# **Chapter 24 - Implementation - Job Scheduling**

**[ Task ]**

- Implement the **Job Scheduling** problem.

**Input:**
```
Enter the number of jobs: 4
Enter the job names and their deadlines and profits:
Job1 4 20
Job2 1 10
Job3 1 40
Job4 1 30
```
**Output:**
```
Job Sequence: Job3 Job1 Job4
Total Profit: 90
```
**Explanation:**
```
Jobs:    1  2  3  4
Deadlines: 4  1  1  1
Profits:  20 10 40 30
```
Here's how the jobs are scheduled in the above example:

- Job3 has the highest profit and its deadline is 1, so it is scheduled first.
- Job1 has the second-highest profit and its deadline is 4, which allows it to be scheduled after Job3.
- Job4 has the third-highest profit and its deadline is 1, but its deadline has already been met, so it can be scheduled after Job3 but before Job1.
- Job2 has the lowest profit and its deadline has already passed, so it cannot be executed.

**[Submission]**

- Turn in this assignment with your repl link.