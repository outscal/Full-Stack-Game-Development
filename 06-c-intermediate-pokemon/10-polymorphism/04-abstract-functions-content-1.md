In the last lesson,

you learnt about function overriding.



I explained it's importance,

and how it helps,

to handle multiple child classes from a base class pointer.



Before moving to abstract functions,

first I want to ask you a question.



Example 1```cpp
#include <iostream>
using namespace std;

class car{
public:
    virtual void engineDetails(){
        cout << "All the cars have engine!" << endl;
    }
};

class hondaCity : public car{
public:
    void engineDetails(){
        cout << "Honda City engine is of 1200cc" << endl;
    }
};

int main() {
    car* ptr = new hondaCity();
    ptr -> engineDetails();

    return 0;
}
```



In the above example,

the `engineDetails()` in `car` class has no meaning,

I am only concerned about  `engineDetails()` in `hondaCity` class.



So why am I even declaring `engineDetails()` in the base class?

If I remove it, I don't even have to use the **virtual** keyword.

Let's try to do it.



Example 2```cpp
#include <iostream>
using namespace std;

class car{
public:

};

class hondaCity : public car{
public:
    void engineDetails(){
        cout << "Honda City engine is of 1200cc" << endl;
    }
};

int main() {
    car* ptr = new hondaCity();
    ptr -> engineDetails();

    return 0;
}
```



Try to run the above code.

Did you also get an error similar to the one shown below?



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_17_2024__10_31_22.png)



*It is because,*

*when a base class pointer points to a child class object,*

*then, it can only access those data members and methods,*

*which are defined in the base class.*



That means, you have to declare `engineDetails()` function in the base class `car`,

even though you don't have to define it in the base class.



So, will you continue using the code as shown in example 1?



Actually, No.

There is one thing in programming that can help you.





# Abstract Functions


---



Abstract Functions can help you out,

for the issue that you faced in example 2.



Before explaining, first check out the syntax of an abstract function.

```cpp
virtual retunType functionName (parameters) = 0;
```



Since,

you very well know the difference between **Declaration** and **Definition**,

so, it will be easy for you to understand abstract functions.



Abstract functions don't contain any definition.

They are just **declared**.



*They are meant to be overridden in child classes.*



> **NOTE:** Abstract Function is also known as Pure Virtual Function



> **NOTE:** If a base class consists an abstract function, then that function must be *overridden* in all the child classes otherwise it will throw a compile error.





Example 3```cpp
#include <iostream>
using namespace std;

class car{
public:
    virtual void engineDetails() = 0;
};

class hondaCity : public car{
public:
    void engineDetails(){
        cout << "Honda City engine is of 1200cc" << endl;
    }
};

int main() {
    car* ptr = new hondaCity();
    ptr -> engineDetails();

    return 0;
}
```



Output

```cpp
Honda City engine is of 1200cc
```





# Coding Time!


---

So, you have understood

- Function Overriding
- Virtual Function
- Abstract Function



Now, it's time to implement your knowledge in the code of **Pokemon Game**.



Update `attack()` function to an abstract function in `Pokemon.hpp` file.

And remove the definition of `attack()` from `Pokemon.cpp`.





Pokemon.hpp```cpp
......
virtual void attack(Pokemon* target) = 0;
........
```



Since you have declared an **abstract function** in `Pokemon` class,

now you have to override `attack` function in all types of Pokemon child classes.



Let me show you some examples.



Caterpie.hpp```cpp
.....
void attack(Pokemon* target) override;
.....
```



Caterpie.cpp```cpp
.....
void Caterpie::attack(Pokemon* target){
    bugBite(target);
}
......
```





Charmander.hpp```cpp
.....
void attack(Pokemon* target) override;
.....
```



Charmander.hpp```cpp
.....
void Charmander::attack(Pokemon* target){
    flameThrower(target);
}
......
```





Do the same for the rest of the different types of Pokemon.



Once you are done with all the needed changes,

try to run your code.



Your code will throw *errors* because you are still missing an important concept.

You will learn it in the next lesson.
