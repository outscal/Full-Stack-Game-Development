So now you know about enums,

how they work internally,

and, how they keep the code clean.



But, that's not all.

You will learn an updated version of Enum in this lesson.

It is known as Enum Class.



It looks quite similar to regular Enums.

You just need to add a *class* keyword.



```cpp
enum class name{
    // Values....
};
```



You must be thinking, why?

What is the need?



Okay, so there is a little difference in functionalities between them,

enum class offers a little more.



Look at the below given two examples.



Example 1```cpp
#include <bits/stdc++.h>
using namespace std;

enum gunColor{
    Black,
    White
};

enum dressColor{
    White,
    Black
};

int main() {
    gunColor gun = gunColor::Black;
    dressColor dress = dressColor::White;
    
    if(gun == gunColor::Black){
        cout << "Black gun" << endl;
    }
    
    if(dress == dressColor::White){
        cout << "White dress" << endl;
    }

    return 0;
}
```



Example 2```cpp
#include <bits/stdc++.h>
using namespace std;

enum class gunColor{
    Black,
    White
};

enum class dressColor{
    White,
    Black
};

int main() {
    gunColor gun = gunColor::Black;
    dressColor dress = dressColor::White;
    
    if(gun == gunColor::Black){
        cout << "Black gun" << endl;
    }
    
    if(dress == dressColor::White){
        cout << "White dress" << endl;
    }

    return 0;
}
```



Try to run both the examples and check their output.



Did you get the same output as below for example 2?

```plain
Black gun
White dress
```



And what happened in example 1?

Did you get some error as shown below?



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_12_2024__12_47_31.png)







This happened because there are two enums,

*gunColor* and *dressColor*, and both have the same name for their values,

that is *White* and *Black*.



Regular enums does not allow you to do this.



So now think, if you are making a much bigger project,

where there can be 50 enums,

is it possible to keep track of the values you have assigned to them?

There is a high probability that the values will be colliding.



Developers also faced this issue,

and they came up with the Enum class as the solution.



So, as a good practice,

I would always recommend that you use enum class instead of enum.



> **NOTE:** Enum class is also known as Strongly typed Enum
