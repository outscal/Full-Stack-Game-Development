In the previous lesson, you have seen the entire code.

Did you feel something off in it?

Did you find it a little challenging to navigate through all the files?

Because there are 19 files in a single folder.



In the upcoming chapters,

there will be even more files.

With this approach, it will be quite difficult to manage such code.



I think you should create separate folders of separate functionalities.

But first of all, you need to separate source files and header files.



Let me give you a quick reminder about these kind of files.

*Header files* - These files consist the skeleton of the code. Functions and variables are declared here.

*Source files - *Functions and variables are defined here.



Now, it's time to organise your code.

I will be guiding you with one file,

then you will be able to do it on your own.



> **TODO:**
> ✅Create a folder with name 'src' to hold all the source files
> ✅Create a folder with name 'include' to hold all the header files
> ✅Move `Pokemon.hpp` file in include folder
> ✅Move `Pokemon.cpp` file in src folder
> ✅Change the #include statement for these files as their location has also been changed



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_05_2024__05_36_21.png)



Your file directory should look like the above image.

Once it is done, you need to change `#include` statements for these files.



> **💡PRO TIP:** "../" in path indicates moving to the previous directory



Pokemon.cpp```cpp
#pragma once
#include "../include/Pokemon.hpp"
..........
```





# Subfolders


---

Since you have created src and include folders.

Now it's time to create subfolders in these folders,

to organise the code according to functionalities.



> **NOTE:** Remember that all the subfolders will be created under ***src*** as well as ***include***



> **TODO:**
> ✅Create Battle, Character, Main, Pokemon, Utility subfolders in src and include
> ✅Create Player subfolder under Character folder
> ✅Shift BattleManager, BattleState, WildEncounterManager files in Battle folder
> ✅Shift ProfessorOak files in Character folder
> ✅Shift Player files in Player folder
> ✅Shift Game files in Main folder
> ✅Shift Grass, Pokemon, PokemonChoice and PokemonType file in Pokemon folder
> ✅Shift Utility files in Utility folder
> ✅main.cpp will be in the main directory



Your directory should look like

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_05_2024__09_28_06.png)





***include*** folder should look like

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_05_2024__06_17_45.png)





***src*** folder should look like

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_05_2024__09_31_29.png)





# File Path


---

Paths have been changed for all the files.

So, you need to change `#include` statements too



Let me show you an example of ***WildEncounterManager.cpp*** file



Earlier, it was having

```cpp
#include "WildEncounterManager.hpp"
........
```



But, now it should look like

```cpp
#include "../../include/Battle/WildEncounterManager.hpp"
..........
```



Similarly, do this for all the files.

**Note: **After organizing all your files and including all the header files, **you'll face a lot of errors!!**

But, why are you facing these errors when all the code is correct?!🤨

Try to think why these errors might occur. What might be the problem?🤔



## Circular Dependency Problem


---

Think about this:

If there are two files **A** and **B.**

And the header files of both A and B include each other.

Does this sound like a problem?🤔

Well, for the compiler, it does!

This problem is called **Circular Dependency Problem.**



> 📖🎮**GameDev Dictionary: **
> ***Circular Dependency Problem***: If `A.h` includes `B.h` and vice versa, the compiler doesn’t know which file to process first. Hence there are errors!



Now, how do we solve this?🤔

**Forward Declaration!**

You have implemented it before. 

You just need to use it again to solve the errors!
