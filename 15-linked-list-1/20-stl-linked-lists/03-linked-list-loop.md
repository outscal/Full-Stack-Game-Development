# **Tasks**


---

## detect a loop in linked list


---

## [IN A REPLIT PROJECT]



**TODO: In this assignment, you will implement a method to detect a loop in a linked list. **

**Your task is to implement the **`**detectCycle**`** function.**



You are given the following code to start with.```cpp
#include <iostream>

using namespace std;

// Node class represents a node in a linked list
class Node {
public:
    int data;       // Data stored in the node
    Node* next;     // Pointer to the next node in the list
};

// Function to detect a loop in a linked
bool detectCycle(Node* head) {
			// Start implemeting code below this line
}

int main() {

    // Create a sample linked list with a loop for testing 
    // Copy-paste start here
    Node* head = new Node();
    Node* second = new Node();
    Node* third = new Node();
    Node* fourth = new Node();
    Node* fifth = new Node();

    head->data = 1;
    head->next = second;
    second->data = 2;
    second->next = third;
    third->data = 3;
    third->next = fourth;
    fourth->data = 4;
    fourth->next = fifth;
    fifth->data = 5;
    fifth->next = third; 
    // Copy-paste end here

    // Check if there is a loop in the linked list
    if (detectCycle(head)) {
        cout << "Loop detected in the linked list." << endl;
    } else {
        cout << "No loop detected in the linked list." << endl;
    }

    // Clean up memory (free the allocated nodes)
    delete head;
    delete second;
    delete third;
    delete fourth;
    delete fifth;

    return 0;
}

```



**Implement the **`**detectCycle**`** function:**

1. Initialize two pointers, `slow` and `fast`, both starting at the head of the linked list.
2. Traverse the linked list using the two-pointers. The `slow` pointer moves one step at a time, while the `fast` pointer moves two steps at a time.
3. If `slow` and `fast` meet at some point, there is a loop in the linked list.
4. If `fast` reaches the end of the list (i.e., `fast` or `fast->next` becomes `nullptr`), there is no loop.



**Input 1**:

`LL: 1 2 3 4 5`



```cpp
		Node* head = new Node();
    Node* second = new Node();
    Node* third = new Node();
    Node* fourth = new Node();
    Node* fifth = new Node();

    head->data = 1;
    head->next = second;
    second->data = 2;
    second->next = third;
    third->data = 3;
    third->next = fourth;
    fourth->data = 4;
    fourth->next = fifth;
    fifth->data = 5;
    fifth->next = third;  
```



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_07_2024__07_17_01.png)



**Output**: `Loop detected in the linked list.`

**Explanation**: The last node with the value of `5` has its `next` pointer pointing to a node with the value of `3`. 



***For the rest of the Input copy-paste the input between copy-paste comment blocks***



**Input 2**:

```cpp
Node* head = new Node(); 
Node* second = new Node(); 
Node* third = new Node(); 
head->data = 1; 
head->next = second; 
second->data = 2; 
second->next = third; 
third->data = 3; 
third->next = nullptr;
```

**Output**: `No loop detected in the linked list.`



**Input 3**:

```cpp
Node* head = new Node(); 
head->data = 1; 
head->next = head;
```

**Output**: `Loop detected in the linked list.`



# Submission Instructions:


---



1. Submit your Replit link for this assignment
