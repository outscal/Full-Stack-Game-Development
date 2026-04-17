What will happen if you run the below code in your compiler?



```cpp
#include<iostream>
using namespace std;

int main(){
int a = 2;
int b = 5;
cout<<a * b<<endl;
return 0;
}
```



It will give the output 10

Right!!



Now run the code below:



```cpp
#include<iostream>
using namespace std;

class Object{
public:
int data;
Object(int value){
data = value;
}
};

int main(){
Object obj1(2);
Object obj2(5);
Object obj3;
obj3 = obj1 * obj2;
cout<<obj3<<endl;
return 0;
}
```



What is the output now?

Compiler throws an error.

But why?



Because the compiler knows how to add numbers using ‘*’

but the compiler doesn’t know how to add objects using ‘*’



We have to tell the compiler how to add objects so that

obj3 = obj1 * obj2 becomes a valid statement.



You can redefine the ‘*’ operator to multiply objects as well.

This is known as Operator overloading.



The syntax for operator overloading is:

 

> return type classname :: Operator operator being overloaded (parameter list)

> {

> //body

> }

> 





But how do you tell the compiler to multiply objects using the '*' operator?

Let's see how,



> **TODO: Class multiply**

> ✅Create a class `multiply` and declare an integer `num``
> ✅Create a method `setData()` to set the value of num. Its return type will be void and it will take an integer as argument

> ✅Create another method `dislay()` to display the value of num.

> ✅Declaring an overloaded `*` operator function for the `multiply` class: multiply operator * (multiply c)





Example code: Class multiply```cpp
class multiply
{
    int num;

public:
    void setData(int a) {
        num = a;
    }

    void display() {
        cout << num << endl;
    }

    multiply operator * (multiply c);
};
```



> **TODO: Operator overloading**

> ✅Define the overloaded operator `*` for the multiply class outside the `multiply` class. It will take an object `c` of class multiply as argument

> ✅Create an object `temp` of multiply class inside it

> ✅Multiply `num` with the `num` of the object `c` that you took as argument and store it in the `num` of `temp`. Return `num`





Example code: operator overloading```cpp
multiply multiply::operator*(multiply c)
{
    multiply temp;
    temp.num = num * c.num;
    return temp;
}
```



> **TODO: main function**

> ✅In the main function create 3 objects of multiply and multiply two objects and store the value in the third object

> ✅Call the method display for the third object where you have stored the value





Example code: main function```cpp
int main() {
    multiply obj1, obj2, obj3;
    obj1.setData(2);
    obj2.setData(5);
    obj3 = obj1 * obj2; // Using overloaded '*' operator
    obj3.display(); // Display result
    return 0;
}

```



Example code: Entire code```cpp
#include<iostream>
using namespace std;

class multiply
{
    int num;

public:
    void setData(int a) {
        num = a;
    }

    void display() {
        cout << num << endl;
    }

    multiply operator * (multiply c);
};

// Operator overloading for '*'
multiply multiply::operator*(multiply c)
{
    multiply temp;
    temp.num = num * c.num;
    return temp;
}

int main() {
    multiply obj1, obj2, obj3;
    obj1.setData(2);
    obj2.setData(5);
    obj3 = obj1 * obj2; // Using overloaded '*' operator
    obj3.display(); // Display result
    return 0;
}
```



What is the output now?



output10



Now the Compiler will know how to add numbers as well as Objects using ‘+’ Operator.


## Exceptions for operator overloading


---

We cannot overload every operator there are some exceptions:

1. Scope resolution operator ::
2. Size operator sizeof()
3. Conditional operator ?:
4. Class member access operator with . operator and .* operator
