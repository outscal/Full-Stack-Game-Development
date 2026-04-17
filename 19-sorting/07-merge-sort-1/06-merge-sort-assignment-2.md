# **Tasks**


---

## IMPLEMENT MERGE SORT


---

## [IN A REPLIT PROJECT]



**TODO: In this assignment, you will implement the Merge Sort algorithm in C++.**



> **Merge Sort** is a divide-and-conquer algorithm that recursively divides the array into halves, sorts each half, and then merges them back together in sorted order.



**Your task is to implement the **`**merge**`**, **`**mergeSort**`**, and **`**processMergeSort**`** functions to sort an array in ascending order.**



You are given the following code to start with.

```cpp
#include <iostream>
using namespace std;

// Function to merge two sorted halves of the array into a single sorted array.
void merge(int arr[], int left, int mid, int right) {
    // Your code here
}

// Function to recursively divide the array and merge the sorted halves.
void mergeSort(int arr[], int left, int right) {
    // Your code here
}

// Function to initiate the merge sort process.
void processMergeSort(int arr[], int n) {
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
    processMergeSort(arr, n);
    cout << "Sorted array: ";
    displayArray(arr, n);
    delete[] arr; // Deallocate dynamically allocated memory
    return 0;
}

```





**Implement the **`**merge**`**, **`**mergeSort**`**, and **`**processMergeSort**`** functions:**

1. Merge Function (`**merge**`):
2. - Initialize temporary arrays to hold the left and right halves.
  - Merge the elements from left to right halves, comparing elements and placing them in order into the original array.
3. Merge Sort Function (`**mergeSort**`):
4. - Divide the array into halves until each sub-array has one element.
  - Recursively call `mergeSort` on each half.
  - Merge the sorted halves back together using the `merge` function.
5. Process Merge Sort Function (`**processMergeSort**`):
6. - Initiates the merge sort process by calling `mergeSort` with appropriate parameters.



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
