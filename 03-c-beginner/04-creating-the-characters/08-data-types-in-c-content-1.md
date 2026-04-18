Okay,

So, how did you create variables in C++?



Well, first, you have to decide on a ***Data Type***!

And then create the variable!



> **💡PRO TIP: *****Data Type*** 
> Data types are a fundamental concept in programming that define the kind of data a variable can hold. They specify the size, format, and range of values that can be stored in a variable.



**SAMPLE CODE: Creating Variables in C++**

```cpp
int age = 30;
float weight = 60.45f;
double height = 1.75;
char grade = 'A';
bool isStudent = true;
string name = "John Doe";
```



But how will you create these variables in C#?

**SAMPLE CODE: Creating Variables in C#**

```csharp
int age = 30;
float weight = 60.45f;
double height = 1.75;
char grade = 'A';
bool isStudent = true;
string name = "John Doe";
```



Do you see any difference?

Well, I don't!

So, is creating variables exactly the same in both languages?

Well no.

Let's see



## Similarities


---



- Both languages have similar basic data types: int, double, char, bool, and string.
- The syntax for declaring and initializing variables is nearly identical.



## Differences


---

- String type:
- - In C++, `string` is part of the Standard Template Library (STL) and requires including the `<string>` header.
  - In C#, `string` is a built-in type and is actually an alias for `System.String`.
- Unsigned types:
- - C++ has unsigned versions of integer types (e.g., unsigned `int`, `unsigned long`).
  - C# also has unsigned types (e.g., `uint`, `ulong`), but they're less commonly used.
- Decimal type:
- - C# has a built-in decimal type for high-precision decimal calculations.
  - C++ doesn't have a built-in decimal type, but libraries can provide similar functionality.
- Size of basic types:
- - In C++, the size of basic types can vary depending on the platform.
  - In C#, the size of basic types is fixed across all platforms.



![Data Type Size Table](/Full-Stack-Game-Development/images/439233782906cff5.png)

**Size of Data Types: C++ vs C#** 





Although Data Types are similar to a great extent in both languages, you can refer to the official documentation to expand your knowledge!

There are many Data Types apart from the common ones.



> **🧠MORE BRAINS: Data Types in C# - Official Documentation **
> Link: https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types
