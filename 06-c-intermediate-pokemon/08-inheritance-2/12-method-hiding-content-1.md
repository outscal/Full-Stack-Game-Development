You have created `attack()` method in `pokemon` class,

and `thundershock()` method in `Pikachu` class.



What would have happened,

if instead of naming `thundershock()`,

you would have named it `attack()` in `Pikachu` as well.



Code Example of `attack()` method in `Pikachu` class:

```cpp
// Pikachu-specific move
void Pikachu::attack(Pokemon &target) {
        cout << name << " uses Thunder Shock on " << target.name << "!\n";
        target.takeDamage(thunderShockDamage); // Example of a unique move
    }
```



Code Example of `attack()` method in `Pokemon` class:

```cpp
// Attack another Pokemon
void Pokemon::attack(Pokemon &target) {
  cout << name << " attacks " << target.name << " for " << attackPower
            << " damage!\n";
  target.takeDamage(attackPower);
}
```



Which method will be called then and when?



Let's see what will happen if you do so by implementing it with a Todo,

You can use [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp) while implementing the code.



> **TODO:**
> ✅Create a `Pokemon` class and declare a method `attack()` inside it. This method will print `"Pokemon attacks with a standard attack!"`

> ✅Create a `Pikachu` class and redefine the method `attack()` inside it. This method will print` "Pikachu attacks with ThunderShock!"`

> ✅In the main function create an object of Pikachu pika and call the `attack()` method.



Example code:```cpp
#include<iostream>
using namespace std;

class Pokemon {
public:
 void attack() {
   cout << "Pokemon attacks with a standard attack!\n";
 }
};
class Pikachu : public Pokemon {
public:
    void attack() {
        cout << "Pikachu attacks with ThunderShock!\n";
    }
};

int main() {
    Pikachu pika;
    pika.attack();  // Output: "Pikachu attacks (from child class) with ThunderShock!"
    return 0;
}
```



What is the output?



Expected output:```cpp
Pikachu attacks with ThunderShock!
```



What did you uderstand?

The `attack()` method was defined in both the Pokemon and Pikachu class, 

but when we created an object of Pikachu, 

and called the `attack()` method, 

the `attack()` method in `Pikachu` class is called.



But then, 

if you want to call the `attack()` method of the `Pokemon` class from pika, 

how will you do it?



What is the use of defining `attack()` method in `Pokemon` class, 

if you cannot call it from an Object of Pikachu class?



No worries! 

Because we have the`::`operator.

Using the `:: Oprator`,

You can call the parent class method having the same name as a method defined in child class from an object of the child class. 



**Syntax:**

`name_of_object.name_of_class::method()`



If you want to call the `attack()` method of the `Pokemon` class from `pika`,

You can do it like I have shown below:



```cpp
pika.Pokemon::attack();
```





> **TODO:**
> ✅In the main function call the `attack()` method of `Pokemon` class from pika



Example code:```cpp
int main() {
    Pikachu pika;
    pika.attack();               // Calls Pikachu's attack method
    pika.Pokemon::attack();      // Calls the parent Pokemon's attack method
    return 0;
}
```

Expected output:```cpp
Pikachu attacks with ThunderShock!
Pokemon attacks with a standard attack!
```



Were you able to call both the `attack() `method from pika.

Yes!



This process of how child classes can hide parent class methods, 

by redefining them with the same name is called **Polymorphism** in OOPS. 



And there are two ways to do this

-  Method overriding 
-  Method Overloading



In the upcoming chapters you will learn what polymorphism is.

But for that you have to learn an important concept: **Pointers**.



So, in the next chapter you will study about Pointers.
