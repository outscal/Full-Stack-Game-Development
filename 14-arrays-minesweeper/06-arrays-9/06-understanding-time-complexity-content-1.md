Assume you're in *1878* when smartphones didn't exist.

You have an old-school telephone at your home ☎️



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/03_11_2025__10_31_16.png)



You're **searching for a name** in a phone book with **1000 pages** and the phone book is not in alphabetical order.😱

Each time you read a page, it takes some time. So the time taken to search the name depends on the **number of pages(n)** that you have read.

Now, here's how you can define **time complexity** in the context of the phone book example: 

The time taken to **search the name** based on how the **number of pages(n)** increases. 



But how do we calculate the time taken to search the name?

Do we calculate the time in seconds?🤔

No, rather than saying "It takes 10 seconds to read each page", we use an abstract unit **C** that represents the conditions that might vary for different people(like reading speed) and **ignore** the abstract unit **C, **so that the time taken to search the name depends **only** on the** number of pages**(**n**).



By making the time taken to search the name dependent only on the number of pages, we make the calculation fair for everyone!

Doesn't matter who is searching for the name and how fast is their reading speed(**C**), the calculation for time complexity depends only on the **number of pages(n).**

We represent this calculation of a generalized time with `**Asymptotic Notations**`!



## Understanding Asymptotic Notations


---



So, in asymptotic notations, we consider 3 scenarios:

- Best Case scenario
- Average Case scenario
- Worst Case scenario

Let's understand this with the same phone book example:



**Best Case** 

The best case is as straightforward as it sounds. 

In the context of the phone book example, the best case would be: 

You already know the exact page number for the name you're looking for. You open the phone book directly to that page and find the name immediately.

- This takes just **C** time (one page read)
- No matter the **number of pages(n)**, if you know the exact page, the time taken to search the name is still just the time to read one page.

We denote this as **Omega (Ω)**: The minimum time a search takes to complete In this case: **Ω(1)** - just one operation regardless of the **number of pages(n)**.



**Average Case** 

You don't know the exact page, but you find the name in the middle of the book (on page 500).

- This takes about **(n/2) × C** time (time to read 500 pages)
- Generally, the time taken to search the name equals the time to read **n/2** pages

We denote this as **Theta (Θ)**: The average search time In this case: **Θ(n/2)** simplifies to **Θ(n)** - time taken proportional to the total number of pages(**n**) 

Why? 🤔 

When the phone book has **1000 pages** and you find the name halfway through, the time taken equals reading **500 pages**. 

Whether we call this `Θ(n/2)` or `Θ(n)` doesn't change the fact that if the phone book doubles to **10,000 pages**, the time taken to search the name also doubles to the time needed to read **5000 pages**. 

If the number of pages doubles, then the time taken to find the name also doubles. So the time taken to search the name is still directly proportional to the number of pages(**n**).

Constants like 1/2 don't change the fundamental relationship - the time still grows linearly with the number of pages, whether it's n/2 or n.

Hence, the average case simplifies to **Θ(n)**!



**Worst Case** 

You don't know the page number and unfortunately, the name is on the very last page (page 1000).

- This takes **(n) × C** time (time to read all 1000 pages!)
- In the worst case, the time taken to search the name equals time to read **n** pages.

We denote this as **Big O (O)**: The upper bound on search time

In this case: **O(n)**: Time taken directly proportional to the number of pages(**n**)



Since **C** represents an arbitrary unit of time, we focus on **how the time taken to search the name grows** with the **number of pages**(**n**). 

These **asymptotic notations** (Ω, Θ, O) help define **how search time changes relative to n** without considering the abstract unit ***C***.



Now, here's how you can define **time complexity** in the context of the phone book example:

The time taken to **search the name** based on how the **number of pages(n) **grows.



But how do you "technically" define time complexity?🤔 

Time complexity is how the `**execution time**` of an `**algorithm**`** **increases as the `**input size**`** **grows.

What is an algorithm?!🤨



> 🎮📖**Game Dev Dictionary**
> **Algorithm**: An algorithm is a **step-by-step procedure** to solve a problem (like searching a name).



In our phone book example:

- The `execution time` is how much time it takes to find the name.
- The `algorithm` is searching for a name.
- The `input size` is the number of pages in the phone book (**n**).
- And **C**, the arbitrary unit, represents the time it takes to do one simple operation, like reading a single page, without worrying about whether you're using a fast or slow computer.



Now that you understand what time complexity is, let's learn how we can use the asymptotic notations to calculate time complexity in code!



# Calculating Time Complexity in Code


---



 We have 3 cases for calculating the time complexity, but we'll only consider the **worst-case** time complexity.

Why?🤔

There are 3 main reasons:

