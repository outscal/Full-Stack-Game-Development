> Go to the following link to attempt this assignment: [click here](https://outscal.com/compiler/find-the-num-of-cards) This link will open a compiler window where you must write your code. After you complete the assignment, you must click the **Save Button** to save your code.



# Problem Statement -


---

Given an integer `**N**` which represents the number of cards in a deck. The deck is ordered from **`1** to **N**` where `**1**` is the topmost card and `**N**` is at the bottom. You take out the topmost card from the deck and insert it at the bottom and throw the next card that appears at the top of the deck. Again you do the same thing until a single card remains.

**The task is to find the number of the card that remains at the end.**



Example 1:

**Input** - `N = 4`

**Output** - `ans = 1`

**Explanation** -

At the beginning Deck looks like `D = [1,2,3,4]`

- Round 1: Shift 1 to the bottom and remove top element, i.e. 2, `D = [3,4,1]`
- Round 2: Shift 3 to the bottom and remove 4, `D = [1,3]`
- Round 3: Shift 1 to the bottom and remove 3, `D = [1]`

So at the end, card with number 1 is left. That is our answer



Example 2:

**Input **- `N = 6`

**Output **- `ans = 5`

**Explanation **-

At the beginning Deck looks like `D = [1,2,3,4,5,6]`

- Round 1: Shift 1 to the bottom and remove 2, `D = [3,4,5,6,1]`
- Round 2: Shift 3 to the bottom and remove 4, `D = [5,6,1,3]`
- Round 3: Shift 5 to the bottom and remove 6, `D = [1,3,5]`
- Round 4: Shift 1 to the bottom and remove 3, `D = [5,1]`
- Round 5: Shift 5 to the bottom and remove 1, `D = [5]`

So our answer is card with number 5





# Constraints -


---

- `1 ≤ N < 10^5`



# Submission Instructions -


---

- After completing this assignment, you must click on the **Save Button** of the compiler to save your code.
- After you save your code in compiler, a Popup will appear with a unique link generated.
- Copy that link and paste it as your assignment submission.
- You can use this link to share your assignment/code with other people as well, they will be able to run your code as well!
- So go ahead and show-off your newly learned and proven skills to your friends on LinkedIn!
