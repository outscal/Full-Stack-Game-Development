> Go to the following link to attempt this assignment: [click here](https://outscal.com/compiler/baseball-game) This link will open a compiler window where you must write your code. After you complete the assignment, you must click the **Save Button** to save your code.



# Problem Statement -


---

You are keeping the scores for a baseball game with strange rules. At the beginning of the game, you start with an empty record.

You are given a list of strings of operations named `ops`, where `ops[i]` is the `ith` operation you must apply to the record and is one of the following:

- An integer `x` : Record a new score of `x`
- `‘+’` : Record a new score that is sum of the previous 2 scores
- `‘D’` : Record a new score that is the double of the previous score
- `‘C’` : Discard the previous score, remove it from the record

**Return *****the sum of all the scores on the record after applying all the operations*****.**



Example 1:

**Input** - `ops = ["5","2","C","D","+"]`

**Output **- `ans = 30`

**Explanation **-

- `"5"` : Since it is an integer value, add it to the record, `Record = [5]`
- `"2"` : Add it to the record, `Record = [5, 2]`
- `"C"` : Here we have to discard the previous value, so remove 2. `Record = [5]`
- `“D”` : Add 2*5 to the record, `Record = [5, 10]`
- `“+”` : Add 5 and 10 i.e. 15, So `Record = [5, 10, 15]`



Example 2:

**Input **- `ops = ["1","C"]`

**Output **- `ans = 0`

**Explanation **-

- `“1”` : `Record = [1]`
- `“C”` : We need to 1 from the record, so `Record = [ ]`
- Since the Record is empty, total sum is 0



# Constraints -


---



- `1 <= operations.length <= 1000`
- `ops[i]` is `"C"`, `"D"`, `"+"`, or a string representing an integer in the range `[-3 * 10^4, 3 * 10^4]`.
- For operation `"+"`, there will always be at least two previous scores on the record.
- For operations `"C"` and `"D"`, there will always be at least one previous score on the record.



# Submission Instructions -


---

- After completing this assignment, you must click on the **Save Button** of the compiler to save your code.
- After you save your code in compiler, a Popup will appear with a unique link generated.
- Copy that link and paste it as your assignment submission.
- You can use this link to share your assignment/code with other people as well, they will be able to run your code as well!
- So go ahead and show-off your newly learned and proven skills to your friends on LinkedIn!
