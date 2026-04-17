> Go to the following link to attempt this assignment: [click here](https://outscal.com/compiler/next-greater-element) This link will open a compiler window where you must write your code. After you complete the assignment, you must click the **Save Button** to save your code.



# Problem Statement:


---

The **next greater element** for some element `x` in an array is the **first greater** element that is **to the right** of `x` in that array.

You are given two **distinct 0-indexed** integer arrays `nums1` and `nums2`, where `nums1` is a subset of `nums2`.

For each index `i` in `nums1` that is `0 <= i < nums1.length`, find the index `j` in `nums2` such that `nums1[i] == nums2[j]` and determine the **next greater element** of `nums2[j]` in `nums2`. If there is no next greater element, then the answer for this query is `-1`.

**Return *****an array***** **`**ans**`** *****of length***** **`**nums1.length**`** *****such that***** **`**ans[i]**`** *****is the next greater element as described above.***





Example 1:

**Input:** `nums1 = [4,1,2], nums2 = [1,3,4,2]`

**Output:** `ans = [-1,3,-1]`

**Explanation: **

The next greater element for each value of nums1 in nums2 is as follows:

- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.



Example 2:

**Input:** `nums1 = [2,4], nums2 = [1,2,3,4]`

**Output:** `[3,-1]`

**Explanation: **

The next greater element for each value of nums1 in nums2 is as follows:

- 2 is underlined in nums2 = [1,2,3,4]. The next greater element is 3.
- 4 is underlined in nums2 = [1,2,3,4]. There is no next greater element, so the answer is -1.





# Constraints:


---

- `1 <= nums1.length <= nums2.length <= 1000`
- `0 <= nums1[i], nums2[i] <= 10^4`
- All integers in `nums1` and `nums2` are **unique**.
- All the integers of `nums1` also appear in `nums2`.



# Submission Instructions:


---

- After completing this assignment, you must click on the **Save Button** of the compiler to save your code.
- After you save your code in compiler, a Popup will appear with a unique link generated.
- Copy that link and paste it as your assignment submission.
- You can use this link to share your assignment/code with other people as well, they will be able to run your code as well!
- So go ahead and show-off your newly learned and proven skills to your friends on LinkedIn!
