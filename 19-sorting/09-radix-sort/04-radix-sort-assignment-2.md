# **Tasks**


---

## IMPLEMENT Radix SORT


---

## [IN A REPLIT PROJECT]



**TODO: In this assignment, you will implement the Radix Sort algorithm in C++.**



> **Radix Sort** is a non-comparative sorting algorithm that sorts numbers by processing individual digits. It sorts digits from least significant digit (LSD) to most significant digit (MSD) or vice versa using Counting Sort.
> 
> **Counting Sort** is a sorting method that organizes numbers by counting how many times each number appears in a list. It then places each number in the list according to its count, arranging them in ascending order.



**Your task is to implement the **`**countSort**`**, **`**radixSort**`**, and **`**processRadixSort**`** functions to sort an array of integers in ascending order.**



You are given the following code to start with.

```cpp
#include <iostream>
using namespace std;

// Function to perform Counting Sort based on digit place (1s, 10s, 100s, etc.)
void countSort(int arr[], int n, int exponent) {
    // Your code here
}

// Function to perform Radix Sort on the array.
void radixSort(int arr[], int n) {
    // Your code here
}

// Function to initiate the Radix Sort process.
void processRadixSort(int arr[], int n) {
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
    processRadixSort(arr, n);
    cout << "Sorted array: ";
    displayArray(arr, n);
    delete[] arr; // Deallocate dynamically allocated memory
    return 0;
}

```





**Implement the **`**countSort**`**, **`**radixSort**`**, and **`**processRadixSort**`** functions:**

1. Counting Sort Function (`**countSort**`):
2. - Performs counting sort based on the digit place specified by `exponent` (1s, 10s, 100s, etc.).
  - Uses a `count` array to store counts of occurrences of each digit.
  - Modifies the original array based on counts and digit positions.
3. Radix Sort Function (`**radixSort**`):
4. - Determines the maximum element in the array to know the number of digits.
  - Applies `countSort` for each digit place (from least significant to most significant).
5. Process Radix Sort Function (`**processRadixSort**`):
6. - Initiates the Radix Sort process by calling `radixSort` with appropriate parameters.



**Input 1:** `arr: [64, 34, 25, 12, 22, 11, 90]`

**Output:**

`**Unsorted array: 64 34 25 12 22 11 90**`

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
