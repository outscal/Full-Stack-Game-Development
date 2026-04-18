In the previous lesson, 

you studied about inheritance, 

and how it can be used in your game.



Can you think of other Pokemon examples in your game, 

that you can create using inheritance?



I can think of creating `Charmander` with his unique move `flameburst`, 

and `Squirtle` with his move `waterSpalsh`.



If you remember the example of`Pikachu` class, 

that I gave you in the previous lesson, 

then you will know that to create `Pikachu`,

you will create a `pikachu` class first.



`Pikachu` class will inherit the `**Pokemon**` class, 

and then you can simply add a method for Pikachu’s unique move `**Thunderbolt**`**,**

without having to rewrite the code for the common features of `Pikachu` again.

This is an example of **single inheritance.**



**Single inheritance*** is basically when a single child class inherits from one base class.*





![Image](/Full-Stack-Game-Development/images/3168c8b04fc1edb2.png)






The `Pokemon` in the picture above is known `Volcanion`.

It is a dual type of **Fire/Water** Pokemon, 

that can use both Fire-type and Water-type moves.

How will you create this `Pokemon` in your game?



You will write a separate class for this Pokemon, 

which will inherit the base class Pokemon,

and then you will add the same `watersplash` and `flameburst` moves to this class. 



But you have already created a class for `Charmander`,

and another class for `Squirtle`, 

where you have declared and defined the moves `flameburst` and `water splash.`



Why are you writing the same code again?



You might be thinking, 

if the `Volcanion` class can inherit these two classes,

then there is no need to write the same code again. 

But can you do that?



Yes, you can! 

A single class can inherit multiple classes at a time. 

You can create `Volcanion` without writing the extra code for `flameburst` and `waterSplash` moves.



*And this type of inheritance is known as ***Multiple Inheritance.**



- **Multiple Inheritance:  **A derived class inherits from more than one base class. Multiple inheritance allows a class to combine the features of several base classes.



![Placeholder](/Full-Stack-Game-Development/images/1ee16c495f442f5b.png)






Suppose you are creating another Water Pokemon `Blastoise`,

other than `Squirtle`, in your game.

Blastoise can use the Water-type move `**Hydro Pump**` in addition to `**Water Splash**`.





![Blastoise | Wiki | •Pokémon• En Español Amino](https://pm1.narvii.com/6554/21933ce6c6eaead7ec2c28b19d57dafcdc0a5b0a_hq.jpg)






Will the `Blastoise` class inherit both the base class `Pokemon` and the `Squirtle` class?



But `Squirtle` have already inherited the base class `Pokemon`,

and so, if `Blastoise` inherits `Squirtle`, 

then it should naturally have the access to the base class `Pokemon`.

And then you can simply add your other unique move for Blastoise `Hydrapump()`. 



*This type of inheritance is known as ***Multilevel inheritance**



- **Multilevel Inheritance: **A derived or child class can have a class that derives from it. This increases the length of the chain and is known as multilevel inheritance.

 ![Placeholder](/Full-Stack-Game-Development/images/86e9235da2b94fdc.png)




All the new classes that you have created for `Charmander`, `Bulbasaur`, `Pikachu`, 

are inheriting the same common features `health` and `attackPower` from the base class `Pokemon`.



*This type of inheritance where multiple child classes are inheriting from a single base class is known as ***Hierarchal Inheritance.**

 

- **Hierarchal Inheritance:** When a single base class has various classes that derive from it.



![Placeholder](/Full-Stack-Game-Development/images/1968f1171b962d84.png)




Another type of inheritance that you need to know is **Hybrid Inheritance**



- **Hybrid Inheritance:** This is a mixture of any of the above types.



![Placeholder](/Full-Stack-Game-Development/images/4138196f5dadd24e.png)






However, you need to be careful when using Hybrid Inheritance since it can lead to issues like the **diamond problem**. 

*(We will discuss what the diamond problem is in detail much later.)*






---



Let's see again how inheritance benefits developers in building game- **Reusability:** Shared code lives in the base `Pokemon` class.
- **Extensibility:** We can easily add new Pokémon types with unique abilities without modifying the base class.





Now try to answer the question below,

Which type of inheritance would you use to create a more specialized Pokémon, such as a Legendary Pokémon with unique abilities?



In the next lesson, 

you’ll gain hands-on experience with inheritance,

by creating different Pokemon classes with unique abilities, 

which will make the battles in your game even more dynamic and fun!
