# **Chapter 9 - Assignment - 1 - Lower Bound (Bonus)**

**[Task]**

**Problem - Implement <a href="https://www.geeksforgeeks.org/lower_bound-in-cpp/" target="_blank">lower_bound()</a>**

- Given a sorted array A of N integers and a number K.
- Find the lower_bound of K in the given array.
- **lower_bound -** The lower_bound() method in C++ is used to return an iterator pointing to the first element in the range [first, last) which has a value not less than val. This means that the function returns the index of the next smallest number just greater than or equal to that number. If there are multiple values that are equal to val, lower_bound() returns the index of the first such value.

**Input Format**
    
- The first line contains an integer N, denoting the number of elements of the array.
- The next line contains N space-separated integers, denoting the elements of the array.
- The last line contains the value K for which you need to find lower_bound().

**Output Format**
    
- Print the required index.

**Constraints**
- 1 ≤ N ≤ 10^5
- 1 ≤ A[i] ≤ 10^9

**Example**
- **Sample Input** <br>
    6<br>
    4 6 10 12 18 20<br> 
    6<br>
        
- **Sample Output**<br>
    1<br>
    

**[Submission]**

- Turn in this assignment with your repl link.