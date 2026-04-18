In the last chapter, we talked about the excitement of encountering wild Pokémon.

In different areas like tall grass, caves, and water. 

Where these Pokémon can hide.



**Professor Oak :**

Before You can find wild Pokémon.

          You need to make a place for them to hide.

          Let's set up some grass where Your Pokémon can stay and surprise us!



![img](/Full-Stack-Game-Development/images/59e6c3565655f8bf.png)



To bring the excitement of wild Pokémon into our game.

You need to represent the "grass".

Just like the tall grass in Pokémon games.



Your "grass" will hold details about the wild Pokémon that live there.



*Can you guess what information the grass will store?*



To keep track of Pokémon in different areas.

You need to store several details.



You need to know the types of Pokémon, how rare they are, and what the environment is like.

Instead of using separate variables for each piece of information, which can get messy.



This is where  **Structs **come into play!



# What is Struct ?


---



A `struct` in C++ is like a special box that holds related pieces of information together.

It helps keep your code neat and easy to read.



Think of it as a way to organize all the info about something, like our patch of grass.

You can use a struct to keep all the details about the grass and the Pokémon that live there in one place.



Now, Lets start to understand how you will create grass in the game code.

And Let's first understand the syntax and structure of `struct`.



# Syntax and Structure


---



Basic Syntax of struct in C++.

```cpp
struct StructName {
    // member variables
};
```



**First**, you use the keyword `struct` to start. 

This tells the computer you are creating a new struct.



**Next**, you give the struct a name, like `Grass.`

so you know what it represents.



Inside the curly braces `{}`, you list the `member variables`. 

These are the pieces of data you want to store.





# Building **Grass** Struct


---

Let's build the `Grass` struct to show where wild Pokémon can be found.



Here's what our `Grass` struct will include:



**1. Pokémon list**

This will store the different types of Pokémon you might find in this patch of grass.



**2. Encounter rate **

 This tells us how often you'll come across a wild Pokémon in this area.



**3.Environment type **

 This describes where the grass is located—like a forest, a mountain, or near a river.



> TODO:

> ✅Create a header file `grass.hpp` in the same folder in which contains main.cpp. [Till Now all different files are still here]
> ✅Create a struct, and Struct name should be `Grass`.
> ✅ Add the** Pokémon List**:  use vector to store `wildPokemon` & vector should contain the value of `Pokemon` type.
> ✅ Set the** Encounter Rate**: make it a `int` variable.
> ✅ Describe the** Environment**: store the environment of grass in `string`.



** Can you Think of building this struct?**



> 💥**NOTE **:  Include string & vector header files in `grass.hpp`.



grass.hpp - Click Here```cpp
// grass.hpp
#include<string>
#include<vector>
using namespace std;

struct Grass {
    string environmentType;  // Example: "Forest", "Cave", "Riverbank"
    vector<Pokemon> wildPokemonList;  // List of wild Pokémon that live in this grass
    int encounterRate;  // Likelihood of encountering a wild Pokémon, out of 100
};
```




---



Now that we've built our `Grass` struct.

it's a great time to explore how structs and classes differ.



## Structs vs Classes: What’s the Difference ?



Youe’ve just created a `Grass` struct. 



**Professor oak :**

** **You might wonder why we picked a struct for the grass and not a class.

           *class also contain different set of data.*



![img](/Full-Stack-Game-Development/images/59e6c3565655f8bf.png)



So the **Key difference between struct and class** is :



They’re typically used for simple data grouping without behavior (methods). 

In our case, the grass just holds data about the environment and Pokémon—it doesn’t need methods to perform actions.

Though structs can have methods, they're meant to be lightweight(small amount of data) containers.



On the other hand, classes are more powerful. 

They usually represent entities that not only store data but also have behaviors (methods) attached to them.

Like our `Pokemon` class that has methods for attacking.



In structs, the default access level is public, while in classes, it is private. 



This means that the data in structs is accessible by default.

Which is fine for a simple data holder like our grass. 



For more complex entities with behaviors, we use classes.

Where we might want to protect some of the data.





# Putting It All Together


---



Let’s add real data to our `Grass` struct. 

and create few instance or object of struct.



**Example 1 :**

forestGrass has an environment of "Forest," contains Pokémon like Pidgey and Caterpie.

And has a 70% chance of encountering a Pokémon.



`**Game.cpp**`

```cpp
Grass forestGrass = {
    "Forest",
    {{"Pidgey", PokemonType:: NORMAL, 40}, {"Caterpie", PokemonType:: BUG, 35}},
    70
};
```



**Example 2 :**



> TODO:
> ✅Add a Data to struct, and StructName should be `caveGrass`.
> ✅ caveGrass represents a cave with Pokémon like **Zubat **and **Geodude**, and an 80% chance of encounters.

**          **



**caveGrass -  Solution**```cpp
Grass caveGrass = {
    "Cave",
    {{"Zubat", PokemonType::POISON, 30}, {"Geodude", PokemonType::ROCK, 50}},
    80
};
```





Try creating your own patches of grass! 

Think about different environments and which Pokémon would live there. 

Adjust the Pokémon lists and encounter rates to make your game more exciting!




---



You might have noticed `std::vector` in the struct. 

It’s a way to handle lists of items that can grow or shrink as needed. 



**Professor Oak :**

You might wonder what these **vectors** are and how they work.

          Don't Worry, You will learn about vectors in the next lesson.



![img](/Full-Stack-Game-Development/images/59e6c3565655f8bf.png)



**Great Job !**
