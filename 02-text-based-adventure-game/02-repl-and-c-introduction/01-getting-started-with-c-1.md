<iframe src="https://www.loom.com/embed/84487f6a3a4f42758adff94191847d48" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





## **Understanding Your First C++ Program**


---

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World! \n";
    return 0;
}
```



The **'Hello World'** program is a classic for a reason. Here's a breakdown:

- Each code file you write in C++ will have a `.cpp` extension. This extension indicates that the file contains C++ source code. For example, `example.cpp` is a common filename for a C++ source file.
- In C++, `main()` is a special function. It serves as the entry point for the execution of the program. When you run a C++ program, the execution starts from the `main()` function. It's mandatory to have a `main()` function in a C++ program. without it, the program won't compile or execute.
- In the above program, we're introducing the concept of **Functions**. A function is a self-contained block of code that performs a specific task. It's a reusable unit of code that can be called from other parts of a program. In the above  program, we have a function called `**main()**`.
- The `main()` function typically has this signature:

```cpp
int main() {
    // Your code goes here
    return 0;
}
```

- Here's what each part does:
- `int`: It specifies the return type of the `main()` function *(A value returned as output once the code is executed)*. It indicates the status of the program after execution. A return value of `0` typically signifies successful execution, while a non-zero value often indicates an error or abnormal termination.
- `main()`: This is the name of the function and the entry point of the program.
- `{}`: These curly braces contain the body of the `main()` function, where you write the instructions for what you want your program to do.
- `return 0;`: This line is the exit point of the `main()` function. It returns an integer value (`0` in this case) to the operating system, indicating that the program terminated successfully.

- `cout` is the key here. it's used to display text on the console. (console out --> cout)
- We explore the power of strings, using `cout` to output our message onto the screen.
- `\n` is a symbol which is used as a "**line terminator**" everything written after this symbol moves to a new line.
- iostream is an inbuilt C++ library which contains helpful functions like `cout` related to input and output operations.
- Variables step in! They're containers storing different types of data. Here, we introduce the `string` type for names and `int` for numbers.
- Variables must be declared before they can be used. Declaration involves specifying the variable's data type and name. Initialization is giving the variable an initial value at the time of declaration.
