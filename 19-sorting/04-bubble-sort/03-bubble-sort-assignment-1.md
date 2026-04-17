# **Tasks**


---

## Implement Bubble Sort


---

## [IN A REPLIT PROJECT]



**TODO: In this assignment, you will implement the Bubble Sort algorithm in C++. **



> **Bubble Sort** repeatedly steps through the array, comparing and swapping adjacent elements if they are in the wrong order. This process is repeated until no more swaps are needed, resulting in a sorted array.



**Your task is to implement the **`**processBubbleSort**`** function to sort an array in ascending order.**



You are given the following code to start with.```cpp
#include <iostream>
using namespace std;

// Function to sort the array using bubble sort algorithm.
void processBubbleSort(int arr[], int n) {
  // Your code here
  
}

void displayArray(int arr[], int n) {
  for (int i = 0; i < n; i++) {
    cout << arr[i] << " ";
  }
  cout << endl;
}

// Function to dynamically allocate an array and fill it with random values.
void fillDynamicArrayWithRandomValues(int** arr, int* n) {
    cout << "Enter the size of the array: ";
    cin >> *n;
    *arr = new int[*n];
    srand(time(0)); // Seed for random number generation
    for (int i = 0; i < *n; i++) {
        (*arr)[i] = rand() % 1000; // Fill with random numbers between 0 and 999
    }
}

int main() {
    int* arr;
    int n;
    fillDynamicArrayWithRandomValues(&arr, &n);
    cout << "Unsorted array: ";
    displayArray(arr, n);
    processBubbleSort(arr, n);
    cout << "Sorted array: ";
    displayArray(arr, n);
    delete[] arr; // Deallocate dynamically allocated memory
    return 0;
}

```





**Implement the **`**processBubbleSort**`** function:**

1. Traverse from left, compare each pair of adjacent items and swap them if they are in the wrong order.
2. In this way, the largest element is moved to the rightmost end. 
3. This process is then continued to find the second largest and place it, and so on, until the data is sorted.
4. To optimize your implementation, add a flag to detect if the array is already sorted and `break` out of the loop early.



**Input 1:** `arr: [64, 34, 25, 12, 22, 11, 90]`

**Output:**

`**Unsorted array: 64 34 25 12 22 11 90 **`

`**Sorted array: 11 12 22 25 34 64 90**`



**Input 2:** `arr: [10, 1, 8, 3, 6]`

**Output:** 

`**Unsorted array: 10 1 8 3 6**`

`**Sorted array: 1 3 6 8 10**`



**Input 2:** `arr: [-2, 5, 0, 8, -1]`

**Output:** 

`**Unsorted array: -2 5 0 8 -1**`

`**Sorted array: -2 -1 0 5 8**`



# Submission Instructions:


---



1. Submit your Replit link for this assignment
