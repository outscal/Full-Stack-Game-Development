The `Pokemon` class that you have created,

had some common features,

that are shared by different `Pokemon`.  

Like `health` or `attackPower`.



What if I want to keep this common features same,

for all the subclasses and objects of `Pokemon` class?

Like setting the health variable 100 for all.

And any change in the variable,

is reflected in all the subclasses and objects of the `Pokemon` class.



We use **static keyword** for this purpose.



When you declare a variable of a class static,

then it belongs to the class itself,

and not to any instance of the class.



You can **access and modify this static variable **anywhere,

through **the class**.



> **NOTE: **Since static variable belong to a class and not to its objects or subclasses, **they cannot be initialized using constructor.**





Static variable is shared by all the objects and subclasses of a class,

and is **defined** **only once**,

regardless of how many objects or subclasses of that class created.





> While accessing the static variable from the base class or derived class you have to use the `::` operator

> and while accessing the static variable from the objects of the base class you will have to use the `.` operator





Let's understand this through an example:

Run the code below in [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp)



Example code:```cpp
#include <iostream>
using namespace std;

class Pokemon {
public:
    static int health;
};

int Pokemon::health = 100; // Initialization of the static variable

class Pikachu : public Pokemon {
};

int main() {
    Pokemon Charmander;
    Pikachu Pika;
    // Accessing static variable via base class
    cout << "Pokemon health:" << Pokemon::health <<endl;

    // Accessing static variable via derived class
    cout << "Pikachu health: " << Pikachu::health << endl;
    
    cout << "Charmander health: " << Charmander.health << endl;
    cout << "Pika health: " << Pika.health << endl;

    // Modifying static variable via base class
    Pika.health = 20;
    
    cout << "Pokemon health after modification:" << Pokemon::health <<endl;
    cout << "Pikachu health after modification: " << Pikachu::health << endl;
    cout << "Charmander health after modification: " << Charmander.health << endl;
    cout << "Pika health after modification: " << Pika.health << endl;

    return 0;
}
    
```



What is the output?



output```cpp
Pokemon health:100
Pikachu health: 100
Charmander health: 100
Pika health: 100

Pokemon health after modification:20
Pikachu health after modification: 20
Charmander health after modification: 20
Pika health after modification: 20
```



In the above code,

`health` is a static variable of the `Pokemon` class.

which is initialized to the value 100,



Inside the main function,

instances of `Pokemon` class `Charmander` and `Pikachu` class `Pika` are created.



You can see that even though,

the `health` variable is defined once,

the value of the `health` variable is the same for all, 

and when we modified its value from `Pika`, 

it was updated for everyone.



## static objects


---

*You can use**** static keyword ****while creating objects of class as well.*



Just like static variables, 

when you declare objects as** static**, 

they have a scope that lasts for the lifetime of the program.

Let's understand this as well with the help of an example:

Run the code below in [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp)



Example code:```cpp
#include <iostream>
using namespace std;

class Pokemon { 
     public:
     int health;  // Declaring health as a member variable
     
     Pokemon() : health(100)  // Initializing health
     {
        cout << "Inside the constructor" << endl;
     }

     ~Pokemon()
     {
        cout << "Inside the destructor" << endl;
     }
};

int main()
{
    if(true){
        Pokemon charmander;  // Local object, will be destroyed when out of scope
        static Pokemon Pika;  // Static object, will live until the end of the program
    }

    cout << "End of the program" << endl;

    return 0;
}
```



What is the output?



output```cpp
Inside the constructor
Inside the constructor
Inside the destructor
End of the program
Inside the destructor
```



The constructor for the non-static `Pokemon` object `Charmander`,

is invoked, when it is created inside the if block, 

and as soon as the control of if block gets over, 

the destructor is invoked.



This is because, 

the scope of the object `Charmander` is inside the if block only,

where it is declared.



But for the static `Pokemon` object `Pika`,

the constructor is invoked when it is created inside the if block, 

but the destructor is called when the program ends.



## static methods in class


---

Just like static data members of a class, 

you can also have static methods.



It is similar to static variables of a class, 

but **Static methods are allowed to access only the static data members or other static member functions**, 

they cannot access the non-static data members or member functions of the class. 



You can access and modify a static member function using  `.` operator and object. 

And you can also use `::` operator and class name for invoking the static method.  



Let's make the `attack()` method of the `Pokemon` class static

Run the code below in [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp)



Example code```cpp
#include <iostream>
using namespace std;

class Pokemon {
public:
    static void attack() { 
        cout << "I attack"; 
    }
};

int main() {
    Pokemon::attack(); // Make sure no invisible characters are here
}
```



See the output below! 

Is it matching to yours?



Output```cpp
I attack
```
