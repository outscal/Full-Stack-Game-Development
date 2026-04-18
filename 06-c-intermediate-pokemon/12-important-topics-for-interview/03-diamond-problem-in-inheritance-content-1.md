Do you remember the example of Volcanion, 

that I gave you in the lesson on types of inheritance?



It is a dual type of **Fire/Water** Pokémon, 

that can use both Fire-type and Water-type moves.

how will you create this Pokémon?



You can create a `Volcanion` class, 

that will inherit from both `Charmander` and `Squirtle` class, 

and use their `flameburst` and `watersplash` moves, 

you can also add some unique moves of `Volcanion` as well.



While You might be thinking,

multiple inheritance provides greater flexibility in modelling real-world relationships, 

it also introduces complexities, 

one of which is the **Diamond Problem**.



Let’s see how it creates the Diamond Problem in the case of `Volcanion`.



`Volcanion` is inheriting from both  `Charmander` and `Squirtle`, 

and both  `Charmander` and `Squirtle` are inheriting from the base class `Pokemon`.



Below is a flowchart showing the relationship between these classes. 

You can see that it forms a diamond shape.

It is because of this kind of relationship,

that leads to an ambiguity error and hence the name 'Diamond Problem.

![Screenshot 2024-09-09 082245.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/8c9f7b97-3438-434a-b8ca-0a53eb7262ea/87f3b36b-96eb-4ef2-a00c-f1f0327e3d68/Screenshot_2024-09-09_082245.png)



![Image](//outscal.github.io/Full-Stack-Game-Development/images/fefaa56a9636e28b.png)



Let's try to understand this ambiguity problem in depth with a Todo:

You can run your code in https://outscal.com/online-compilers/cpp 



> **TODO:**
> ✅Create a class `Pokemon` and a method `attack()` inside it.

> ✅This method will return void and will print a statement `"I attack"`

> ✅Create another two class `Charmander` and `Squirtle` which will inherit the `Pokemon` class.

> ✅Create another class `Volcanion` which will inherit both `Bulbasaur` and `Squirtle`

> ✅In the main function create an object of `Volcanion` and call the function `attack()`.





Example code:```cpp
#include<iostream>
using namespace std;

class Pokemon{
  public:
  
  void attack(){
      cout<<"I attack"<<endl;
  }
  
};

class Charmander: public Pokemon{ };

class Squirtle: public Pokemon{ };

class Volcanion:public Charmander,public Squirtle{ };


int main() {

    Volcanion vol;
    vol.attack();
    return 0;
}
```



Run your code.



Did you get an ambiguity error?



Okay, forget about the error for some time and answer the question first:

What do you understand by the word ambiguity?



When you google the word ambiguity it shows

"The quality of being open to more than one interpretation"



So, the ambiguity error means,

an error that is arising due to existence of multiple ways or interpretation. 



In the above example,

the derived class `Volcanion` has multiple paths to access the method `attack(),`

inherited from the common ancestor `Pokemon`.



When the `Volcanion` class is calling the method `attack()`,

the compiler gets confused as which path it should take,

because both the class `Bulbasaur` and the class `Squirtle`are inheriting the `Pokemon `class,

and multiple instances of `Pokemon` class is created.



But how will you resolve this error?



*Using ****virtual keyword***



> **TODO:**
> ✅Use virtual keyword in front of public while Charmander and Bulbasaur are inheriting the Pokemon class





Example code:```cpp
#include<iostream>
using namespace std;

class Pokemon{
  public:
  
  void attack(){
      cout<<"I attack"<<endl;
  }
  
};

class Charmander:virtual public Pokemon{ };

class Bulbasaur:virtual public Pokemon{ };

class Volcanion:public Charmander,public Bulbasaur{ };

int main() {

    Volcanion vol;
    vol.attack();
    return 0;

}
```







YAY, the error got resolved right away when you used virtual keyword.



But why?

Because when you declare the inheritance as virtual,

it ensures that only one instance of the common base class `Pokemon` is created.

So, now the compiler doesn't get confused,

hence resolving the problem of ambiguity.
