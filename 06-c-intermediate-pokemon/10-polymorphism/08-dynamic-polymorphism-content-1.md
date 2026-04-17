Don't you wonder,

you have reached the 5th lesson of this chapter,

But you still don't know exactly what **Polymorphism** is.



What if I tell you that,

you have already used **Polymorphism**?



Do you think I am kidding?

Eh, my friends also never believe me 😭



But trust me,

this time, I am telling the truth.



All the things that you have implemented in your code,

is known as **Dynamic Polymorphism**.



Polymorphism is of 2 types

- **Static Polymorphism** (Don't relate it with *static* keyword, that is different)
- **Dynamic Polymorphism**



You have already used Dynamic Polymorphism,

and in the upcoming lessons,

You will learn about static polymorphism.



But what exactly is Polymorphism?



Polymorphism means,

able to perform multiple functionalities,

with a single name.



Like in your code,

you are using the `attack()` function for all the types of Pokemon.



You are able to execute,

individual functionalities of different types of Pokemon,

with the *same* name, that is `attack()`.



*This is the essence of Polymorphism.*



You can also imagine a shooting game,

as another example of dynamic polymorphism.



There are hundreds of guns in a game,

now, you can not create 100 functions to use them.



Instead, it would be great to use a function like,

`useWeapon()` which you can create as an abstract function in the base class,

and override it in all the child classes.





# Dynamic Polymorphism


---



```cpp
Pokemon* ptr;

// ptr = some type of Pokemon

ptr -> attack();
```



In the above code,

I am calling the `attack()` with a pointer.

This is an example of dynamic Polymorphism.



But, what exactly is dynamic Polymorphism?



Without changing the code of the 5th line,

I am able to change the output of `attack()` function,

by just assigning some other Pokemon type,

to the `Pokemon` class pointer (ptr).



In simple words,

I can change the behaviour of `attack()` dynamically.



That's why it is known as **Dynamic Polymorphism**.



> **NOTE:** Dynamic Polymorphism is also known as run time polymorphism
