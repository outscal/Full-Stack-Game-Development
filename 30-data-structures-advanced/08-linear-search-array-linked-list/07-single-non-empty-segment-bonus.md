# **Chapter 8 - Assignment - 4 - Single Non-Empty Segment (Bonus)**

**[Task]**

**Problem**
- Vivek has a string S. Each character of S is a digit '0' or '1'.
- Help Vivek and check if all the '1' digits form a single non-empty segment (consecutive sequence) in the string.
- For each test case, print "YES" or "NO" accordingly.

**Input Format**
- The first line of the input contains an integer T denoting the number of test cases. The description of T test cases follows.
- The only line of each test case contains one string S, consisting of digits '0' and '1' only.

**Output Format**
- For each test case, output a single line containing the answer — "YES" if all the '1' digits form a single non-empty segment, and "NO" otherwise. Don't print the quotes.

**Constraints**
- 1 ≤ T ≤ 10
- 1 ≤ |S| ≤ 10^5 (here, |S| denotes the length of S)

**Example**
- **Sample Input -** </br> 
    6</br>
    001111110</br>
    00110011</br>
    000</br>
    1111</br>
    101010101</br>
    101111111111</br>
- **Sample Output -** </br>
    YES</br>
    NO</br>
    NO</br>
    YES</br>
    NO</br>
    NO</br>
- **Explanation** 
    The answer is "YES" for strings 001111110 and 1111.
    The answer is "NO" for 00110011 because the '1' digits form two disjoint segments (while they should all be consecutive, with no '0' digits between them).
    The answer is "NO" for 000 because the segment formed by the '1' digits must be non-empty (as written in the statement).

**[Submission]**

- Turn in this assignment with your repl link.