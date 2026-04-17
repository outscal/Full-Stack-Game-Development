You might be curious about vectors from the previous chapter.



Let’s put an end to your curiosity here,

and start learning about vectors.



In this chapter you will be learning in depth about vectors,

and how they can be incredibly useful in game development.



I am assuming you like shopping (don't be shy, I know you do).

When going for shopping, 

you make a list to keep track of what you need to buy at the store. 



Vector is similar to this list,

which allows you to create a list in your program,

to keep a track of similar items be it numbers, words, and in your case, `Pokemon`.



## what are vectors?


---



Vector in C++ is a type of container,

that allows you to store and manage a collection of items of the same type.



You can insert and delete element from vector any time because it changes it size dynamically.



> It is defined in the `<vector>` header file and provides a dynamic array that can resize itself automatically when elements are added or removed.





## how to create a vector?


---



Now what you need to know is how to create a vector?

But for that, first you need to know the basic syntax for creating a vector  



`vector<data_type> vector_name;`



`data_type` is the type of data that you will store in the vector,

and `vector_name` is the name that you want to give to the vector.



> Note: You can store any type of data in vectors as long as long as all the items in the vector are of the same type.



For example:

```cpp
#include <vector>
#include <string>
using namespace std;

vector<string> pokemonNames; // A vector to store Pokémon names
```



In the above lines of code, 

a vector `pokemonNames` is created which will store a list of strings as names of different `Pokemon`




---



You know how to create a list of `Pokemon`,

but what will you do with the empty list?



Nothing!

You can do nothing with the list,

unless you add names of the `Pokemon` in your game to it.



So, add names to it.

But how will you do it?



We have `push_back()` method in vectors for this purpose. 



You have to call the `push_back()` method,

and pass the value that you want to insert in the vector.



It adds the value at the back of the vector.



Example code:

```cpp
pokemonNames.push_back("Pikachu");
pokemonNames.push_back("Charmander");
pokemonNames.push_back("Bulbasaur");
```



In the above lines of code, `push_back()` method is used to insert `"Pikachu"`, `"Charmander"` and `"Bulbasaur"` into the vector `pokemonNames`



Now that you know how to add names to the list of `Pokemon`, 

it's time that you learn different types of operation that can be performed in vectors.



let's see what they are.



## Accessing and Using Items in a Vector


---



Accessing elements in vectors is very easy. 

You just need to write the name of the vector, 

and the index of the element which you want to access inside square brackets.



**Syntax:**

`name_of_vector[ index_of_the_element ]`



Let's print out the name of the first `Pokemon` in the vector `pokemonNames`



Example Code:

```cpp
cout << "The first Pokémon is: " << pokemonNames[0] << endl;
```



Output:

```cpp
"The first Pokémon is: Pikachu"
```





## Iterating Through a Vector


---

If I ask you to print the name of all the Pokemon in your `pokemonNames` ,

how will you do it?



Write a `cout` statement for each element?

What if your vector has 100 elements? 

Will you write 100 lines of `cout` statements?



But coding is all about reusing codes by making small changes.



Yes,

You will iterate through your vector. 



We can use a simple for loop to iterate over the list,

right?



Let's see how you can do that. 



Example Code:

```cpp
for (int i = 0; i < pokemonNames.size(); i++) { 
cout << "Pokémon " << i + 1 << ": " << pokemonNames[i] << endl; 
}
```



This loop will go through each item in `pokemonNames` and prints it out, 

showing how easily you can manage and use the list.
