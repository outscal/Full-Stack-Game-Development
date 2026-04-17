This is a quick lesson.

Here, you will experiment with different ways to print messages on the console using the Console class of C#.



> **PRO TIP 💡:** `***Console***`*** Class***
> 
> It is a class in `System` namespace, which is used to show error messages, taking input and printing messages in the console.



You have already used `Console.Writeline()`, let's dive deep into it.

# `cout` vs `Writeline`()


---



In C++, you used `cout` to print messages in the console.

`cout` and `Console.WriteLine()` does the same thing, but they are still different from each other.

Let’s see how...

 

## `cout`:


---

It uses the insertion operator (“`<<`” ) to show multiple outputs and requires `#include <iostream>` library and the use of the `std::` namespace or `using namespace std;`.

**SAMPLE CODE**

```cpp
std::cout << "Hey, there " << std::endl 
<< "Enjoying the content so far? " <<std::endl;
```



## `Console.WriteLine()`:


---

It uses parentheses ( “`*()*`” ) to pass the string or variables to print the message. There is no need for any operator. 

**SAMPLE CODE**

```csharp
Console.WriteLine("You want some Pizza??");
```



***Note:**** *`*Console.WriteLine()*`* isn’t the only way to print messages in C#.*



# `Console.write()` vs `Console.writeline()`


---



C# also has `Console.Write()`, which does the same thing as `Console.WriteLine()` but with a slight twist.

What is that slight twist you are asking?



## `Console.WriteLine()` :


---

It prints the message and then automatically moves the cursor to the next line.

**SAMPLE CODE**

```csharp
Console.WriteLine("Avengers");
Console.WriteLine("Assemble!");
```

**OUTPUT :**

```text
Avengers
Assemble!
```



## `Console.Write()` :


---



It prints the message but **does not** move the cursor to the next line.

**SAMPLE CODE**

```csharp
Console.Write("Avengers");
Console.Write("Assemble!");
```

**OUTPUT:**

```text
AvengersAssemble!
```



***ENOUGH OF C#!*****😡 ** 

In the next lesson, you'll print the story of the game!

Stay tuned to discover the story of the game 😉.
