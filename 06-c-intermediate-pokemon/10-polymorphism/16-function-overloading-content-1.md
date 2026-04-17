So you have learnt many topics in polymorphism till here,

but one topic is still missing.



That is known as function overloading.

Does it sound similar to function overriding?

It is a little bit different than that.



Let me give you a quick revision of function overriding.

Function overriding happens when there is a function in the base class,

and you declare a function in the child class,

with the same name, return type and parameters.



Before discussing their differences,

let's see the code for function overloading.



```cpp
#include <iostream>
using namespace std;

class Pokemon{
public:
    void attack(){
        cout << "Pokemon is attacking" << endl;
    }
    
    void attack(int power){
        cout << "Pokemon is attacking with " << power << " power" << endl;
    }
};

int main() {
    Pokemon* p1 = new Pokemon();
    p1 -> attack();
    p1 -> attack(50);

    return 0;
}
```



Do you get it?

In the above code, `attack` function has been overloaded.



So in function overloading,

the name of the function remains the same,

but parameters are different.



Now try to run the above code

Output

```plain
Pokemon is attacking
Pokemon is attacking with 50 power
```



In function overloading,

the function that will get triggered depends on how you call the function.

In simple words, it is dependent on your given parameters.



This is an example of Static Polymorphism.

Because the compiler knows which function definition should be called,

based on the function signature,

at the compile time, unlike function overriding.



You may be wondering,

can function overloading be achieved by just changing the return type?



To check this yourself,

try to run the below given code



```cpp
#include <iostream>
using namespace std;

class Pokemon{
public:
    void attack(){
        cout << "Pokemon is attacking" << endl;
    }
    
    int attack(){
        return 10;
    }
};

int main() {
    Pokemon* p1 = new Pokemon();

    return 0;
}
```



What did you get?

An error?



Definitely, because it is not possible to overload a function by changing the return type.

Compiler won't be able to decide that which function the programmer wants to execute exactly.
