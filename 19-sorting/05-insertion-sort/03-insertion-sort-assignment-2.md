# **Tasks**


---

## IMPLEMENT INSERTION SORT


---

## [IN A REPLIT PROJECT]



**TODO: In this assignment, you will implement the Insertion Sort algorithm in C++.**



> **Insertion Sort** iterates through the array, inserting each element into its correct position in the sorted portion by shifting larger elements to the right, building a sorted array one element at a time.



**Your task is to implement the **`**processInsertionSort**`** function to sort an array in ascending order.**



You are given the following code to start with.

```cpp
#include <iostream>
using namespace std;

// Function to sort the array using insertion sort algorithm.
void processInsertionSort(int arr[], int n) {
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
    processInsertionSort(arr, n);
    cout << "Sorted array: ";
    displayArray(arr, n);
    delete[] arr; // Deallocate dynamically allocated memory
    return 0;
}
```





**Implement the **`**processInsertionSort**`** function:**

1. Traverse from the second element to the end of the array.
2. For each element, compare it with the elements in the sorted portion of the array and shift the sorted elements to the right if they are greater than the current element.
3. Insert the current element into its correct position.



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
