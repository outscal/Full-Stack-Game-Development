## constructors


---



You are learning game development now. You will get Job after that and go to your office at 10 A.M



And every day before going to office you will have to make breakfast, prepare your clothes and take your car out of your garage.



It will be nice for the first few days but then you will start hoping if somebody else do these small tasks for you so that you can directly start your days without doing these chores.



What if I Program a robot for you that do all these chores for you. Now, you can directly start your day by going to office.



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_13_2024__10_05_37.jpg)



Constructor in OOP is similar to this robot.



You all must be familiar with the word constructor in a class. 



Just like the robot who does all the chores that you need to do to start your day off, Constructors are there in class that initialize the data members and methods for us whenever we create objects of the class. 



So that when we create Objects of the class, we don't repeatedly need to initialize them with some values.



Constructors are special member function which initializes an object of a class and is automatically called when an object is created. 



If you don't explicitly define any constructors in your class, the compiler automatically creates an implicit default constructor for your class. 



This default constructor initializes the class members to their default values.



You can also explicitly create constructor for your class to initialize objects with specific values. It will have the same name as the class that it belongs to, and they don't have a return type.



Let's see how we can create a default constructor for our Pokemon class

```cpp
// Constructor 
Pokemon()
  {
    name = "unknow";
    type = FIRE;
    health = 60;
  }
};

```



> **💡Pro Tip: ***Your Constructor should be a ****public****** ****method, since it is always going to be accessed from outside the class.*



Now try running the code below:

Code to see how default constructor work```cpp
#include<iostream>
#include<string>
using namespace std;

enum class PokemonType { 
    FIRE, 
    GRASS, 
    WATER, 
    ELECTRIC 
};

class Pokemon { 
public: 
    // Attributes 
    string name; 
    PokemonType type; 
    int health; 

        // Constructor 
    Pokemon() { 
        name = "unknow"; 
        type = PokemonType::FIRE; 
        health = 60; 
    } 
};

int main(){
  Pokemon pokemon1;

  cout<<pokemon1.name<<endl;

// You can not print Enum class value directly
  cout<< (int)(pokemon1.type) <<endl;

  cout<<pokemon1.health<<endl;
}
```



What is the output? 

The default values that we have given to the constructor 

![image]()

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_28_2024__11_23_12.jpg)





## DESTRUCTORS


---



It makes sense that if a Constructor exists to initialize variables, then so does a **Destructor** for the opposite. 



When we create Objects, memory is allocated to them. 

There is no default garbage collector present in C++ that deallocate this memory when an object's work is completed.



And if we don't free up this memory a time will come when we won't have memory left for new objects.

So, to free up the memory that is allocated to objects once their work is done, we use Destructor



Destructor to free up any resources and memory or do any cleanup for the object when an object is destroyed. 



It looks very similar to a Constructor but with a Tilda `**(~)**` symbol before the method name.



Destructor is automatically called by the compiler when the object gets destroyed or deleted from the memory.



```cpp
~Pokemon() {
        cout << "Pokemon is getting destroyed"<< endl;
        // Perform cleanup operations here, e.g., save player data to a file or log a message.
    }
```



Later when we are making the game, we will look into the use cases for destructors in more detail as well.
