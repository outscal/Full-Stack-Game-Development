> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your current branch called → ***Feature_2_OOP***

> Let’s start working on the new feature now!





Take a look around your room where you are right now. What do you see?

                                                               ![MemeToYou](//outscal.github.io/Full-Stack-Game-Development/images/9c932ff848921823.gif)

ARE YOU LOOKING????



"Pick anything that is close to you."



Did anything else in the room moved, when you did that??  (unless you have mind control probably not!!). 



Picking up an object near you will not affect other objects that are there in the room. 



![c++](//outscal.github.io/Full-Stack-Game-Development/images/2da8cae2e23828c2.png)



These Objects have their own properties and behavior, and ***they don't impact each other unless they come in contact with each other for some work.***



The world is made up of individual objects like that!!!



Object Oriented Programming or OOP is a way of coding where we replicate the world with objects.



In OOP, a programmer Organizes his code with the mindset that everything around can be represented as objects.





## why is it useful for a code to be object oriented?


---



We know that Code is a sequence of instructions, and many programs are built in this way.



But what if we want to write a program for something really big and complex like a game. 



Game code can be a few thousand to a million of lines of code. 



Without any clear organization your list of instruction will end up jumbled like a plate of spaghetti. 



With so many entangled noodles it will be nearly impossible to pull one out without disrupting the others.

 

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/08_28_2024__12_23_10.jpeg)







In OOP we can organize code in such a way that it becomes easier to maintain and change by treating things as “Objects”. 



But what is exactly an object? 

Anything that has some data and/or behavior can be an object. 



Consider any game that you have played. 

Everything that you see in that game can be treated as an object in that game. 



Everything in a Game has its own data and functions. 

Let's take a few examples to understand better…



In the pokemon game that we are going to build in this module, 

- The pokemon has:

1. **Properties: **name, Type and health
2. **Behavior:** like attacking or evolving. 



- The Player has:

1.   **Properties: **name, Type of pokemon it has
2. **Behavior:** which Pokémon it will choose.           



But they work together in the game, the player chooses the pokemon it wants, it says which attack the pokemon will do next.



Just like Objects in real world work together to keep it running :)

                                                           ![Pokemon](//outscal.github.io/Full-Stack-Game-Development/images/44ff3c99b4221b27.jpg)



You must have played the game subway surfers at least once!! (If not, your childhood was too boring.... Just Joking) Go ahead and download it once again and try playing the game (You shouldn't Play games when You study!!)

..........

..........

So, how was it? Refreshing right. 

Now, can you Think of different Objects that will be there in the game and what will be their properties and methods? Below are some snapshot to help you out!!!

![game](//outscal.github.io/Full-Stack-Game-Development/images/cc934757945c25fc.jpg)



`"These are some objects I could think of. Do they match the ones you thought of?"``Train`**Properties**: Type, Speed

**Behavior**: Movement, Collision

`Player`**Properties**: Position, Speed, Lives/Revives, Score

**Behavior**: Movement, Collision Detection, Item Collection

`Obstacles`**Properties**: Position, Type

**Behavior**: Movement, Collision Effect

`Train Tracks`**Properties**: Number of Lanes, Obstacles

**Behavior**: Endless Generation, Lane Change

`Coins`**Properties**: Type, Value

**Behavior**: Collection

`Hover Board`**Properties**: Type, Duration

**Behavior**: Protection, Activation



If you structure code as objects, then you can change one part without messing up anything else.



We have been talking all about objects but exactly how are you going to represent “objects” in your code?



Well to answer this, you actually have to know about **Classes** first. 

You will study about classes and how an object is represented in your code in the next chapter. 



Till then why don't you try thinking what other objects will be there in the Pokemon game and what will be there properties and behavior?
