You've already learned about pointers in C++.

In this lesson, let's dive into a closely related concept: **References**.



## DEFINITION



Let’s briefly revisit pointers before moving to references.



**Pointers**:

- A pointer is a variable that holds the address of another variable.
- You can use pointers to access and modify the data stored at that address.
- Plus, you can change a pointer's target, meaning it can point to different variables during its lifetime.



You already know what pointers are.

Let's go over what a reference is in-depth.



**References**: 

A reference is an alias(another name) for an existing variable. 

- When you create a reference, you essentially tell the compiler, "From now on, I want to use this *new name* to refer to this existing variable." 
- Therefore, any operations you perform using the reference directly affect the original variable it is tied to.



It is created with the `**&**` operator in the declaration and **must be initialized to a variable when it is created**.

Once set, a reference cannot be changed to refer to a different variable; it always refers to the initial variable to which it was bound.



Let’s look at the syntax and usage of a reference to understand all of this better!



## **SYNTAX AND USAGE**



Let’s start with things you know and then slowly increase the difficulty with each step.

Make sure you run all the examples in **Replit**, otherwise you won't really understand the concept.



> ✅**TODO :** Run the following code in `**Replit**` to get a better understanding of what is happening.



Let’s start with pointers first since you already know how they work. ( no need to run the following in `**Replit**` )

```cpp
int a = 10;
int* p = &a;  // p stores the address of a
*p = 20;      // modifies a through the pointer
```



Now, run the following code to see **how you can create a reference**.



Level 1```cpp
#include <iostream>

int main() {
    int x = 10;
    int& ref = x;  // Reference to x

    std::cout << "Reference example:" << std::endl;
    std::cout << "x: " << x << std::endl;
    std::cout << "ref: " << ref << std::endl;

    ref = 30;  // Change the value of x through the reference
    std::cout << "After ref = 30;" << std::endl;
    std::cout << "x: " << x << std::endl;
    std::cout << "ref: " << ref << std::endl;

    return 0;
}


```





Now that you know the basics, let’s step it up.

The following code will show that** a Reference Must be Initialized and Cannot be Changed:**





level 2

```cpp
#include <iostream>

int main() {
    int x = 10;
    int y = 20;
    int& ref = x;  // Reference to x

    std::cout << "Reference must be initialized and cannot be changed:" << std::endl;
    std::cout << "Initial values - x: " << x << ", y: " << y << std::endl;
    std::cout << "ref (initially bound to x): " << ref << std::endl;

    ref = y;  // This changes the value of x, not the reference itself
    std::cout << "After ref = y;" << std::endl;
    std::cout << "x: " << x << std::endl;
    std::cout << "y: " << y << std::endl;
    std::cout << "ref (still bound to x): " << ref << std::endl;

    return 0;
}


```







If you ran the above code, you might have noticed something interesting.

`**ref**` is nothing more than another name for the variable it is initialized with → `‘x’`.



This is different from pointers because pointers are actual variables, you can change what a pointer points to.

However, a reference is just another way of calling the variable it was initialized with. **It is not a new variable.**



Finally, let’s see how a reference is passed to a function:



Level 3```cpp
#include <iostream>

void modifyWithPointer(int* p) {
    *p = 100;
}

void modifyWithReference(int& r) {
    r = 200;
}

int main() {
    int x = 10;
    std::cout << "Initial value of x: " << x << std::endl;

    modifyWithPointer(&x);  // Passing pointer to function
    std::cout << "After modifyWithPointer(&x): " << x << std::endl;

    modifyWithReference(x);  // Passing reference to function
    std::cout << "After modifyWithReference(x): " << x << std::endl;

    return 0;
}

```





The above code block might look confusing, but is quite straightforward.



The pointer function takes the address of `**x**` ( A pointer is just the address of a variable ).

The reference function directly takes the variable, which is what the reference is ( The reference is just an Alias for the var ).



Now that you know what a reference is, let’s list down the differences between a reference and pointer.



![placeholder](/Full-Stack-Game-Development/images/2b208d9000704b1c.png)






The table above shows the differences between pointers and references.

Don’t worry too much about things like pointer arithmetic as you don’t need it at the moment.



You might also have the question, ‘is it better to use a pointer, or should I use references?’

Honestly, there is no clear answer. It really depends on what you are tying to achieve.



Finally, the above table mentions the following line:

“Preferred for passing objects that must not be modified and when *passing by value* is too expensive. “



You might be wondering what **‘passing by value’** even means.

Let’s discuss that in detail in the next lesson!
