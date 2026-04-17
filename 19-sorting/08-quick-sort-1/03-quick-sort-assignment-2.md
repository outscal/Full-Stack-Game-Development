# **Tasks**


---

## IMPLEMENT **Quick** SORT


---

## [IN A REPLIT PROJECT]



**TODO: In this assignment, you will implement the Quick Sort algorithm in C++.**



> **Quick Sort** is a divide-and-conquer algorithm that selects a pivot element and partitions the array into two sub-arrays around the pivot. Elements less than the pivot are placed before it, while elements greater than the pivot are placed after it. This process is applied recursively to sort the entire array.



**Your task is to implement the **`**partition**`**, **`**quickSort**`**, and **`**processQuickSort**`** functions to sort an array in ascending order.**



You are given the following code to start with.

```cpp
#include <iostream>
using namespace std;

// Function to partition the array and return the pivot index.
int partition(int arr[], int low, int high) {
    // Your code here
}

// Function to recursively sort the array using Quick Sort.
void quickSort(int arr[], int low, int high) {
    // Your code here
}

// Function to initiate the Quick Sort process.
void processQuickSort(int arr[], int n) {
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
    processQuickSort(arr, n);
    cout << "Sorted array: ";
    displayArray(arr, n);
    delete[] arr; // Deallocate dynamically allocated memory
    return 0;
}

```





**Implement the **`**partition**`**, **`**quickSort**`**, and **`**processQuickSort**`** functions:**

1. Partition Function (`**partition**`):
2. - Choose a pivot (the last element in the array).
  - Initialize `i` to `low - 1` and iterate `j` from `low` to `high - 1`.
  - If `arr[j]` is less than or equal to the pivot, increment `i` and swap `arr[i]` with `arr[j]`.
  - Finally, swap `arr[i + 1]` with `arr[high]` (pivot element) and return `i + 1` as the pivot index.
3. Quick Sort Function (`**quickSort**`):
4. - Base case: If `low` is less than `high`, partition the array using `partition`.
  - Recursively call `quickSort` on the left and right partitions.
5. Process Quick Sort Function (`**processQuickSort**`):
6. - Initiates the Quick Sort process by calling `quickSort` with appropriate parameters.



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
