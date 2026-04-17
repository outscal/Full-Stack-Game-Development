# **Tasks**


---

## IMPLEMENT IN-place MERGE SORT


---

## [IN A REPLIT PROJECT]



**TODO: In this assignment, you will implement the In-Place Merge Sort algorithm in C++.**



> **Merge Sort** is a divide-and-conquer algorithm that recursively divides the array into halves, sorts each half, and then merges them back together in sorted order.



**Your task is to implement the **`**inPlaceMerge**`**, **`**inPlaceMergeSort**`**, and **`**processInPlaceMergeSort**`** functions to sort an array in ascending order.**



You are given the following code to start with.

```cpp
#include <iostream>
#include <cstdlib> // for rand() and srand()
#include <ctime> // for time()

using namespace std;

// Function to merge two sorted sub-arrays in place.
void inPlaceMerge(int arr[], int left, int mid, int right) {
    // Your code here
}

// Function to recursively sort the array using Merge Sort.
void inPlaceMergeSort(int arr[], int left, int right) {
    // Your code here
}

// Function to initiate the Merge Sort process.
void processInPlaceMergeSort(int arr[], int n) {
    if (n > 1) {
        inPlaceMergeSort(arr, 0, n - 1);
    }
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
    processInPlaceMergeSort(arr, n);
    cout << "Sorted array: ";
    displayArray(arr, n);
    delete[] arr; // Deallocate dynamically allocated memory
    return 0;
}

```





**Implement the **`**inPlaceMerge**`**, **`**inPlaceMergeSort**`**, and **`**processInPlaceMergeSort**`** functions:**

1. In-Place Merge (`**inPlaceMerge**`):
2. - Initialize temporary arrays to hold the left and right halves.
  - Merge the elements from left to right halves, comparing elements and placing them in order into the original array.
3. In-Place Merge Sort Function (`**inPlaceMergeSort**`):
4. - Divide the array into halves until each sub-array has one element.
  - Recursively call `inPlaceMerge` on each half.
  - Merge the sorted halves back together using the `merge` function.
5. Process In-Place Merge Sort Function (`**processInPlaceMergeSort**`):
6. - Initiates the merge sort process by calling `inPlaceMergeSort` with appropriate parameters.



**Input 1:** `arr: [64, 34, 25, 12, 22, 11, 90]`

**Output:**

`**Enter the size of the array: 7**`

`**Unsorted array: 64 34 25 12 22 11 90**`

`**Sorted array: 11 12 22 25 34 64 90**`



**Input 2:** `arr: [10, 1, 8, 3, 6]`

**Output:**

`**Enter the size of the array: 5**`

`**Unsorted array: 10 1 8 3 6**`

`**Sorted array: 1 3 6 8 10**`



**Input 2:** `arr: [-2, 5, 0, 8, -1]`

**Output:**

`**Enter the size of the array: 5**`

`**Unsorted array: -2 5 0 8 -1**`

`**Sorted array: -2 -1 0 5 8**`



# Submission Instructions:


---



1. Submit your Replit link for this assignment
