Up to this point, you’ve learned about pointers and memory address.

Pointers are variable that store address of a variable.

And through memory address we can access the value of unknown variable.



But Why do you create a Pointer ?

Until now, you didn’t need a pointer, so what changed?



Remember-How you created a object of player in player class ?

```cpp
Player player;
```



This statement creates a Player object named `player` in memory, and the memory is managed automatically.
When the `Player` class or the block where `player` was created ends, the memory is freed.



# new Keyword


---



Now, let’s check another way to** create objects **:

```cpp
Player* player = new Player();
```



On the **left-hand side (LHS)** of the equation 

`Player* player` declares a pointer variable named `player` that can store the address of a `Player` object.



On the **right-hand side (RHS)**

 `new Player()` creates a `Player` object in memory and returns the memory address of this object.



Putting it together :

- `Player* player = new Player();`: 
- The pointer `player` on the LHS is assigned the address of the `Player` object created in the memory by the RHS.





# What is the Difference Between the Two Methods?


---



When you create an object directly, like this:

```cpp
void someFunction() {
    Player player; // Object is created and destroyed within this function
    // ...
}
```



The program manages the memory for the object. 

The `player` object will be destroyed when it goes out of scope, in this case when the function ends. 

This means you don’t need to worry about manually freeing the memory.



*But we might want manual control over the lifetime of an object.*



To do so we use the second method which allocates new memory for a Player object. 

Here, the programmer (YOU) is responsible for managing the lifetime of the object.



# delete keyword


---



When the object is no longer needed the programmer needs to manually delete the memory by calling the` delete `keyword.



For every **new** keyword, there should always be a **delete.** 

Otherwise, we get a 'memory leak'.



If we don’t free the memory then our computer has less free memory to allocate,.

Which causes it to slow down, and potentially crash.



```cpp
delete player; // Explicitly delete the object to free memory
```




---



When creating objects without pointers, you access properties like this:

```cpp
Player player;
player.player_sprite;
```



But with pointers, the syntax changes slightly:

```cpp
Player *player = new Player();
player->player_sprite;
```



The `->` operator is used to access properties and methods of the object pointed to by `player`.



Now that you understand the basics of creating objects with `new` keyword.

We'll consider some best practices and common pitfalls in our next lesson to help you use pointers effectively.
