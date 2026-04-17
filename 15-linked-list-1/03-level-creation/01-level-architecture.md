> **TODO:**
> ✅ Try the game in the `***Doubly-Linked-List-Solution***` branch



After trying the game, you can jump on creating The Snake!



> It’s time to create a new feature branch for the upcoming game features.

> 

> Make a new feature branch out of your `**main**` branch called → [ `**Feature-1-Level**` ]

> Let’s start working on the new feature now!



![Level Solution Output](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__07_09_56.png)

Level Solution Output SS



This is the output you'll create at the end of this chapter.

.

.

.

Does this feel boring to you?

A plane rectangle with a border...

How can something so basic be fun and enjoyable?

Let me share with you the case of *Gotham Knights*!



![Gotham Knights](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__07_17_14.png)

***Gotham Knights***

Gotham Knights was one of the most hyped games of 2022

After years a game was coming tailored around Batman. There were 4 playable characters, it had multiplayer co-op, had the
greatest villains from Batman's Rogue Gallery

And yet...

***It was disappointing!***



> The level design was called... ***"Repetitive, Boring, Empty, Lifeless"***



It was a AAA game with countless things to do, still, it didn't feel fun



A lot of big games go through this, and the reason is very clear

Scale is not everything



In the case of Snake, the level is not just a border, it is a portal, and it is part of the strategy!



The snake could pass through the walls and emerge from the opposite side!



Passing through the border can be used to reach to food quickly, it can be used to avoid collision

… it has its own purpose!



In this chapter, you'll get close to fulfilling this purpose by creating the background and the walls!



## Understanding level


---

![Snake Movement](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__07_36_38.gif)



If you notice, the snake moves in a discrete motion and not continuous.

That means it is moving like it is on a grid and moving from 1 block to another



This grid-like movement gives us 2 advantages:

1. It gives the *retro* vibe of the original Nokia Snake
2. Detecting collisions becomes super easy



Wait what?
Collision?

How do you detect collisions?

Don't worry we'll have an interesting discussion about collisions in games in the upcoming chapters!



## Level Architecture


---

![Level Architecture](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__08_41_06.png)

**Level Architecture**



This architecture should be self-explanatory to you by now!

It's the same old Model, View and Controller accompanied by a Service



> **TODO: LevelModel, LevelView, LevelController, LevelService**
> ✅ Create files for `LevelModel`, `LevelView`, `LevelController` and `LevelService`. Follow proper folder structure and use `namespace Level` 
> ✅ Create empty lifecycle methods inside `LevelService`, `LevelController` and `LevelView`



Apart from this, you have a `LevelData` and `enum LevelNumber` 

`LevelNumber` as the name suggests is an Enum that describes a level's number.  



`**enum LevelNumber**` 

```cpp
namespace Level
{
	enum class LevelNumber
	{
	    ONE,
	    TWO,
	};
}
```



You created `LevelData` in ***Array Jumper*** too

In this game, a level can have multiple elements like its `LevelNumber`, what food it can have, what obstacles it can have, etc.

All this data can be put inside a structure

For now, you have the `enum LevelNumber`, you can create a structure `struct LevelData` and create a variable for `LevelNumber` inside it.

…Later you will be expanding this struct by adding more data like obstacles and other stuff.



`**LevelData.h**`

```cpp
#pragma once
#include "Level/LevelService.h"

namespace Level
{
    struct LevelData
    {
        LevelData(LevelNumber ind)
        {
            level_index = ind;
        }

        LevelNumber level_index;
    };
}
```



> **TODO: **
> **LevelNumber **
> ✅ Create `LevelNumber.h` in `include/Level`  
> ✅ Create `enum class LevelNumber` inside it
> 
> **LevelData** 
> ✅ Create `LevelData.h` in `include/Level`



**See you in the next section!👋🏼**
