In this lesson, let's see how you can create and traverse an array of a built-in data type.

To understand the syntax and implementation of an array, now we will consider some real-time game dev. examples. 
For this, we are going slightly away from our actual project minesweeper.

But don’t worry, once we understand the syntax, we will come right back to it…



**Note: **I recommend you implement the code in this lesson while reading it, in our [**Compiler**](https://outscal.com/compiler/arrays).
Refer to this [**content**](https://outscal.com/course/full-stack-game-development/text-based-adventure-game/getting-started-with-letho-using-c/using-outscals-compiler-content-3) if you're not familiar with outscal's compiler.



Let's consider an example of scores of 5 players for this lesson.

How will you create an array of scores?



## **Creating an Array**


---

In C++, an array is defined by specifying the type of its elements and the number of elements it will hold.

The syntax for declaring an array is:

`data_type arrayName[arraySize];`

- `**data_type**` is the data type of the elements (e.g., `**int**`, `**double**`, `**char**`).
- `**arrayName**` is the name of the array.
- `**arraySize**` is an integer constant greater than zero, representing the number of elements in the array.

For example, to declare an array named `**scores**` that can hold 5 integers, you would write:

```cpp
int arraySize = 5
int player_scores[arraySize];
```

Now, how do you add scores in the array?🤔



## Initializing an Array


---

An array can be initialized in 2 ways:

1. At the time of declaration.
2. By *traversing* each element of the array

```cpp
int player_scores[arraySize] = {10, 20, 30, 40, 50};
```

This is how the `player_scores` array looks:


![ ](//outscal.github.io/Full-Stack-Game-Development/images/d34d3f4637adefea.png)



Now, let's understand another way of initializing an array which is using a for-loop.

To initialize each element, you first need to access each element.



## **Accessing Array Elements**


---

Elements of an array can be accessed if you know the `**index**` of the elements.

What is an index? 🤔

Well, an index is just the numbering of elements that starts from `**0 to arraySize - 1**`



![ ](//outscal.github.io/Full-Stack-Game-Development/images/a54dd190ceafd64e.png)



So, if an array like `player_scores` has 5 elements, then it'll have its index from `**0 to (5-1)**` = `**0 to 4**`



Now you know the indexes of the elements.

But, how to use the index to access the elements?🤔

Elements of an array are accessed using the index operator (`**[]**`). 

The syntax for accessing an element at a particular index `**i**` is:

`arrayName[i]`

For Example: `player_scores[0]`, `player_scores[1]`, `player_scores[2]`, `player_scores[3]` and `player_scores[4]`



> **TODO: **[**Compiler**](https://outscal.com/compiler/arrays)
> **✅ **Declare a `player_scores[arraySize]` array.
> ✅ Initialize the `player_scores` array.
> ✅ Print the element at `index = 0`



 As you have now learned about accessing (using the [ ] operator), it will be fairly easy.

```cpp
int player_scores[5];

for(int i=0; i<5; i++) // loop goes from 0 to 4 (array indexing starts with 0)
{
			player_scores[i] = (i+1) * 10; // here with [i] , we are accessing each element and initializing it with the value of (i+1) * 10
}
```



Now, you can also print the array elements by traversing them:

Example:

```cpp
for(int i = 0; i < 5; i++ )
{
			cout<<"Score of the player " << i << " is " <<player[i] <<endl;
}
```



> **TODO: **[**Compiler**](https://outscal.com/compiler/arrays)
> **✅ **Initialize the `player_scores` array using a for loop.
> ✅ Print all the elements of the `player_scores` array using a for loop.




<iframe src="https://www.loom.com/embed/b72c8bbb5b6a4d9abeebedf8c9ce2d60" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





You now know how to create, initialize, and traverse an array.

But do you how memory is allocated to an array?🤔



## Memory Allocation of an Array


---

![ ](//outscal.github.io/Full-Stack-Game-Development/images/d1a4c8e600555979.png)




Memory Address of each element can be calculated using this formula: `base-element-address + index * datatype-size`

If the first element is at `200` memory address
1 integer occupies 4 bytes of memory
The second will be `200 + 1 * datatype-size` = `200 + 1 * 4` = `204`
Similarly, the third element will be at `200 + 2*4 = 208`

**Note: **200, 204, 208, etc are just examples of memory addresses.


You know now about arrays in detail!

And you have also created your array 💪🏼

Now let's understand some core operations of arrays:

- Inserting a new element
- Deleting elements
- Searching an element



Let's start understanding the operations one by one. Starting from inserting a new element.



## Inserting Elements in an Array


---

Elements can be inserted into an array at a specific position if you know the `index` where you want to place the new element.

What is insertion?🤔

Well, insertion is adding a new element at a specific index, which requires shifting elements to make space.

So, if an array like `player_scores` has 5 elements `{10, 20, 30, 40, 50}` and we want to insert `100` at index `2`, we need to shift elements at and after the index `2`.

Now you know what insertion means. But, how to insert an element in an array?🤔 

Insertion in an array requires three steps:

1. Shift elements to the right
2. Insert the new element

The syntax for inserting an element at a particular index `position` is:

```cpp
int insertIndex = 2;
int valueToInsert = 100;

//Shift the elements to right
for(int i = arraySize-1; i >= insertIndex; i--) {
    player_scores [i+1] = player_scores [i];
}

// Insert the new element
player_scores [insertIndex] = valueToInsert;

//print the updated array
cout << "Updated array after insertion: ";
for (int i = 0; i < arraySize; i++) {
    cout << player_scores[i] << " ";
}

```

For Example: If `player_scores = {10, 20, 30, 40, 50}` and we insert `100` at position `2`:

- This is how the elements shift:
- - `{10, 20, 30, 40, 0}` (50 is removed from the array to make space) -> `{10, 20, 30, 40, 40}` -> `{10, 20, 30, 30, 40}` -> 
    `{10, 20, 100, 30, 40}` 
- After insertion: `**{10, 20, 100, 30, 40}**`



> **TODO: **
> ✅ Insert `100` at index `2`. 
> ✅ Print the updated array to verify insertion.



Here are some more game dev examples where inserting can be used:

- Insert enemies at the beginning of the list
- Insert power-ups in an inventory
- Insert checkpoints dynamically
- Insert scores in a sorted list
- Insert waypoints dynamically



Now, let's see the deletion of elements.



## Deleting Elements from an Array


---

Elements can be deleted from an array at a specific position if you know the `index` of the element you want to remove.

What is deletion? 🤔 

Well, deletion is removing an element at a specific index, which requires shifting elements to the left to fill the gap.

So, if an array like `player_scores` has 5 elements `{10, 20, 30, 40, 50}` and we want to delete the element at the index `2` (which is `30`), we need to shift elements after the index `2` to the left.

Now you know what deletion means. But, how to delete an element from an array?🤔 

Deletion in an array requires two steps:

1. Shift elements to the left
2. Update the array

The syntax for deleting an element at a particular index `position` is:

```cpp
int deleteIndex = 2;

//Shift the elements to left
for(int i = deleteIndex; i <= arraySize-1; i++) {
    player_scores[i] = player_scores[i+1];
}

//print the updated array
cout << "Updated array after deletion: ";
for (int i = 0; i < arraySize-1; i++) {
    cout << player_scores[i] << " ";
}

```

For Example: If `player_scores = {10, 20, 30, 40, 50}` and we delete the element at the position `2`:

- This is how the elements shift:
  `{10, 20, 30, 40, 50}` -> `{10, 20, 40, 40, 50}` -> `{10, 20, 40, 50, 50}` -> `{10, 20, 40, 50, 0}`



> **TODO:** 
> ✅ Delete the element at index `2`. 
> ✅ Print the updated array to verify deletion.



Here are some more game dev examples where deleting can be used:

- Remove defeated enemies from an active enemy list
- Remove collected power-ups from the inventory
- Remove obsolete waypoints when a player reaches them
- Clear a completed quest from the player's quest log
- Remove old high scores when the leaderboard exceeds a limit



Lastly, let's see how we can search for an element in an array.



## **Searching in an Array**


---

Finding specific elements in an array is called searching. You need to check each element until you find the one you're looking for.

What is searching? 🤔 

Well, searching is examining each element one by one until you find the element you're looking for or reach the end of the array.

So, if an array like `player_scores` has 5 elements `{10, 20, 30, 40, 50}` and we want to find if the value `30` exists, we need to check each element until we find it.

Now you know what searching means. But, how to search for an element in an array?🤔 

Searching in an array requires a simple approach:

1. Check each element one by one
2. If found, return the index
3. If not found after checking all elements, return -1

The syntax for searching an element in an array is:

```cpp
int searchValue = 30;
int foundIndex = -1;

//Search for the element
for(int i = 0; i < arraySize; i++) {
    if(player_scores[i] == searchValue) {
        foundIndex = i;
        break; // Exit loop once found
    }
}

//print the result
if(foundIndex != -1) 
{ 
		cout << "Player score " << searchValue << " found at index " << foundIndex << endl; 
} 
else 
{ 
		cout << "Player score " << searchValue << " not found in the array" << endl; 
}

```

For Example: If `player_scores = {10, 20, 30, 40, 50}` and we search for value `30`:

- This is how the search progresses:
- Check index 0: `player_scores[0]` is 10, not equal to 30
- Check index 1: `player_scores[1]` is 20, not equal to 30
- Check index 2: `player_scores[2]` is 30, equal to 30! We found it and exit the loop.
- Result: Element 30 found at index 2



> **TODO:** 
> ✅Search for a value in the array. 
> ✅Print the result to verify if the element was found.



Here are some more game dev examples where deleting can be used:

- Search for a specific item in an inventory
- Find the last checkpoint the player activated
- Locate an unused weapon slot for picking up a new weapon
- Check if a player has already completed a specific quest



But as you know, everything comes with its pros and cons.

So, let's understand the pros and cons of Arrays.

# Pros and Cons of Using Arrays


---



## **Advantages**


---

✅ **Fast Access:** Arrays allow **instant access** to any element using its index, making them highly efficient for retrieving game data (e.g., player inventory, enemy positions).

✅ **Performance-Friendly:** Arrays are stored **contiguously in memory**, leading to **faster processing** in performance-critical game loops.

✅ **Simple to Use:** Arrays provide a **basic structure** for managing game elements like UI menus, player stats, or animations. You’ll see more advanced structures in future modules.



## **Limitations**


---

❌ **Fixed Size:** If an array is **too large**, it wastes memory (e.g., a 1000-slot inventory but only 300 items). If it’s **too small**, it may not fit all elements (e.g., needing 1500 enemy spawn points but only allocating 1000).

❌ **Manual Shifting:** Inserting or deleting elements requires **shifting** other elements, which adds **extra processing** (e.g., removing an item from an array shifts all items backwards).

- These operations are **not needed** in dynamic structures like **linked lists or vectors**, which you'll learn later.



> 💡 **Protip:** 
> In future modules, you'll explore **dynamic data structures** that overcome these limitations, allowing flexible memory allocation.



Here's a summary of the lesson:

> **Summary📃**
> 🔸Arrays can be made of other data types like char, float, double, etc.

> 🔸Array indexing starts with zero.

> 🔸**Direct Accessing:** If you know the index of an element, you can directly access it.

> 🔸**Fixed in size**: Array always has a fixed size. The size of the array can not be changed once declared.

> 🔸**Linear**: Array stores data in a linear order.

> 🔸**Homogenous nature**: The array contains the same elements throughout the data structure. 
> 🔸In this case, it is an integer array, so all of the elements in this array will be integers only.

> 🔸**Size of an array:** This array has 5 integer elements and  `int` is of `4 bytes`, so the total of array = `5 * 4 = 20 bytes`

> 🔸**Continuous Memory Allocation:** All elements of the array are stored contiguously in memory



Since you've understood arrays, it's time to explore a fundamental concept in programming: **time and space complexities!** 

We'll start with Time complexity in the next lesson.

**See you in there!👋🏼**
