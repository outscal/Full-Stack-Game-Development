# **What is a WebGL build?**


---



WebGL builds are [a collection of files](https://docs.unity3d.com/Manual/webgl-building.html) which contain your real-time experience. You can play them in your browser locally, or publish them on our platform letting others to play as well.



After making significant changes in your project, you will be asked to make a playable WebGL build of your game which you will be able to share with the world!



> **Please Note:**
> 
> **WebGL builds only work for Unity versions after 2020.**



## Step 1: Installing WebGL Build Support


---



Check if the WebGL Build Support module has been added to your Unity installation



1. Open the Unity Hub.
2. Select the **Projects** tab, and identify the version of Unity you are using in the project you want to build.

![](//outscal.github.io/Full-Stack-Game-Development/images/8a52fd3b3bad1a00.png)



1. Select the **Installs** tab and search for the version in the list available. If the **WebGL Build Support** module is installed, a WebGL icon will be present at the bottom of the version tile.

![](//outscal.github.io/Full-Stack-Game-Development/images/b8c7600983105a1b.png)



1. If the WebGL icon is not present, add the **WebGL Build Support** module to your version of Unity.
2. Select “**Add modules**” option in Settings menu for the Unity version you wish to use.

![](//outscal.github.io/Full-Stack-Game-Development/images/e090367647805820.png)



1. Choose “**WebGL Build Support**” module and select “**Install Button**”.
2. ![](//outscal.github.io/Full-Stack-Game-Development/images/2bb2d59957a369d8.png)

## Step 2: Creating a WebGL Build


---



1. Open the project in the Unity Editor.
2. In the Unity Editor top menu, go to **File** > **Build Settings**.
3. In the Build Settings window, find the **Scenes in Build** section. This is where you can control which Scenes are included in your build.
4. ![](//outscal.github.io/Full-Stack-Game-Development/images/40a3b1d56a0d2d17.png)
5. Find the **Platform** selection and select WebGL from the list available. This will change the settings and configuration options available to the right of the list. 
6. A **Switch Platform** button will be available at the bottom right of the window. If this is present, select it to change your build Platform to WebGL.
7. ![](//outscal.github.io/Full-Stack-Game-Development/images/7da858549d0dbf67.png)
8. Now you’re ready to build your real-time experience! You can: - Select **Build** to create the build. - Select **Build And Run** to create the build and immediately run it in your default browser.



# **About your build files**


---



Your WebGL build consists of an index.html file, as well as other folders, files and assets that the game will need to run. The index.html file is a loader file. It functions as a launcher for your game. However, without the other files in their correct locations it won’t work properly, as it is dependent on them to run your build.

If you need to **Upload** or move the build files to a different location — we recommend zipping the files to do this.
