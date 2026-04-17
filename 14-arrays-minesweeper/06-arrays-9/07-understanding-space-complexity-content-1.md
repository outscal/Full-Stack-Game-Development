# Understanding Space Complexity


---

Just like time complexity measures the growth of execution time, space complexity measures how much **memory **an algorithm requires as input size increases.

Let's consider an example of the `player_scores` array**:**

```cpp
int n;
cout << "Enter the number of elements: ";
cin >> n;

int player_scores[n];
```

In this example, the user determines the size of `player_scores`

Since the array is directly **proportional to n**, we analyze **how memory usage grows** as `n` increases.

Let’s consider the different values of `n` and analyze how memory grows:

**For n = 3:**

- The array stores 3 integers → **O(3)**
- Memory for 3 integer values is needed.

**For n = 5:**

- The array stores 5 integers → **O(5)**
- Memory for 5 integer values is needed.

**For n = 1000:**

- The array stores 1000 integers → **O(1000)**
- Memory for 1000 integer values is needed.

So for input size(n) = n, memory required is for n integers and hence the space complexity is **O(n)**.

Thus, the **space complexity of an array is O(n)**, where `n` is the number of elements stored.



You might think that is there a best / average/ worst case complexity for space as well? 🤔

Yes, **space complexity** can also have **best, average, and worst cases**, just like time complexity. 

However, it is not as commonly discussed because space complexity is usually more predictable and depends on the problem constraints.



You have now understood Space Complexity as well! 💪🏼



In the next lesson, you’ll learn how to implement an array in our game.

**See you there👋🏼**
