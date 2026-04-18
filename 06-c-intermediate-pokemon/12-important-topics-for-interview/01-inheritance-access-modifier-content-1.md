Till now in your code, 

while inheriting the `Pokemon` class,

you have been using a public keyword before the `Pokemon` class.

`**class Pikachu : public Pokemon**`



Why are you using this public keyword before the `Pokemon` class?

What will happen if you remove this public keyword?



Let's see with a simple Todo:

You can run your code in [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp) 



> **TODO:**
> ✅Create a class `Pokemon` and a method `attack()` inside it.

> ✅`attack()` method will print `"Pokemon attack!"`

> ✅Create another class `Pikachu` that is inheriting the `Pokemon` class.

> ✅Inside the `Pikachu` class create a method `thunderbolt()` that will print `"Pikachu uses Thunderbolt!"`

> ✅Don't use the public keyword before the `Pokemon` class while inheriting.

> ✅Inside the main function create an object of Pikachu `Pika` and call the methods `thunderbolt()` and `attack()`

> ✅`Pika` will call the methods `thunderbolt()` and `attack()`



Example code:```cpp
#include<iostream>
using namespace std;

class Pokemon { 
	  public: 
		void attack() { 
		cout << "Pokemon attack!" << endl; 
		} 
};

class Pikachu : Pokemon { 
	  public: 
		void thunderbolt() { 
		cout << "Pikachu uses Thunderbolt!" << endl; 
		}
};

int main() {
    Pikachu pika;
    pika.thunderbolt(); 
    pika.attack(); 
    return 0;
}

```



What is the output?

`thunderbolt()`  method is running perfectly, 

and you got an error while executing `attack()`, right?



But `attack()` is a public method of the `Pokemon` class.

What did you get this error?



Before answering this question,

I want you to answer the following question first:



> **Why should a public member of the Parent class remain as public in the Child class as well?**





If you really think about it,

Why can’t the child class have different accessibility for the inherited members?

If you could do that, then you would have more control over your code.



Luckily, you can change the accessibility of base class members after they are inherited by the child class!



**"Access modifiers can be used during inheritance to set the accessibility of inherited members in the child class."**



Does it sound confusing? 



Don't worry, we will go through it in detail.

What it essentially means is that you can use access modifiers in the following way during inheritance:



`**class Pikachu : private Pokemon**`

`**class Pikachu : protected Pokemon**`

`**class Pikachu : public Pokemon**`



Let's understand what it means to inherit using access modifiers.



In the above example Todo,

you are using inheritance in the following way: `**class Pikachu : Pokemon.**`

This uses the **default** inheritance access specifier, which is → `**private**`.



You have seen three access modifiers till now:

1. **Public**
2. **Private**
3. **Protected**



We can use either of these **during** **inheritance** to change how base class members are inherited in the child class.

Take a look at the below diagram:





![Image](/Full-Stack-Game-Development/images/9c2860ea363cacab.png)





Inheritance Access Modifiers





If you observe the above diagram, you will notice some interesting stuff, like:

- the health variable is public in base class, but in child class it changes to:
- - protected → if the inheritance access modifier is protected.
  - private → if the inheritance access modifier is private.
- the damage variable is protected in base class, but in child class it changes to:
- - private → if the inheritance access modifier is private.
- If the inheritance access modifier is public, access modifiers for all members remains unchanged.



I guess we can draw the following conclusion from this data:



> **The inheritance access modifiers can restrict the access of all inherited members from parent class.**



Let's briefly see the syntax for each and discuss them as well.



## **Public Inheritance:**


---

Public Inheritance indicates that all the base class members will be inherited with the same access they have in the base class.



For example, if a base class member is public in the base class, it will remain public in the child class.

If a member is protected, it will remain protected in the child class.

If a member is private, then it will remain private.



We said that `**class Pikachu: Pokemon**` used the default accessor, which is private,

and so, you were not able to access the public method `attack()` in the above example.



You have used `**class Pikachu : public Pokemon**`** **in your game code,

which is why, you didn't get any error, 

while accessing the methods and members of the `Pokemon` class.



## **Protected Inheritance:**


---

Protected Inheritance indicates that the highest accessibility for inherited members will be protected.



This means that a public member of the base class will become protected in the child class.

Protected and Private members of the base class will have the same access levels.


**Private Inheritance:**


---

Private Inheritance indicates that the highest accessibility for inherited members will be private.



This means that all members of the base class will be inherited as private members in the child class.

This is also the default access modifier which is used if we do not specify one during inheritance.



This is exactly why you were getting that error in the example before:

The error said that "`**attack()**` is a private method of the base class."



The error is correct.

the `**attck()**` function of the base class `Pokemon` class was being privately inherited in the `Pikachu` class.

This is exactly what the error indicated.



> ✅**TODO:** Fix the error that you got in the example before by setting the inheritance access modifier to Public.