- **Predictability** – Ensures that an algorithm will not take more time than expected in any scenario.
- **Scalability** – Helps understand how an algorithm performs as the input size grows.
- **Standardized Comparison** – Provides a uniform way to compare different algorithms without relying on best or average cases.





So, let's first understand **O(1)** time complexity with an example

## O(1)

```cpp
int add(int a, int b) {
    return a + b; 
    // Just one simple calculation
    // No matter what values a and b have
}
```

In this example, we will analyze the time complexity by considering different values:

For small numbers:

- The function performs a single addition operation
- Execution time is proportional to **1C**

For medium numbers:

- Still performs just one addition
- Execution time is still **1C**

For large numbers:

- Even with very large numbers, we still only perform one addition
- Execution time remains **1C**

The time remains constant regardless of input size, hence **O(1)**.



Now, let's explore an example of **O(n) **time complexity:

## o(n)

```cpp
// O(n) time complexity - linear time
for (int i = 0; i < n; i++) {
    // operations: operations can be any operation which takes C time. Like addition, subtraction, etc
}
```

In this example, we will analyze the time complexity by considering different values of `n`:

For n = 3:

- The loop runs 3 times.
- Execution time is proportional to **3C**

For n = 5:

- The loop runs 5 times.
- Execution time is proportional to **5C**

For n = 1000:

- The loop runs 1000 times, scaling linearly with `n`
- Execution time is **1000C**

The time scales linearly with input size, hence execution time will be `**n * C**`  ignoring C we get: **O(n)**.

If the input size(**n**) doubles, the time also doubles.



Now let's look at a variation that's still O(n):

```cpp
for (int i = 0; i < n; i++) {
    // operations
}
for (int i = 0; i < n; i++) {
    // operations
}
```

In this example, we will analyze the time complexity:

For n = 3:

- First loop: n operations = 3 operations
- Second loop: n operations = 3 operations
- Total: n + n = 2n = 6 operations
- Execution time is proportional to **6C** or **2n * C**

For n = 5:

- First loop: n operations = 5 operations
- Second loop: n operations = 5 operations
- Total: n + n = 2n = 10 operations
- Execution time is proportional to **10C** or **2n * C**

For n = 1000:

- First loop: n operations = 1000 operations
- Second loop: n operations = 1000 operations
- Total: n + n = 2n = 2000 operations
- Execution time is **2000C** or **2n * C**

The time is 2n * C, but the constant factor 2 is dropped and we only focus on the input size in asymptotic notation, so this is still **O(n)**.



Then, there's also **O(n²)**!

## **O(n²)**

```cpp
// O(n²) time complexity - quadratic time
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // operations
    }
}
```

In this example, we will analyze the time complexity by considering different values of `n`: 

For n = 3:

- The outer loop runs 3 times.
- For each iteration of the outer loop, the inner loop runs 3 times.
- Total operations: 3 × 3 = 9 operations
- Execution time is proportional to **9C** 

For n = 5:

- The outer loop runs 5 times.
- For each iteration of the outer loop, the inner loop runs 5 times.
- Total operations: 5 × 5 = 25 operations
- Execution time is proportional to **25C** 

For n = 1000:

- The outer loop runs 1000 times.
- For each iteration of the outer loop, the inner loop runs 1000 times.
- Total operations: 1000 × 1000 = 1,000,000 operations
- Execution time is **1,000,000C** 

The time scales quadratically with input size (if the `input size = n` then the `time taken for operations to complete = n * n`), hence execution time will be:

`n² * C` ignoring C we get: **O(n²)**.



Now let's look at a variation that's still O(n²):

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // operations
    }
}
for (int i = 0; i < n; i++) {
    // operations
}
```

In this example, we will analyze the time complexity: 

For n = 3:

- First nested loops: n² operations = 9 operations
- Additional loop: n operations = 3 operations
- Total: n² + n = 9 + 3 = 12 operations
- Execution time is proportional to **12C** or **(n² + n) * C** 

For n = 5:

- First nested loops: n² operations = 25 operations
- Additional loop: n operations = 5 operations
- Total: n² + n = 25 + 5 = 30 operations
- Execution time is proportional to **30C** or **(n² + n) * C** 

For n = 1000:

- First nested loops: n² operations = 1,000,000 operations
- Additional loop: n operations = 1,000 operations
- Total: n² + n = 1,000,000 + 1,000 = 1,001,000 operations
- Execution time is **1,001,000C** or **(n² + n) * C** 

The time is `(n² + n) * C`, but when n is large, n² dominates and the n term becomes insignificant. 

In asymptotic notation, we focus on the most dominant term, so time complexity is still **O(n²)**.



You have successfully understood time complexity 💪🏼

In the next lesson, you'll learn about space complexity!

**See you there 👋🏼**
