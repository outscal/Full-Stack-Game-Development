> It’s time to create a new feature branch for the upcoming game features.
> 
> You can merge the branch you are currently working on back into main now!

> 

> Make a new feature branch out of your main branch called → [ `**Feature-2-Binary-Search**` ]

> Let’s start working on the new feature now!



In this lesson, you will be learning about Binary Search in detail. You'll understand how it works and then learn its implementation.



Binary search is a powerful algorithm for locating a target value within a sorted array. It repeatedly divides the search area in half until the target is found or its absence is determined.

Unlike linear search, which checks each element individually, binary search narrows down the possibilities very quickly.



As mentioned in the last lesson, binary search can only work with sorted lists. What do you think could be the reason for it?

Think about it.

.

.

![  ](//outscal.github.io/Full-Stack-Game-Development/images/79ab453bb091abb8.gif)





Click below for the answer!

Reason*Binary search works only on sorted lists.*

The key reason it only works on sorted lists is that it relies on the ability to continuously divide the search area in half for searching the target element, which is only possible in a sorted structure.

(You will understand this better by the end of this lesson)



Let’s take another look at Binary Search and then discuss what is happening in the video.



![   ](//outscal.github.io/Full-Stack-Game-Development/images/8092af1569222d89.gif)





Binary Search is being performed on the sticks. It divides the collections into half, checks if the target stick is in the middle, and keeps narrowing down the search until it finds the target stick.



But for binary search to happen, there are conditions that need to be met.

Let's discuss about them.



## Conditions for binary search


---

For binary search to work effectively, two conditions must be met:

1. **Sorted Array:** The elements must be arranged in ascending or descending order to for proper division and comparison.

- Binary search relies on dividing the search space in half and eliminating half the possibilities with each comparison. This is only possible if the elements are sorted in ascending or descending order.
- Imagine a sorted array of numbers. You're searching for the number 10. If 8 is to the left of 10 and 15 is to the right, you know 10 must be between them. This order allows you to discard half the line (left or right) based on each comparison with the middle element.
- Without sorting, the array is like a mess of numbers mixed together. If 8, 15, and 10 are randomly placed in the array, comparing them with the middle element won't make any sense because you wouldn't know which half to discard to continue searching.



1. **Constant Time Access:** Binary search assumes it can access any element in the list in constant time (O(1)). This means it can directly jump to any position in the array using the index.

- It can directly access the element in the middle of the search space using its index. So, there is no need to search through each element one by one.
- Based on the comparison with the middle element, binary search can immediately discard half of the remaining possibilities. This quick elimination speeds up the search time.



As you already saw the visualization of binary search, let's understand the steps that make it work.



## Steps of Binary Search


---



The steps to perform Binary Search are as follows:-

- Divide the search space into two halves by finding the middle of the index.
- Compare the middle element of the search space with the key.
- If the key is found at the middle element, the process is terminated.
- If the key is not found in the middle element, choose which half will be used as the next search space. 
- - If the key is smaller than the middle element, the left side is used for the next search. 
  - If the key is larger than the middle element, the right side is used for next search. 
- This process is continued until the key is found or the total search space is exhausted.



The pseudocode for binary search is given below. Please go through it:-

Pseudocode

```cpp
function binary_search(array, target) 

		left = 0 
		right = length(array) - 1 
		
		while left <= right: 
				mid = (left + right) / 2 
				
				if array[mid] == target:
						return mid
					
			elif array[mid] > target: 
					right = mid - 1 
					
			else: 
					left = mid + 1 
					
		return -1 	

```





Let's understand the pseudo-code:



```cpp
function binary_search(array, target) 
```

The `binary_search` function takes a sorted array and a target element to find.



```cpp
left = 0 
right = length(array) - 1
```

Sets `left` and `right` pointers to the beginning and end of the array, defining the initial search space.



```cpp
while left <= right 
```

The loop continues until (left <= right).



```cpp
mid = (left + right) / 2 
```

Calculates the middle index of the current search space.



```cpp
if array[mid] == target:
		return mid 				               
```

If the element at the middle index matches the target, it returns its position.



```cpp
elif array[mid] > target: 
		right = mid - 1              
```

 If the middle element is greater than the target, it discards the right half of the search space and focuses on the left half.



```cpp
else: 
		left = mid + 1              
```

If the middle element is less than the target, it discards the left half of the search space and focuses on the right half.



```cpp
return -1 	
```

If the loop finishes without finding the target, it returns -1 to indicate it's not present in the array.





Now that you have understood the concept of binary search, you'll implement it in the next lesson.
