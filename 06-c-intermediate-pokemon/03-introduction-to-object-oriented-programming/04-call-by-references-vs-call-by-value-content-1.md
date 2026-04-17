![ ](https://media1.tenor.com/m/57_zV98BB-AAAAAC/coffe-cup.gif)



In the previous lesson, you saw '**&**' symbol for the first time.

You used it while passing a parameter in the function.



Did you wonder what it can be?

In programming, it is known as **call by reference**.

```cpp
returnType functionName (type &parameter){
.........
}
```



Till date, you have passed parameters in the functions normally,

without any special symbol.

That is known as **call by value**.

```cpp
returnType functionName (type parameter){
.........
}
```



So, these are the two ways to pass parameters into the functions.

- **Call by reference**
- **Call by value**





# Call by value


---

If some variable or some data structure is passed as **call by value**,

then, a new copy gets created of that variable,

and that copy is passed to the function.



```cpp
int a = 5;
int b = a;
```



Look at the above code snippet,

'b' is a copy of 'a'.



Now, if you change the value of 'b',

The value of 'a' is not affected.



That is the exact definition of **call by value**.

So, the actual code will not be changed in this case.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_13_2024__10_16_06.png)







# Call by reference


---

It is just the opposite of calling by value.

No new copy is created here.



Instead, the **reference** of the actual variable or data structure is passed to the function.

which will result in affecting the actual data.



By using the '&' symbol,

you can pass any variable as **call by reference**.



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_13_2024__10_34_12.png)







# Coding Time!


---



Example 1```cpp
#include <iostream>
using namespace std;

void updateName(string name){
    
    string to_add = "is cool!!";
    name = name + to_add;
    
}

int main() {
    string name = "Outscal ";
    updateName(name);
    
    cout << name << endl;

    return 0;
}
```



I want to give you a task,

for that, you need to go through the above example.



Now tell me, without running the code,

what do you think?

What would be it's output?



Is your answer "Outscal is cool!!"?



Let's run the code and see.



Output```plain
Outscal
```





What? But, How?

The string **name** has been updated in the `**updateName()**` function.

Then, why did you not get the updated string as the output?



Okay, do one thing, 

add '&' symbol while passing the string in the function.



Your code should look like the example given below.



Example 2```cpp
#include <iostream>
using namespace std;

void updateName(string &name){
    
    string to_add = "is cool!!";
    name = name + to_add;
    
}

int main() {
    string name = "Outscal ";
    updateName(name);
    
    cout << name << endl;

    return 0;
}
```



Now, run it and check the output.



Outscal```plain
Outscal is cool!!
```



Wow, isn't it a magic?

By just adding a single symbol,

you did what you wanted.



Actually, no,

there is nothing like magic in coding.

Everything is based upon the rules and syntax.



Let me explain what happened in the above code.



In example 1,

the original string `name` was not passed to the `updateName` function.

The computer created a copy of the original string `name` inside the `updateName` function.



And let me remind you,

whenever a variable is created inside a function.

Then, the **scope** of that variable is limited to that function only.



That means the variable will be initialized,

will be used in the function,

and, as soon as the function gets executed entirely,

that variable will be automatically deleted.



So, when the function `updateName` was called,

it updated the copied string of `name`,

then, the function got terminated,

and the computer deleted the copied string.



Which means the original string remained unaffected.





But, when you added '&' symbol in example 2,

you passed the reference of the original string.

That means, the original string `name` was provided to the function.



So, whatever changes `**updateName()**` function did on the string,

got reflected in the `cout` statement
