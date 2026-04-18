Think about how you use a computer. 
You press buttons, use the mouse, and see things on the screen. 



You don’t need to know how everything inside the computer works. 
You just know that when you press a button, something happens. 



This is called a **User Interface**.

![img](/Full-Stack-Game-Development/images/6f2e3c52ebc94e9e.png)





In programming, an **interface** works the same way. 
It helps different parts of your code communicate with each other. 



In object-oriented programming (OOP), 

An interface is like a set of rules that tell classes what to do.
But it doesn’t tell them how to do it. 



It’s like saying, “You need to do this,” but not explaining how exactly.






---



Now, let’s imagine you are making a game. 
In this game, your character can throw rocks, shoot arrows, and fire bullets. 
Each of these things moves in different ways—rocks are slow, arrows are faster, and bullets are even faster. 


They cause different amounts of damage, too.



![img](/Full-Stack-Game-Development/images/1ca23b90dc440a17.png)




But even though they are different, all of these projectiles have something in common. 
They all need to move, they need a direction, and they need to start from a position. 

Rather than defining how each projectile behaves in separate classes.
*Wouldn’t it be easier to create a common set of rules that every ****projectile**** must follow?*



![img](/Full-Stack-Game-Development/images/42e0f598eacff91d.png)





To achieve the above in our game,
You might have methods called `setInitialDirection()` and `setInitialPosition()` inside a method called `throw()` or `fire()` inside both the bullet and the rock object.



**throw() Method :**

```cpp
class Rock
{
   void throwRock()
   {
       setInitialDirection();
       setInitialPosition();
       move();
   }
}
```



**fire() Method:**

```cpp
class Bullet
{
   void fireBullet()
   {
       setInitialDirection();
       setInitialPosition();
       move();
   }
}
```



You might think that, oh these are only two things, its not an issue.

However, imagine you have 20 different things in your game in the future that work in a similar way.

Like an arrow, or a missile, that apply damage to the enemy.



The enemy will need a reference for each of these 20 objects.

And the code inside all these 20 classes will have same methods like `**setInitialDirection()**` , `**setInitialPosition()**`** and **`**move()**`



Here is where an interface comes in.

Instead of talking to the 20 objects, would it not be easier to talk to one thing instead.

But how do we do that?





# Interface


---

An interface is a set of pure virtual functions that acts like a **contract**. 

It tells the projectiles, ‘You must have a `move` method and a `setInitialDirection` method.

But it doesn’t care how they implement them.



![img](/Full-Stack-Game-Development/images/3bf2989e448afc94.png)





**Let’s see an example:**

```cpp
class IProjectile {
  public:
    virtual void move() = 0;
    virtual void setInitialDirection() = 0;
    virtual void setInitialPosition() = 0;
};
```



This `IProjectile` interface tells any projectile—like a rock, arrow, or bullet.

All of these **must** have three functions: `move()`, `setInitialDirection()`, and `setInitialPosition()`. 

The interface doesn’t care how each projectile moves, it only cares that they all move.




---



Let’s say you have an enemy in your game. 

Without an interface, the enemy would need to know how to handle every type of projectile—how to deal with rocks, arrows, bullets, and more. 

This would make the game’s code very complicated.



With an interface, the enemy only needs to know one thing: “This is a projectile.” 
It doesn’t matter if it’s a rock or an arrow. 
The enemy can interact with all projectiles the same way, because all projectiles follow the same rules.



Now that you understand **what an interface is**.
And how it helps us manage similar objects in our game.
You can see why it’s such an important concept in programming. 



It handle many different types of objects in a simple and organized way. 


By following the same basic rules
our code becomes easier to write, easier to manage, and much more flexible.






---



In the next lesson,
You’re going to create an interface specifically for **status effects**. 
This will help us manage different effects like Burn, Sleep, and Paralysis in a clean, organized way.



**Great Job🎉!**
