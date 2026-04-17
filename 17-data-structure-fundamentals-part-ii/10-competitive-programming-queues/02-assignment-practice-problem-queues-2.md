> Go to the following link to attempt this assignment: [click here](https://outscal.com/compiler/students-unable-to-eat-lunch) This link will open a compiler window where you must write your code. After you complete the assignment, you must click the **Save Button** to save your code.



# Problem Statement -


---

The school cafeteria offers circular and square sandwiches at lunch break, referred to by numbers `0` and `1` respectively. All students stand in a queue. Each student either prefers square or circular sandwiches.

The number of sandwiches in the cafeteria is equal to the number of students. The sandwiches are placed in a **stack**. At each step:

- If the student at the front of the queue **prefers** the sandwich on the top of the stack, they will **take it** and **leave** the queue.
- Otherwise, they will **leave it** and go to the queue's end.

This continues until none of the queue students want to take the top sandwich and are thus unable to eat.

You are given two integer arrays `students` and `sandwiches` where `sandwiches[i]` is the type of the `ith` sandwich in the stack (`i = 0` is the top of the stack) and `students[j]` is the preference of the `jth` student in the initial queue (`j = 0` is the front of the queue).

**Return *****the number of students that are unable to eat.***



Example 1:

**Input** - `students = [1,1,1,0,0,1], sandwiches = [1,0,0,0,1,1]`

**Output **- `ans = 3`

**Explanation **-

- Front student wants a square sandwich and at the top of the stack, square sandwich is present so he takes it, `students = [1,1,0,0,1], sandwiches = [0,0,0,1,1]`
- Front student wants a square but it is not available right now, so he leaves the queue and stand at the end, `students = [1,0,0,1,1], sandwiches = [0,0,0,1,1]`
- Again front student leaves and go to the end, `students = [0,0,1,1,1], sandwiches = [0,0,0,1,1]`
- Front student eats the sandwich, `students = [0,1,1,1], sandwiches = [0,0,1,1]`
- Again front student eats the sandwich, `students = [1,1,1], sandwiches = [0,1,1]`

Now **NO** student ****is standing in the queue who wants a circular sandwich, but at the top of the stack circular sandwich is present. That means all the remaining students will be unable to eat.

Therefore answer is 3



Example 2:

**Input **- `students = [1,1,0,0], sandwiches = [0,1,0,1]`

**Output **- `ans = 0`



# Constraints -


---

- `1 <= students.length, sandwiches.length <= 100`
- `students.length == sandwiches.length`
- `sandwiches[i]` is `0` or `1`
- `students[i]` is `0` or `1`



# Submission Instructions -


---

- After completing this assignment, you must click on the **Save Button** of the compiler to save your code.
- After you save your code in compiler, a Popup will appear with a unique link generated.
- Copy that link and paste it as your assignment submission.
- You can use this link to share your assignment/code with other people as well, they will be able to run your code as well!
- So go ahead and show-off your newly learned and proven skills to your friends on LinkedIn!
