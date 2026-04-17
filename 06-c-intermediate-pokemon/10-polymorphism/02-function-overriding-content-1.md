> **NOTE:** You can write and run your code [here](https://outscal.com/online-compilers/cpp)



I don't want to start it with some boring formal definitions.

So, let's jump into the code example directly.





Example 1```cpp
#include <iostream>
using namespace std;

class car{
public:
    void engineDetails(){
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

    return 0;
}
```



Look at the above example.



There is a class `car`, 

which is a generalized class.

And there is an individual class for `Honda City` car,

which inherits `car` class.



Did you notice both the classes have,

`engineDetails()` function with the same name, the same return type and the same parameter?

In other words, I can say that `engineDetails()` function is **overridden** in `hondaCity` class.



Are you curious to know what's going on here?



Just a minute. First, look inside the `main` function.

`car` class pointer is initializing `hondaCity` class object.



Is it allowed?

Well, check it yourself, and try running the above code.



What happened? Did the code give any errors? I guess not.

That means, 

yes, it is allowed to do so.



But why am I even doing this?





Suppose there are 100 types of individual cars like Honda City, Ferrari, etc.

So, will it make sense to create 100 variables in the code to control them?



When you can control them with just a single variable type.

This will be a much cleaner and easier way to manage your code.



That's why you should handle child class objects with base class pointers,

because base class is common for all the child classes.





Now, let's try to execute the child class function with the base class pointer.



Example 2```cpp
#include <iostream>
using namespace std;

class car{
public:
    void engineDetails(){
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



Output

```plain
All the cars have engine!
```



What? That means base class function has been triggered,

and not child class.

Because I have used a base class pointer.



So, how would I be able to handle the child class using the base class pointer,

if I am not able to access functions of the base class?





# Virtual Functions


---

Add a **virtual** keyword in the base class function.

Then see what will happen.



Example 3```cpp
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



Output

```plain
Honda City engine is of 1200cc
```



Nice!!!

You got what you wanted.



Now, let's understand the **virtual** keyword.

If you make a function virtual, 

does that mean that the function will be hidden in the code?



Let's check it in the below example.



Example 4```cpp
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

class marutiSwift : public car{
public:
    
};

int main() {
    car* ptr1 = new hondaCity();
    car* ptr2 = new marutiSwift();
    
    ptr1 -> engineDetails();
    ptr2 -> engineDetails();

    return 0;
}
```



Output

```cpp
Honda City engine is of 1200cc
All the cars have engine!
```



Okay!

Did you get it?



In Honda City, I have overridden `engineDetails()` but not in Maruti Swift.



That means If a virtual function is overridden in the child class,

then the child function will be executed.



But if it is not overridden,

then the virtual function will behave as a regular function,

and the virtual (base class) function will be executed.
