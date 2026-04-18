> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your current branch called → ***Feature_7_Inheritance***

> Let’s start working on the new feature now!



Programmers strive to be as efficient/lazy as they can be. *(In a good way!)*



![r/ProgrammerHumor - Lazy programming](//outscal.github.io/Full-Stack-Game-Development/images/ff59574ed49d741e.jpg)



Therefore, over the years programmers have figured out various ways to **do less work**.

Re-writing the same piece of code in a different place in your program feels like a sin, ***it is wrong***.



This is why we have the **DRY** principle → **Don't-Repeat-Yourself**.



![7 Software Development Principles Boiled Down to Memes | by Jose Granja |  Better Programming](https://miro.medium.com/v2/resize:fit:1200/1*TwfpCvvZsuKzQTt3KGK0NA.jpeg)



Repeating code makes your project harder to manage and prone to errors. 

The DRY Principle helps you write clean, efficient, and maintainable code by avoiding repetition.





You’ve already created a **Pokémon** class and used it to create different Pokémon. 

These Pokémon can battle each other, which is a great start!



But there’s one problem. All your Pokémon behave the same way. 

They have the same properties and perform the same actions, making the game feel a bit boring.



# The Problem


---



Right now, all your Pokémon share the same behaviors. 



But imagine adding special abilities, like a **Fire-type Pokémon** that can use powerful fire moves 

or a **Water-type Pokémon** that can heal itself.



**For example : **

What if you wanted Pikachu to use a special move like **Thunderbolt**? 

You might think you need to create a new class for Pikachu with all the properties of the Pokémon class plus the new **Thunderbolt** ability.

But wait—that's a lot of work! You’d be repeating code.



And if you have 100 different Pokémon, each with its own special move, you’d end up writing the same things over and over again. 

This breaks the **DRY Principle**.





Instead of repeating code for each Pokémon.

You need to think of a way to **not re-write code** that stays the same for all Pokémon. 

This is where **Inheritance** comes in.



# Inheritance


---



Inheritance lets you create a **base class** that contains common features for all Pokémon.

Then, you can create **specialized classes** for Pokémon like Pikachu, Charmander, or Squirtle. 

These classes will inherit everything from the base class and can also have unique abilities.







Imagine a family tree. 

At the top, you have the grandparents, then their children, and finally the grandchildren.



![Placeholder](//outscal.github.io/Full-Stack-Game-Development/images/1f53977b6b52a382.png)





Imagine there is a base class called **Parent**. 

All the children in the family tree inherit things from the Parent, like eye color, hair type, etc. 

But each child can also have unique traits of their own, like one might be good at sports while another is good at art.



The same idea applies in programming.



In code, inheritance works like this:

- You have a **Base Class** (also called a **Parent Class** or **Super Class**) that contains common features.
- Then you have **Derived Classes** (also called **Child Classes** or **Sub Classes**) that inherit these common features but can also have their own unique features.







![Placeholder](//outscal.github.io/Full-Stack-Game-Development/images/1968f1171b962d84.png)



Children take some features from their parents and have some features unique to them.

Similarly, Inheritance allows the code inside a base class to be reused by all the child classes that inherit from it. 



So all the common code of Class A, Class B and Class C in the above diagram, is inside Base Class!

And all the unique code is inside the child classes themselves. 




---



Think about birds. All birds have wings, feathers, and the ability to lay eggs. 

So, you can create a **Bird** class that contains these common traits.

But not all birds are the same. 

A **Penguin** is also a bird, but it can’t fly. Instead, it can swim! 



So, you can create a **Penguin** class that inherits all the common traits of the **Bird** class,.

but you can add a special swimming ability to it.



This way, you don't have to repeat the basic information about birds when creating the **Penguin** class. 

Inheritance makes the code simpler and more organized.



![img](//outscal.github.io/Full-Stack-Game-Development/images/2de8d3cdda899a59.png)



Penguin Class Inherit all the trait from Birds Class.

and Have Extra Functionality of **swim.**



# Inheritance for Pokemon


---



Now, let’s apply this to your Pokémon game.

You already have a **Pokémon** class with common properties like health and attack power. 

But some Pokémon, like Pikachu, might have special abilities such as **Thunderbolt**.



With inheritance, you can create a new class for Pikachu that inherits all the common features from the **Pokémon** class. 

Then, you can add Pikachu’s unique move **Thunderbolt** without having to rewrite all the other code.

This way, each Pokémon can have special moves or abilities without you needing to repeat code.





In the next lesson, you'll learn about different types of inheritance.

This will let you give your Pokémon unique moves, like Pikachu's **Thunderbolt**.

It’ll make your game more exciting and help you stick to the **DRY Principle.**



No more repeating code—just smarter, cleaner programming.
