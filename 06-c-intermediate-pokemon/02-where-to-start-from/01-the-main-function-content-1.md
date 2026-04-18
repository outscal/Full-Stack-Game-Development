> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your main branch called → ***Feature_1_Pokemon_Selection***

> Let’s start working on the new feature now!



A project can contain hundreds of files. Don't get scared. We won't be having that much. Chill.

But have you ever wondered how the computer decides where to start your code from if a project has so many files?



Suppose there are two functions, movePlayer() and createPlayer().



`createPlayer()` will create an object to represent the player,

and `movePlayer()` will be responsible for the player's movement.



Now just imagine,

what will happen if `movePlayer()` gets executed before `createPlayer()`.

If there is no player exists, then who will do the movement?



![ ](//outscal.github.io/Full-Stack-Game-Development/images/fed446feab76e2a7.png)





That's why executing all the functions sequentially is important to avoid errors.





# Initialization of the code


---

In a project, there are lots of functions that you implement.

But what will be the first function that initializes your whole game?



You just saw above how important it is to execute the code sequentially.

I will be a big mess if the computer executes the code randomly.



C++ developers also thought of this.

So, they have introduced a function to tackle this problem.



C++ language has a default function called `main()`which gets triggered as soon as the code starts. 

This is the ***opening door*** of your code. 

You will call other functions through this `main()` , so now you don't have to worry about ordering of execution.





## **Did you use it before?**


---

I think you guys have already used this function previously.

Remember, in C++ beginner, you used to write all the code inside your `**main.cpp**` only. This file had all your code including the `**main()**` function.

But still, I believe you don't know the exact use case of **main()** function. 

No worries; you will learn it in depth in this module as you develop this game.





# Main()


---

`Main()` is not an ordinary function of the code. It is a critical part.

It is responsible for how the operating system interacts with the code. 

It triggers the OS to think that this is where the code is getting started.



```cpp
#include<iostream>
using namespace std;

int main(){

    return 0;
}
```



## Return Type


---

You guys have tried making some functions in the C++ beginner module. Do you remember its syntax? 

Every function has a return type, which signifies what the function will give in return.



Here for the `main()` function, the return type is int.

But to whom, is this `main()` returning this integer value?

Because, as far as we know, no one is calling this function.



Ahh, one second. As I just mentioned above, OS directly coordinates with this function. 

Does that mean it returns this int value to the system's OS?

YES, the OS can use this value to determine whether the code has been successfully executed.



But how? 

So, it is very simple. If the OS gets 0 from this function, everything will be perfect. 

But if it gets any other value, the code has some problem.



Any integer apart from 0 being returned is an error code. 

Each value will represent some kind of an error that the OS will recognize.





## Body


---

You see those curly braces that are known as the body of the `main()`. All the logic and code will be written there.





## Parameters


---



In the above image, you saw there is nothing in the parameter of `main()`. But sometimes, you will also come across a parameterised `main()` function. 

It looks like `int main(int argc, char* argv[])`



It is an advanced topic. You are not going to use it anywhere in this module. 

I showed it to you just to inform you that this also exists.



We won't go into details, but remember it's use case.

Developers use this `main(int argc....)` function when they want to implement the functionality of taking input through command-line arguments.





# Coding time


---

There have been many discussions about this function now.

I think you're also getting bored like me (sorry guys, but that was all needed).

Don't worry. Let's jump and do some coding.



> **TODO: Main Function**

> ✅Create a main() function

> ✅Write a cout statement "Enter your name"

> ✅Take name as the input and store it in a string variable player_name

> ✅Write a cout statement  “Great Start `**palyer_name**`, looks like you have understood the main() function properly now!”



> NOTE: Do not forget to add #include<iostream> and using namespace std;





Solution```cpp
#include <iostream>
using namespace std;

int main() {
    string player_name;
    
    cout << "Enter your name: ";
    cin >> player_name;

    cout << "Great Start " << player_name << ", looks like you have understood the main() function properly now!" << endl;

    return 0;
}
```
