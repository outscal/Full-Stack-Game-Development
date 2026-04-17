> You must have already cloned the project earlier, if not then please go back to the **Getting Started** chapter and clone the **GitHub** repo of this project.

> The branch you need to checkout: `**main**` branch**.**



Now before we begin, you need to set up SFML in your Searching Sticks project!



Let's go through it together step by step:



## STEP 1: DOWNLOAD SFML


---

If you don't have SFML, install it from this link: [SFML](https://www.sfml-dev.org/download/sfml/2.6.1/)

Download the version that works with Visual Studio C++ **2022** 

![SFML Download Version](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/04_05_2024__07_46_10.png)






## STEP 2: ADDING INCLUDE AND LIB FOLDERS


---

- Open the directory where your solution file (.sln) for your project is present, as shown in the image below:

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/02_20_2024__15_55_05.png)

**Project Folder**



- Here you can see there are 2 folders called 'assets' & 'sfml'. Open the sfml folder.
- You will see only a text file inside this folder. This is the location where you need to copy and paste your include and lib directories that you downloaded earlier. 



**BEFORE:**

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/12_19_2023__10_18_59.png)

**AFTER:**
![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/12_19_2023__10_49_52.png)






- We have already linked the files by specifying the path to these folders. So you won't need to set up SFML in Visual Studios!



## STEP 1: ADDING BIN FOLDERS


---

- Open the solution file (`**.sln**`) in Visual Studios 2022 and **run it**. It will throw an error. Don't worry, its all part of the plan 😉
- After you try to run it, a folder called `**x64/Debug**` will be created inside which you can find your project's executable file (`**.exe**`). 
- Now all you need to do is **→** copy paste a few `**.dll**` files from **bin** folder into your Debug folder.
- Make sure you copy all the files highlighted below from the bin folder (they should have a -d suffix indicating debug mode).
- Let's copy them and paste it among our executable files as follows:
- ![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/02_20_2024__16_05_09.png)


---



![Minesweeper is ready to be built](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/04_04_2024__07_36_21.png)

**The game is ready to be created!**
