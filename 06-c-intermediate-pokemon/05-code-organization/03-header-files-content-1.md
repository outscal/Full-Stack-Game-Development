Before starting this lesson, I want to ask you a question,

Have you ever seen any construction site?



If you have, then you might know that while building a house,

We first create the structure of the house 

and then we implement all the functionalities inside each room.

Which makes it easier for us.

 

Now if I want to cook, 

then I can simply go to the kitchen,

without having a tour of the entire house to know where the kitchen is,

because I already know the structure of the house.



![](https://cdn.discordapp.com/attachments/1269892230274089043/1285486620950134866/file-N3pqptugHxbzr6DdNEdexmd6.png?ex=66ea7235&is=66e920b5&hm=7bac4578a035ba188d6198d467a9a6efd8db69c29ce20b27610a7a31956ebfcd&)





You will also use the similar approach to write the code.

If you have an organized codebase with different classes in different files

and a structured file organization, 

Won't it be easier for you to update and manage all the changes in your code? Yes, it is.



In the previous lesson,

when you were studying about separating classes into different files 

You came across `.hpp` and `.cpp` files.

You were told that `.hpp` files contain the declarations and `.cpp` files contain the definitions.



**But what is Declarations and Definitions?**



In Programming, 

**declaration** is basically announcing that something exists.



When you declare a variable, or a function,

the compiler gets to know that the variable or function exists.



Let's understand this with an example.



```cpp
int Add (int num);
```



In the above line of code,

you can see that, I have written a function.



At this moment, the compiler knows that a function `Add()` exists,

with int return type and taking an integer argument `num`.





But what will happen if you call this function?

It will throw you an error.



Because the compiler doesn't know what the `Add` function does.

It just knows that a function `Add` exists,

and that is what declarations is.



Now let me explain to the compiler, 

what `Add` function will do when it is called.



```cpp
int Add (int num){

//defining the function Add
	num += num;
	return num;
	
};
```

 

If you call the `Add` function now and pass the value 4 to it 

It will give you 8 as the output.



Because I have told the compiler to double the num when `Add` is called. (4 + 4 = 8)



What I did above is known as **defining the function**,

that I had declared earlier.




---



Now that you know what declaration and definition is,

let's see what header files and source files are.



You know that all the declarations go to header files,

and all the definitions go to source files.



But why do we need to separate declarations and definitions in different files?



Suppose we are working on a multi-player game together.

I am creating a weapon class for different weapons that will be used in the game,

and you are creating the Player class.



The Player class will need to use different methods in the weapon class, 

But it will be tiring if you had to go through all the methods in the weapon class, 

just to know which method in the weapon class will be used in the Player class.



What if I add any other method in the weapon class that you will need in your Player class.

You again, had to go through the entire class to find that method.



But if I create a separate header file that will contain all declarations,

then it won't be a big deal for you even if I make any changes to my part of the code.



It is very similar to a book's index page.

Imagine going through an entire book,

because you don't know where the topic is, 

that you want to study.



So, it's always a best practice to write declarations and definitions in separate files.



> **NOTE**: The extension for header files is `.hpp`/`.h` and the extension for source files are `.cpp`



But how will the source file know,

where the declarations of the methods and data members are present, 

that are defined in it.



While coding, 

you always use `#include <iostream>` on the top of your main file.



Why do you write that?

Why do you write that at the top of your file and not at the bottom?

Can you write that in the middle?



Let's understand this with a TODO



> **TODO: **
> ✅ Create a file in the main directory and name it header.hpp

> ✅ Inside the header.hpp file just write a closing curly bracket `}`



Example code:```cpp
}
```



> **TODO: **
> ✅ In your `main.cpp` file, use `#include "header.hpp"` at the end of your main function instead of closing curly bracket `}`

 



Example code:```cpp
#include<iostream>
using namespace std;

int main() {

	cout<<"file included"<<endl;
	
#include "header.hpp"
```



Now run the code.

Is it working? Yes, it is.



`#include` keyword includes a file in another file as if the entire file is written in that place.

You can think of this as a way of including 100 of lines of code written on another file in single line.



Now in `#include <iostream>`

`#include` is a **preprocessor directive** that tells the compiler to copy the contents of the specified file(iostream) into the program before compilation.



`iostream` is a standard file in Cpp,

that includes all the input/output functions that you use while coding. 

For example: cout, cin etc.



So, if you want to use these functions in your main function,

you need to include them before the main function.



That's why you write `#include <iostream>` at the top of your main.cpp file,

and not at the bottom or middle.



 `<>` is used for pre-defined header files,

which includes all the functions that are commonly used by the programmers,

like the iostream file which includes all input and output operations. 



If you want to include files that you have defined for your specific needs, 

then you have to use `" "` instead of `<>`
