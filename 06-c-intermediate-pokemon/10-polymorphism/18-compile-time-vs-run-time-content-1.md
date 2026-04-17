So far, you have learnt a lot of topics like

- Virtual Functions
- Function overloading
- Function overriding
- Abstract Functions
- Abstract Classes



But what is compile time polymorphism?

And how is it different from run time polymorphism?



First, let me give you a quick reminder about polymorphism.

As you saw in the previous examples.

In the same code, 

you were able to perform multiple things,

using `attack` function only.



Now, before explaining the types of polymorphism,

check the two examples below.



Example 1```cpp
#include <iostream>
using namespace std;

class Pokemon{
public:
    void attack(){
        cout << "Pokemon is attacking" << endl;
    }
    
    void attack(int power){
        cout << "Pokemon is attacking with " << power << " power" << endl;
    }
};

int main() {
    Pokemon* p1 = new Pokemon();
    p1 -> attack();
    p1 -> attack(50);

    return 0;
}
```



Example 2```cpp
#include <iostream>
using namespace std;

class Pokemon{
public:
    virtual void attack(){
        cout << "Pokemon is attacking" << endl;
    }
};

class Pikachu : public Pokemon{
public:
    void attack(){
        cout << "Pikachu is attacking" << endl;
    }
};

int main() {
    Pokemon* p = new Pikachu();
    p -> attack();

    return 0;
}
```



There are 2 types of Polymorphism, as discussed previously

- Compile time polymorphism
- Run time polymorphism



In example 1,

Before the code starts getting executed,

the compiler will be able to understand which `attack` function will be called at which point.



It is obvious that in the first call, `attack` function without any parameter will be called.

And similarly for the second call.



```cpp
ptr -> attack()
```



If you want to change the functionality of **attack** in function overloading,

then you must have to change the above given line of code.

And if you make any changes to it,

you can easily predict which `attack` function will be executed.



So, during the compile time, you can predict it,

and even computers can also judge what function will be triggered.

That's why it is known as compile time polymorphism.



> **NOTE:** Compile time Polymorphism is achieved by function overloading.







But in example 2,

the compiler won't be able to figure out that whether the base class function will be triggered,

or the child class function.



Once code starts executing,

compiler will move to the base class because the pointer is of base class type,

but there it sees that it is a virtual function,

that means if it has been overridden,

the overridden function should be triggered.



This is known as run time polymorphism.

Run time Polymorphism is achieved by function overriding.



> **NOTE:** Run time polymorphism can not be implemented without the use of inheritance
