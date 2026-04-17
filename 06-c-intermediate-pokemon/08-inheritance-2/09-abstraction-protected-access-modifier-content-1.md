You have used the `public` and `private` keywords, 

while creating classes and are familiar with their use.



How do you access the Private members of your class?

By using getters/setters right?



Let's have a quick revision of what they are:

- **Public:** Accessible from anywhere.
- **Private:** Only accessible within the class.
- **Public Getter/Setter:** Allows controlled access to private variables.



In your `Pokemon` class all the attributes that you created are public.

It can be a big Problem later. 

Let's see how?



> **TODO:**
> ✅Go to [https://outscal.com/online-compilers/cpp](https://outscal.com/online-compilers/cpp) and Create a `Pokemon` class.

> ✅Inside the `Pokemon` class create two public variables: int `health` and int `attackPower`.



Code Example:```cpp
class Pokemon {
public:
    int health = 50;  // Public access, can be accessed anywhere
    int attackPower;
};
```



Since both the data are public `health` and `attackPower`, 

they can be accessed and modified by any other class from anywhere, 

including its own child class `Pikachu`.



This might not be the best practice as it allows uncontrolled access to crucial variables.



Let's understand this with an example



If the health variable is public in the `Pokemon` class, 

any other class or function could change the value, 

including inappropriate values.



Suppose I am working with you in your game, 

and I changed the health value of `Pokemon` class using `Pikachu` class, 

and set it to 1000 which is an Invalid health value (Not an intentional mistake)



```cpp
class Pikachu : public Pokemon { 
  public: 
  Pikachu() { // Constructor to initialize health 
  health = 1000; //invalid health data
   } 
 };
 
int main() {
    Pikachu pika;
    cout<<pika.health<<endl;
    return 0;
}
```



But you have set the health variable of all the `Pokemon`, in your game to be 50.



The above lines of code will change the default value of health variable of `Pokemon` class to 1000, 

and you will not understand where is the bug? 

(Imagine this error happening to some data that is very crucial to your company. They can lose data anytime)



Allowing such uncontrolled access can break the game logic and is not secure.



So, to solve this Problem we use Private access modifier.

Let's see how making the health variable private will help us in avoiding such problems



> **TODO:**
> ✅In the above Pokemon class make the health variable private.

> ✅create two public method `getHealth()` and `setHealth(int h)` to get and the set the value of health in `Pokemon` class.



Example code:```cpp
class Pokemon {
private:
    int health;  // Private access
public:
    void setHealth(int h) { health = h; }
    int getHealth() { return health; }
};


```



When you made the health variable private, 

you prevented it from being modified directly, thus improving security.



If some other class wants to use the `health` variable in their methods,

they can simply get the value of health using the `getHealth()`,

and make changes to the health variable according to their needs,

and set the value to the `health` variable using `setHealth()` inside them,

without affecting the actual `health` variable of the `Pokemon` class.



> Here, `getHealth()` and `setHealth(int h)` is the getter and setter of the `Pokemon` class.

> getter and setter are used to get controlled access to the private members of a class.

 



When you declare any variable or method of a class **Private, **

no class, not even its subclass can have direct access to that variable.



Try to access the health variable now through your Pikachu class. 



```cpp
class Pikachu : public Pokemon {
public:
    Pikachu() {  // Constructor to initialize health
        health = 1000;  
    }
};

int main() {
    Pikachu pika;  // Creating a Pikachu object
    cout << pika.health << endl;  // Accessing health

    return 0;
}
```



Were you able to do it? 

NO!



There are times, 

when you need the child class to have access to the data members and methods of the base class,

but not any other class.



But you won't be able to do it, 

with the help of Private access modifier, 

nor by using public access modifier.



For this purpose, we have another access modifier called **protected.**

Protected members are accessible inside the base class and all the child classes of the base class,

but are still hidden from outside classes.



> **TODO:**
> ✅Make the health variable and `AttackPower` of `Pokemon` class Protected



Example code:```cpp
class Pokemon {
protected:
    int health;  // Accessible to child classes like Pikachu
    int attackPower;
};
```



Now, Run the code below after making the changes in `Pokemon` classes.



```cpp
class Pikachu : public Pokemon {
public:
    Pikachu() {  // Constructor to initialize health
        health = 1000;  
    }
};

int main() {
    Pikachu pika; 
    cout << pika.getHealth() << endl;  // Accessing health through the getter function
    return 0;
}
```



In the above code,

`Pikachu` class is inheriting the `Pokemon` class, 

so, it can access the `health` variable of `Pokemon` class as it is a `protected` variable, 

but pika is out of scope of the `Pokemon` class.



Because pika is declared inside the main function.

So, to access the health variable from main function pika had to call the `getHealth()` method.



> Protected variables allow secure access within the inheritance chain, promoting abstraction by hiding unnecessary details from the outside world.



## what is abstraction?


---



Would you like it if a random person suddenly comes, 

and change a data value in your `Pokemon` class?



Not only change, 

but you have lost the data, 

and now you don't remember what its value was initially, 

nor you know whom to blame.



Because you are the one who had given access to all the classes by making your data member in `Pokemon` class public.



You do not want any external classes to modify a Pokemon’s health directly, right?



Instead, 

you want them to interact with the Pokémon through methods like `takeDamage()` and `heal()`, 

while keeping the internal data private or protected.



Let's see the code below:

```cpp
class Pokemon {
protected:
    int health;
public:
    void takeDamage(int damage) {
        health -= damage;
    }
    void heal(int amount) {
        health += amount;
    }
};
```



Here using the methods `takeDamge()` and `heal()` , 

other classes can access the health variable of `Pokemon` class, 

and use it in their methods, 

without directly or indirectly making any unintended changes to it.



Now, other classes don't need to know how the health is reducing or increasing,

nor they can directly make any change to the health variable.

If they want to reduce the health, 

they will simply call the `takeDamage()` method. 



This is known as **abstraction.**

It will be even easier to manage your codebase.



> Abstraction in programming allows you to hide complex implementation details while exposing only what’s necessary for other classes to interact with.

> 



Now that you know the importance of Private, public and protected access modifier,

implement them in your code.



> **TODO:**
> ✅In pokemon.hpp make the variables `name`, `type`, `health`, `maxHealth` and `attackpower` protected.



Example code:```cpp
#pragma once
#include <string>

namespace N_Pokemon {
    
    using namespace std;
    
    enum class PokemonType;
    
    class Pokemon {
    protected:
        string name;
        PokemonType type;
        int health; 
        int maxHealth; 
        int attackPower;
        
    public:
        Pokemon(); 
        Pokemon(string p_name, PokemonType p_type, int p_health, int p_attackPower);
        Pokemon(const Pokemon &other);
    
        bool isFainted() const;
        void heal();
        void attack(Pokemon &target);
        void takeDamage(int damage);
    };
}
```



> **TODO:**
> ✅In the header files of Pikachu, Zubat, Pidgey and Caterpie make all the unique attack methods private.



Pikachu.hpp```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
  
    class Pikachu : public Pokemon {
    private:
    void thunderShock(Pokemon &target);
    
    public:
      Pikachu();
    };
    
  }
}
```



Zubat.hpp```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
  
    class Zubat : public Pokemon {
    private:
    void supersonic(Pokemon &target);
    
    public:
      Zubat();
    };
    
  }
}
```



Pidgey.hpp```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
  
    class Pidgey : public Pokemon {
    private:
    void wingAttack(Pokemon &target);
    
    public:
    Pidgey();
      
    };
    
  }
}
```



Caterpie.hpp```cpp
#pragma once
#include "../Pokemon.hpp"

namespace N_Pokemon {
  namespace N_Pokemons {
    
    class Caterpie : public Pokemon {
    private:
     void bugBite(Pokemon &target);
     
    public:
      Caterpie();
     
    };

  }
}
```
