> You must have already cloned the project earlier, if not then please go back to the **Getting Started** chapter and clone the **GitHub** repo of this project.

> The branch you need to checkout: `**main**` branch**.**



Now before we begin, you need to set up SFML in your Sorting project!



Let's go through it together step by step:



## STEP 1: DOWNLOAD SFML


---

If you don't have SFML, install it from this link: [SFML](https://www.sfml-dev.org/download/sfml/2.6.1/)

Download the version that works with Visual Studio C++ **2022** 

![SFML Download Version](/Full-Stack-Game-Development/images/3fe1f73f7816fe77.png)






## STEP 2: ADDING INCLUDE AND LIB FOLDERS


---

- Open the directory where your solution file (.sln) for your project is present, as shown in the image below:

![](/Full-Stack-Game-Development/images/091fefcb5bd0641b.png)

**Project Folder**



- Here you can see there are 2 folders called 'assets' & 'sfml'. Open the sfml folder.
- You will see only a text file inside this folder. This is the location where you need to copy and paste your include and lib directories that you downloaded earlier. 



**BEFORE:**

![](/Full-Stack-Game-Development/images/89e4d709f9c9ef03.png)

**AFTER:**
![](/Full-Stack-Game-Development/images/744b9e93af502308.png)






- We have already linked the files by specifying the path to these folders. So you won't need to set up SFML in Visual Studios!



## STEP 1: ADDING BIN FOLDERS


---

- Open the solution file (`**.sln**`) in Visual Studios 2022 and **run it**. It will throw an error. Don't worry, its all part of the plan 😉
- After you try to run it, a folder called `**x64/Debug**` will be created inside which you can find your project's executable file (`**.exe**`). 
- Now all you need to do is **→** copy paste a few `**.dll**` files from **bin** folder into your Debug folder.
- Make sure you copy all the files highlighted below from the bin folder (they should have a -d suffix indicating debug mode).
- Let's copy them and paste it among our executable files as follows:
- ![](/Full-Stack-Game-Development/images/a19dbcd7c5f7ea10.png)


---



![Minesweeper is ready to be built](/Full-Stack-Game-Development/images/e234cd73b192fdab.png)

**The game is ready to be created!**
