Type casting in C++ is nothing but converting one data type to another.



> The operator used for this purpose is known as the **cast operator**.

> It is a **unary operator** which forces one data type to be converted into another data type.

> 



Let's understand this with the help of an example,



Suppose I give you an integer x = 10 and a char y = 'a'

What do you think will happen,

if I add x and y?



```cpp
#include<iostream>
using namespace std;

int main() {
	int x = 10;
	char y = 'a'; 
	x = x + y;

	cout<<x<<endl;
return 0;

}
```



Go and run the code in your compiler.

What is the value of x?



The ASCII value of 'a' is 97 which is an integer so it will add 97 with 10 and assign the value 107 to x.

So, the output will be 108.



But how did that happen?

How did the compiler add a char variable with an integer?



What happened in the above example is called implicit Typecasting.

The compiler automatically converted the char to integer,

and adds it with the other integer and stored the result as an integer.



But why did the compiler store the result as an integer and not as a character?

Because we have stored the output in x.



If you had stored the value of x + y in y than the output would have been 'k' instead of 107,

Because the ASCII value of 'k' is 107,

which is a character.



Try to run the code given below in your compiler and see yourself.



```cpp
#include<iostream>
using namespace std;

int main() {
	int x = 10;
	char y = 'a'; 
	y = x + y;

	cout<<y<<endl;
return 0;

}
```



There are times when you need to convert data types explicitly as well,

when the compiler doesn't.



Suppose you are given an integer num = 8,

and you are asked to assign this value to a float variable b.



```cpp
int num = 8;
float b = num;
```



If you directly assign the value of num to it, like above,

the compiler will throw you an error.



So, you need to change the data type of num,

while assigning its value to the float variable.



```cpp
int num = 8; 
float b = (float)num; 
```



This is called explicit Type casting in C++ and there are multiple ways to do that.

Let's see what they are.



## C-Style Cast


---

**Syntax**:

`(target_type) expression`



- `target_type` is the data type to which you want to convert your data.
- expression is the variable or pointer or object which you want to **cast**.



In the above example that I have given to you,

you can use this Typecast,

to assigning the value of num to the float variable



Example code:

```cpp
int num = 8; 
float b = (float)num; // Convert int to double 
cout << b << endl; // Output: 8.0
```



## static_cast


---

**Syntax**:

`static_cast<target_type>(expression)`



It checks if the conversion is valid at compile time.

You can use this for most basic type conversions (for e.g., between numeric types)



Example code:

```cpp
int num = 8; 
double b = static_cast<double>(num); // Convert int to double 
cout << b << endl; // Output: 8.0
```



## dynamic_cast


---

**Syntax**:

`dynamic_cast<target_type>(expression)`



Dynamic casting in C++ is like checking if a pointer or reference to a base class actually points to a derived class.



It’s a way to **safely convert** a base class pointer (or reference) to a derived class pointer, 

but only if the object really belongs to that derived class.



It checks at runtime if the cast is possible,

and returns a `nullptr`, if the cast is not valid.



Let's understand this with an example:



You have a **general Animal class** and a **specific Dog class** that inherits from Animal. 

You have a pointer to Animal, 

but you want to know if it’s actually pointing to a Dog. 

You can use dynamic casting to check:



Example code:

```cpp
class Animal { 
    virtual void sound() {} // Virtual function makes the class polymorphic
};

class Dog : public Animal { };

Animal* animal = new Dog(); // Pointer to an Animal, but it's actually a Dog
Dog* dog = dynamic_cast<Dog*>(animal); // Safe cast

if (dog) {
    // The cast was successful, 'animal' is actually a Dog
    cout << "This is a dog!" << endl;
} else {
    // The cast failed, 'animal' was not a Dog
    cout << "This is not a dog." << endl;
}

```



In the above code you have typecasted the animal pointer to a pointer that is pointing to a dog class.



In the if statement you are checking is the dog pointer is actually pointing to a dog,

after you typecasted the animal pointer to a dog pointer.



If the value of dog is null that means the animal pointer is not typecasted to dog,

and it will print `"This is not a dog."`
