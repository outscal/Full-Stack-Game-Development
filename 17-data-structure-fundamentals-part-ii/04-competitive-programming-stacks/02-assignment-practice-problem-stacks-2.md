> Go to the following link to attempt this assignment: [click here](https://outscal.com/compiler/daily-temperatures) This link will open a compiler window where you must write your code. After you complete the assignment, you must click the **Save Button** to save your code.



# Problem Statement:


---

Given an array of integers `temperatures` represents the daily temperatures. Your task is to find number of days you have to wait to get a warmer temperature after the current day for each index `i` that is `0 ≤ i < temperatures.length`

**Return an array **`**ans**`** of size **`**temperatures.length**`** such that **`**ans[i]**`** represents waiting time for each day as explained above**





Example 1:

**Input **- `temperatures = [73,74,75,71,69,72,76,73]`

**Output **- `ans = [1,1,4,2,1,1,0,0]`

**Explanation -**

The number of waiting days for each day is as follows:

- For index 0, Temperature is 73. The next warmer day for this day is at index 1 where the temperature is 74. So `ans[0]` = 1 - 0
- For index 1, next warmer day is present at index 2. Hence `ans[1]` = 2 - 1
- For index 2 with temperature 75, next greater temperature comes at index 6 which is 76. So `ans[2]` = 6 - 2 = 4. That’s how for all other indexes `ans[i]` has been calculated.



# Constraints:


---

- `1 <= temperatures.length <= 10^5`
- `30 <= temperatures[i] <= 100`



# Submission Instructions:


---

- After completing this assignment, you must click on the **Save Button** of the compiler to save your code.
- After you save your code in compiler, a Popup will appear with a unique link generated.
- Copy that link and paste it as your assignment submission.
- You can use this link to share your assignment/code with other people as well, they will be able to run your code as well!
- So go ahead and show-off your newly learned and proven skills to your friends on LinkedIn!
