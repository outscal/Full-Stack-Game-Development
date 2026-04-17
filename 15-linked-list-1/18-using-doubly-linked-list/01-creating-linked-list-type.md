You have 2 types of Linked Lists now, 

and you have to use both the Linked Lists



Now, how will your code handle these 2 LLs, you need a way to identify each LL, right?

And you are smart enough to guess what will be the next step!



Of course, you have to create an `Enum` for LL Type: `enum class LinkedListType` 

But I have a proposal to make!



Level Number and Linked List Types are 2 important factors for playing a level. 

So you should just rename `LevelNumber.h` to `LevelConfig.h` 



I know I know, it can be annoying, but good architecture over anything!



> **TODO**
> ✅ Replace `LevelNumber.h` with below given `LevelConfig.h`



`**LevelConfig.h**` 

```cpp
#pragma once

namespace Level
{
    enum class LevelNumber
    {
        ONE,
        TWO,
    };

    enum class LinkedListType
    {
        SINGLE_LINKED_LIST,
        DOUBLE_LINKED_LIST,
    };
}
```
