Welcome to the last lesson of this module!

In this lesson, we will compare both search algorithms: **Linear search** and **Binary search**. 

Each has its own way of finding the target element, so let's explore them.



![linear vs binary](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/06_12_2024__07_08_53.png)

*Comparison between linear search and  binary search*



But how to select the right algorithm for any situation?



Selecting the right search algorithm, linear or binary, relies on various factors. 

This includes the nature of your data, the requirements of your application, and the constraints you're working under.



Wouldn't it be easy for you if you already knew under what scenarios one algorithm can be preferred over the other?

Definitely yes! You won't always have to strain your brain to figure out the best choice for every situation.



So, here are some scenarios where linear search becomes the preferred choice over binary search:-

1. **Unsorted Data**

- - ***Scenario***: Your data is not sorted, and you cannot afford the time or resources to sort it.
  - ***Explanation***: Linear search works well because it doesn't require any order in the data. It can simply check each element one by one. Binary search, on the other hand, needs the data to be sorted in a specific order to function.



1. **Small Data Sets**

- - ***Scenario***: The data set is relatively small.
  - ***Explanation***: With small datasets, the ease of linear search and its minimal overhead can outperform binary search. Since sorting isn't needed for linear search, its constant factor is lower, making it quicker for small collections.



1. **Single or Few Searches**

- - ***Scenario***: You need to perform a single search or only a few searches on the data set. 
  - ***Explanation***: If you only search occasionally, the overhead of sorting required for binary search might not be justified. Linear search performs well for a small number of search operations.



1. **Streaming or Real-Time Data**

- - ***Scenario***: The data arrives in a stream, and you need to search in real time.
  - ***Explanation***: In real-time scenarios where data arrives continuously and requires immediate searching, linear search is ideal. It can be applied directly to the incoming stream without waiting for complete data sorting.



1. **Non-Indexed Data Structures**

- - ***Scenario***: You're working with data structures that do not support random access efficiently, like linked lists.
  - ***Explanation***: For data structures where randomly accessing elements is slow, like linked lists, then linear search becomes the right choice because binary search jumps to the middle element quickly, whereas linear search iterates through each element in these structures.



1. **Simplicity and Ease of Implementation**

- - ***Scenario***: You need a simple and straightforward search algorithm.
  - ***Explanation***: Linear search is easy to implement and understand, making it suitable for quick and dirty searches, prototyping, or when algorithm complexity is not a primary concern.



Remember, the best search method depends on your specific needs. So, always choose accordingly!



So, the next time you need to search for something, remember the **sticks**! 

Choose linear search for a quick and easy approach, but binary search should be the choice for larger or sorted data.



Congratulations on acing the search algorithms!

And we're done with this module.



**See you in the next module!**
