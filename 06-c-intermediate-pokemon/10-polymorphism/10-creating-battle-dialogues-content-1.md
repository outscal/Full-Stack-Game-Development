So far, you have learnt many topics of Polymorphism,



But do you still remember?

What your actual goal was.



Your major goal was to implement individual functionalities,

for different types of Pokemon.



That's why you started learning Polymorphism.



So what are you waiting for?



Let's Goooo!





# Coding Time


---

Currently,

when you call `attack()` for any Pokemon,

just a single line comes up.



For examples

```cpp
cout << name << " uses Flame Thrower on " << target->name << "!\n";
target->takeDamage(20);
```



`attack()` function of **Charmander** Pokemon triggers the above lines of code.

It looks really boring.



Let's try replacing it with something interactive with the player.



Charmander```cpp
cout << name << " used FLAME THROWER!\n";
N_Utility::Utility::waitForEnter();

cout << "...\n"; 
N_Utility::Utility::waitForEnter();

target->takeDamage(attackPower);

if (target->isFainted())
    cout << target->name << " fainted!\n";
else
    cout << target->name << " has " << target->health << " HP left.\n";
N_Utility::Utility::waitForEnter();
```





Let me show you one more example.

Currently, **Pidgey** has a really basic cout statement.



```cpp
cout << name << " uses Wing Attack on " << target->name << "!\n";
target->takeDamage(20);
```



I have converted it to



Pidgey```cpp
cout << name << " used WING ATTACK!\n";
N_Utility::Utility::waitForEnter();

cout << "...\n"; 
N_Utility::Utility::waitForEnter();

target->takeDamage(attackPower);

if (target->isFainted())
    cout << target->name << " fainted!\n";
else
    cout << target->name << " has " << target->health << " HP left.\n";
N_Utility::Utility::waitForEnter();
```





So, for the rest of the **Pokemon** types,

It's your task to change the conversation.

And make it interactive.



It is not a compulsion,

to do exactly how I did it.



After all, it's Your Game!!

You can do whatever you like.



You may change the conversation style,

according to your preferences.



Before ending this lesson,

I want to ask you a question.

Is there anything wrong with your code structure?

Think a little bit about this.
