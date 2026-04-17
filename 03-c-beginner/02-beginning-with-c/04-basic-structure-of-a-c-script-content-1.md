![Code with Fancy Words](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/09_05_2024__09_58_46.png)

**Code with fancy words**

What are these fancy words?

What is `**Main()**`?

What is `**static**`?

What is `**class Program**`?

What is `**using System**`?



# `Main()` Function


---



In C#, `Main()` is the entry point of a console application. It's the method that the operating system calls when the program is executed.

It is similar to the C++ `main()` function.



> **PRO TIP **💡**:** `***Main()***`*** ***

> Remember, in C#, the `Main()` starts with an uppercase 'M'. But in C++, the `main()` begins with' m'.



🧠MORE BRAINS: Why is ‘M’ uppercase in C# `Main()`?

This is because of ***Microsoft!*** 

Microsoft is the maker of C#, and they recommend this naming convention in their official [Naming Guidelines](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names?source=recommendations).

This naming convention is **PascalCase**: The first letter of each function/method name is capitalised.


While the compiler would recognize `main()` as a method, it won't treat it as the program's entry point. That’s because the compiler specifically looks for a method named "Main" (with a capital 'M') when determining the program's entry point.





# Program Class


---



You might have noticed that, unlike in C++, the `Main ()` in C# is inside a class called `Program`. 

Why?



C++ allows Global Functions that can be created outside any class and called from any class.

But C# restricts this, and functions can only be created inside a class.

So, it is clear that `Main()` has to be inside a class!



But which class?

Right now, it is inside the `class ``**Program**`**. **"Program" is just a default name. You can put `Main()` inside any other class.



# Why `Main()` is defined as `static`?


---

Did you notice🤔?

In C #, `Main()` is defined as `static`. But why is that?



To call a function of a class, you need to create its object, right?

You must remember this from C++ Beginner.



Well now, to call `Main()`, the compiler should be able to call it without creating the object of its parent class(Program class).

And `***static***` is a way to do this.



> **PRO TIP **💡**:** ***W*****hy is **`**Main()**`**, **`***static***`**?**

> Here, `Main()` is `*static*` so that it can be called without creating the object of its parent class(Program class).
> `***static***` keyword has a lot more to it that you'll understand in detail in the ***C++ Intermediate Module.***



# `using System`


---



What is this?

Why is this?



Well, you are printing a message using `Console.Writeline()`, right?

![Console.Writeline()](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/09_05_2024__10_08_06.png)

`***Console.Writeline()***`



Here, `Console` is a class, and `Writeline()`  is its function.

So you are using a class in this program, but this class is not present in this file?

Well, then, how does the compiler know which class you are exactly talking about?



This is where **Namespaces** come in.



> **PRO TIP 💡:** ***Namespaces***
> 
> Namespaces organise code by grouping related classes, functions, variables, etc., under a unique name. They are helpful when there are multiple scripts. They act like a container that holds related objects together.



So when you write `using System`, you basically tell the compiler that you want access to all the objects inside the `System` namespace.  

And guess what? The `console` class is inside the `System` namespace. 



> **PRO TIP 💡:** `***using***`*** in C#***** and *****C++***
> It creates an alias for a namespace or imports types defined in other namespaces.
> 
> `**using**` keyword exists in both C# and C++ and serves the same purpose.
