In previous lesson, you have learned about pointers.

pointers are variable that point to memory address of a variable.

Let's Double click on memory address.



Imagine your computer's memory as a vast collection of storage boxes. 

Each box represents a memory location.

And every variable you declare in your program resides within one of these boxes.



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_07_2024__02_52_07.gif)





A **Pointer**, then, holds the address label of a specific box instead of the content directly.

Pointers are special variables that store memory addresses instead of actual values. 

They literally **"point" to locations in memory** where data is stored.



# Memory Address


---



Can you find out the address of your variable ?

Can you find out the value stored on that memory address ?  which you created.



Let's again Look to this code :

```cpp
int a = 10;
int * ptr =  &a;
// print ptr 
```



As we already discuss this in our previous module.

Here, `ptr `store the address of variable `a `or point to `a`.



> **TODO:**
> ✅ Try to print the variable` ptr` in replit.




What is the output, you noticed ?

is there any wage output print on the screen ?



Yes, This is Memory Address where variable `a `stored.



Code```cpp
#include <iostream>
using namespace std;
int main() {
    int a = 10;  // Declare a variable
    int *ptr = &a;
    cout << "The address of a is: " << ptr << endl;  // Print the address of the variable a
    return 0;
}
```

 

**Output : **

```cpp
The address of num is: 0x7ffd025c4fd4
```



Actually, this is hexadecimal number which denote memory address in your hard disk.



But Wait, is there different output you noticed ? than this.



Yes, this address changes depending on the machine and even each time you run the program. 

It's based on how your computer allocates memory, so don't worry if the address looks different every time



# Dereference Operator


---



Now suppose you have a pointer of a variable.

and you knows it stores the address of that variable.



What if you have only address of Variable ?

You don't know the actual value of variable.



is there any way to find the the value of variable, stored at that address ?



Yes, It is same like if you have address of home then you can reach home.

So, if you have pointer of variable means address of that variable.



You can  know the value stored at that address. But How ?

Now,** Dereference Operators (*) **Comes In ! 



Let's Break Down Dereference.

What is reference ?

so Basically , a pointer variable stores the address of some variable.

This means it refers that variable or address.



and Dereference means finding out value stored at that address.



> **TODO:**
> ✅ Try to print the variable` *ptr` in an online compiler.

> ✅ Imagine , you don't have` a` variable, only have `ptr` .





Code```cpp
#include <iostream>
using namespace std;
int main() {
    int a = 10;  // Declare a variable
    int * ptr = &a;
    cout << "The Value at  address ptr  " << *ptr << endl;  //  *ptr ----> dereferecing the ptr
    return 0;
}
```



Great, Now you knows How to Find the exact value of variable, using pointer variable.



![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_07_2024__03_41_54.png)





Now, you might be confused between` &` and` *.`

So let's take a quick recap.



**&** (Address-of operator) : Gives the **address** of a variable.

 `&variable` returns where the variable is stored in memory.



*** **(Dereference operator) : Retrieves the **value** stored at a given address.




---



Let’s add a fun twist to our pointer adventure! 

*Did you know that a pointer can point to another pointer?*



***Yes****, Pointer Can store the address of pointer variable.*

```cpp
int a = 10;
int * ptr = &a;
// ptr store the address of a 

int ** ptr2  = &ptr;  // ptr2 store the address of ptr.
```



- `**ptr**` is a pointer to an `int`.
- `**ptr2**` is a pointer to `ptr`, which means it stores the address where `ptr` is located.
- and so on.

![img](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_07_2024__05_58_52.png)





# Importance of Memory Address


---



Without these addresses, pointers, which are used to reference data, wouldn’t have anything to point to. 

Knowing the memory address lets you directly access or modify the data stored there.

Making programs more efficient and easier to manage.





So, we have seen so far that when we create a variable, memory is allocated to it.
Now, can you think how many variables we can create until our memory is full?
Since we have limited memory in our system.



Sometimes, we keep our memory engaged even when we don’t need that variable.
It slows down our program if too much unnecessary memory is used.



So, memory management is crucial.
In the next lesson, you will learn about `new` and `delete` to manage memory.
