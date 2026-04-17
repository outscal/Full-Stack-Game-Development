# Loops in C#


---

C# provides several types of loops, each suited for different scenarios:

1. `**for**` loop
2. `**while**` loop
3. `**do-while**` loop
4. `**for-each**` loop

Let's explore each type with examples!



## For Loop


---

The for loop is used when you know how often you want to execute a code block.



Example of `for` loop

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int room = 1; room <= 5; room++)
        {
            Console.WriteLine("You entered room " + room + " of the dungeon.");
            Console.WriteLine("You find some treasure and a mysterious item.");
            Console.WriteLine("You proceed to the next room.");
        }

        Console.WriteLine("You have explored all the rooms in the dungeon!");
    }
}

```





## While Loop


---

The while loop executes a code block as long as a specified condition is true.

You'll use the while loop in the final chapter!



## foreach loop


---

> **💡PRO TIP: *****Collections in C#***
> As the name suggests, collections are collections of data types. These can be collections of integers or strings or objects of a class or even a collection of collections. You'll use collections in upcoming Unity projects!



The `foreach` loop makes it very easy to go through each element of these collections

**SAMPLE CODE for **`**foreach**`** Loop:**  

```csharp
foreach (string color in listOfColors)
{
    Console.WriteLine(color);
}
```



Here this loop runs till whatever number of colours are there in the list.

For each iteration of this loop, `color` will store a specific element from the list (`listOfColors`).



Assume the list (`listOfColors`): Black, Blue, White, Orange, Purple

Then the output will be:

```text
Black
Blue
White
Orange
Purple 
```



***🫡Bella Ciao!***
