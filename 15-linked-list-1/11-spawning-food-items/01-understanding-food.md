> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your main branch called → [ `**Feature-3-Food-Spawning**` ]

> 

> Let’s start working on the new feature now!




---



**NO MORE HUNGRY SNAKE!! 🍕😋🐍**



You've been doing a fantastic job so far by adding obstacles for the snake. 

Now, it's time to add some delicious items to your game. 

You will introduce different types of food items that will have different effects on the snake! 🫡



Remember the OG snake game where the only food was a tiny dot that made the snake grow? 



![ ](/Full-Stack-Game-Development/images/e171ba6ee1dd7dfb.gif)



In the original snake game, variety wasn't on the menu. 

But why settle for just one type of food when we can have many delightful options? 

Let's make it more exciting by offering your snake some tasty snacks (and a few not-so-tasty snacks).🍕🧀🍔🍎🍊



![Image](/Full-Stack-Game-Development/images/1e429e2839c9e0e5.png)

***Food Items for Snake***



Each food item has a special effect that will change how you play the game.

You'll understand the effects of food as we go along, but for now, let's get your code ready to handle this variety.



How do you handle different types of things in programming? That's right—**Enums**! 🎉

But, But, But...

Do you have an idea of how the Food architecture would look like. Let's discuss.



## Understanding Food Architecture


---

![Image](/Full-Stack-Game-Development/images/fb4f832694cc436a.png)

***Food Architecture***



The `FoodService` manages different food items in the game, represented by `FoodItem` elements. 

These foods are characterized using enums like `FoodType` and `FoodSpawningStatus`. 

Understanding the need of `FoodSpawningStatus` is for later. 



First, have a look  `enum class FoodType` would look like this:

```cpp
enum class FoodType
    {
        APPLE,
        MANGO,
        ORANGE,
        PIZZA,
        BURGER,
        CHEESE,
        POISION,
        ALCOHOL,
    };
```



Now, do the things that are important right now.



> **TODO: **`**FoodType.h**`

> ✅ Create a new file `FoodType.h` inside the `Food` folder. Use `namespace Food`.

> ✅ Create `enum class FoodType`



Click here to see `FoodType.h````cpp
#pragma once

namespace Food
{
    enum class FoodType
    {
        APPLE,
        MANGO,
        ORANGE,
        PIZZA,
        BURGER,
        CHEESE,
        POISION,
        ALCOHOL,
    };
}
```



The above diagram shows a `FoodService` for food items. Time to work on it.



**See you in the next section.👋🏼**
