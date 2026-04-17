Constructors are special member function, 

which initializes an object of a class,

and is called automatically when an object of the class is created. 



We use a Destructor to free up memory, 

or do any cleanup,

when an object is destroyed.



Remember this definition of constructors and destructors,

from the chapter Introduction to Object Oriented programming in this module?



Because this lesson is all about the sequence in which constructors and destructors are called.



Now, you know that. 

when an object of a class is created, 

its constructor is automatically called first by the compiler.



But what about the classes that inherits other class?

Whose constructor will be called first?

Base class or subclass?



Let's try to answer this with a simple Todo:

Use this link to run your code: [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp)



> **TODO:**

> ✅Create a `Pokemon` class and a default constructor inside it.
> ✅In the default constructor `cout` the following statement `"Pokemon constructor called."`

> ✅Create a destructor in the `Pokemon` class.

> ✅In the destructor `cout` the following statement `"Pokemon destructor called."`

> ✅Create another class `Pikachu` which is inheriting the `Pokemon` class.

> ✅In the default constructor of `Pikachu` class `cout` the following statement `"Pikachu constructor called."`

> ✅Create a destructor in `Pikachu` class and `cout` the following statement `"Pikachu destructor called."` inside it



Example code: `Pokemon` and `Pikachu````cpp
#include <iostream>
using namespace std;

class Pokemon{
public:
  Pokemon() {
        cout << "Pokemon constructor called.\n";
    }
    ~Pokemon() {
        cout << "Pokemon destructor called.\n";
    }  
};

class Pikachu : public Pokemon{
 public:
  Pikachu() {
        cout << "Pikachu constructor called.\n";
    }
    ~Pikachu() {
        cout << "Pikachu destructor called.\n";
    }  
};

int main() {
    return 0;
}
```



Let's instantiate the `Pokemon` class first.



> **TODO:**
> ✅ In the main function create an object of `Pokemon` class



Example code: main function```cpp
int main() {
    Pokemon p;
    return 0;
}
```



Try to run the code.

What is the output?



Output:```cpp
Pokemon constructor called.
Pokemon destructor called.
```



Is the output same as you expected?

YES!



Now instantiate the `Pikachu` class.



> **TODO:**
> ✅ In the main function create an object of `Pikachu` class



Example code: main function```cpp
int main() {
    Pikachu p;
    return 0;
}
```



Run your code again.

What is the output?



Output:```cpp
Pokemon constructor called.
Pikachu constructor called.
Pikachu destructor called.
Pokemon destructor called.
```



Is that what you expected?

What reason do you think for the above output result is?



When you instantiated the `Pokemon` class,

its constructor is called first followed by its destructor.



But when you instantiated the `Pikachu` class,

first the constructor of `Pokemon` class is called,

and then the constructor of `Pikachu` class.



Then later, while cleaning up, 

the destructor of `Pikachu` class is called followed by the destructor of `Pokemon` class.



Why is the constructor of the parent class called first, 

and then the constructor of child class. 

But the destructor of the child class is called first followed by base class destructor



let's see!!



## sequence of constructor calls


---

You know that `Pikachu` class is inheriting the data members and methods of `Pokemon` class, 

i.e, child class may rely on the base class properties.

e.g., `Pikachu` uses properties like health from the `Pokemon` class.



When the `Pikachu` class gets instantiated, 

it needs the `Pokemon` class to be initialized first,

so that it can use the properties declared in the `Pokemon` class.



## sequence of destructor calls


---

But while cleaning up, 

the child class might depend on the parent class.

The parent class may allocate resources or manage data that the child class inherits. 

Like the name of `Pikachu`, its `health` and attack power. 



So, if the Parent class is deleted before child class, 

then the attributes of `Pokemon` class that `Pikachu` is inheriting will also be deleted.

But `Pikachu` is still using these attributes which are already deleted,

leading to undefined behavior and error. 




---





Have you ever felt that the data members of `Pokemon` class is not secure?



That the attributes of parent class are not even secure from the child class that is inheriting it?



If it is inheriting the attributes of parent class, then it can change the value as well!!



Don't worry!! You will study about how to protect the data of a class in the next lesson.
