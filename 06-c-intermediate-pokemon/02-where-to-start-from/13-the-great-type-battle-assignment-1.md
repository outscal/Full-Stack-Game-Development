> [Click here](https://outscal.com/compiler/the_great_type_battle) to this assignment.

> Go to this link and start writing your code.

> **NOTE:** This assignment is independent of your game code.





**Professor Oak’s Voice:**



"Young Trainer!" 

"You’ve been doing a fantastic job so far." 

"But a new challenge awaits, one that even I am struggling with in the lab!" 

"Today, we’re dealing with a *type confusion* like no other!" 

"We need your help to solve this puzzle with the power of **Enum Classes**."




---



🟡 **The Problem:**

- - There’s chaos in the Pokémon Lab! Our systems are getting confused because they can’t tell the difference between various item types in the inventory.



- - We have different kinds of items: **Healing Items** and **Battle Items**, but both categories share similar names like **Potion** and **Elixir**.



- - This has caused the system to apply a battle effect when you wanted to heal your Pokémon. We can’t have that happen, can we?



Take a look at the current state of the code that is causing the issue:



```cpp
// Current Enums causing confusion in the lab
enum HealingItems {
    Potion,
    Elixir
};

enum BattleItems {
    Potion,
    Elixir
};
```



**Professor Oak’s Voice:**



"You see the problem, don’t you?" 

"The same names are used for different purposes in different enums." 

"The Potion from HealingItems heals," 

"but the Potion from BattleItems boosts attack in battle!" 

"The system can’t tell them apart, and chaos ensues!"




---



🟢 **Your Mission:**

**Step 1:**

- - - Convert the **HealingItems** and **BattleItems** enums into **Enum Classes**. This way, each type of item will have its own unique identity, even if the names are the same!

**Step 2:**

- - - Update the main function to show the correct usage of these **Enum Classes (Use Scope Operator ::)**.

**Step 3:**

- - - Print out the correct effects based on the item types, showcasing that the system now knows exactly which Potion you’re using!




---



🟡 **Bonus Challenge:**

- - Add a **switch** statement for both **HealingItems** and **BattleItems** inside your main function that prints out a unique message depending on which item is being used.




---



**Professor Oak’s Voice:**

"Fantastic! By converting the enums into **Enum Classes**,

"you’ve made the lab systems more organized and precise. 

"Now, each item is recognized properly, 

"and your Pokémon won’t accidentally drink an attack potion when they need healing! 

"This is why **Enum Classes** are so valuable—order from chaos, my dear student!"




---



### **Expected Output in Console:**



When you run your updated code, you should see the following output:

```cpp
Healing Potion used! Your Pokémon recovers HP!
Battle Potion used! Your Pokémon's attack power rises!
```



# Submission Instructions


---

> Submit your personal generated link below after completing your code.
