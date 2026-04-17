# **Chapter 22 - Assignment - 4 - Minimum Number of Days to Eat N Oranges** (Bonus)

**[ Task ]**

**Problem**
- There are n oranges in the kitchen and you decided to eat some of these oranges every day as follows:
    1. Eat one orange
    2. If the number of remaining oranges (n) is divisible by 2 then you can eat n/2 oranges.
    3. If the number of remaining oranges (n) is divisible by 3 then you can eat 2*(n/3) oranges.
- You can only choose one of the actions per day.
- Find the minimum number of days to eat n oranges.

**Input Format**
- First line: n, number of oranges

**Output Format**
- Print the minimum number of days to eat n oranges.

**Constraints**
- 1 ≤ n ≤ 10^9

**Example - 1**
- **Sample Input -** <br>
    10<br>
- **Sample Output -**<br>
    4<br>
- **Explanation -** <br>
    You have 10 oranges.<br>
    Day 1: Eat 1 orange,  10 - 1 = 9.<br>
    Day 2: Eat 6 oranges, 9 - 2*(9/3) = 9 - 6 = 3. (Since 9 is divisible by 3)<br>
    Day 3: Eat 2 oranges, 3 - 2*(3/3) = 3 - 2 = 1.<br>
    Day 4: Eat the last orange  1 - 1  = 0.<br>
    You need at least 4 days to eat the 10 oranges.<br>

**Example - 2**
- **Sample Input -** <br>
    1<br>
- **Sample Output -**<br>
    1<br>
    

**[Submission]**

- Turn in this assignment with your repl link.