# **Chapter 22 - Assignment - 5 - Jump Game III** (Bonus)

**[ Task ]**

**Problem**
- Given an array of non-negative integers ***arr***, you are initially positioned at the ***start*** index of the array.
- When you are at index *i*, you can jump to *i + arr[i]* or *i - arr[i],* check if you can reach any index with value 0.

**Input Format**
- First line: n, size of the array
- Second Line: n space-separated integers, elements of the array
- Last line: start, starting index

**Output Format**
- Print **Yes** if you can reach else **No.**

**Constraints**
- 1 ≤ n ≤ 10^5
- 0≤ arr[i] < n
- 0≤ start ≤ n-1

**Example - 1**
- **Sample Input -** <br>
    7<br>
    4 2 3 0 3 1 2<br>
    5<br>

- **Sample Output -**<br>
    Yes

- **Explanation -** <br>
    All possible ways to reach at index 3 with value 0 are:<br>
    index 5 -> index 4 -> index 1 -> index 3<br>
    index 5 -> index 6 -> index 4 -> index 1 -> index 3<br>

**Example - 2**
- **Sample Input -** <br>
    5<br>
    3 0 2 1 2<br>
    2<br>
- **Sample Output -**<br>
    No<br>

**[Submission]**

- Turn in this assignment with your repl link.