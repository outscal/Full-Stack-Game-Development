Now that you are familiar with Unity, let's explore manipulating objects in our scene more deeply. This is where the real fun begins!



# Understanding Transform


---



At the heart of every object in Unity is the Transform component.

It's not just another component - it's the foundation of how objects exist in your game world.



> **📖 🎮 GAME DEV DICTIONARY** 
> ***Transform Component:*** "The Transform component in Unity controls an object's position, rotation, and scale. It's the key to how objects interact with one another in the game world."



The Transform component consists of three main properties:

1. **Position:** Where the object is located in the game world.
2. **Rotation:** Which way the object is facing.
3. **Scale:** How large or small the object is.



Every single object in your Unity scene has a Transform component.

It's not optional - it's a fundamental part of how Unity works.

You’ll learn more about components in further lessons, along with the module.



# Tools for Manipulating Objects


---



Unity provides several tools to customize objects in your scene.

Let's explore each of them:




[Watch video](https://www.loom.com/embed/27e62bac942e47a281f9eda078b750ea)





## Inspector: Direct Value Change


---

The most precise method is changing values directly in the Inspector:

1. Select an object in the Hierarchy or Scene view.
2. Find the `Transform` component in the Inspector.
3. Type in exact values for `Position`, `Rotation`, or `Scale`.



## Move Tool (`W`)


---

The Move tool allows you to drag objects around in the Scene view:

- Press W or click the Move tool icon in the toolbar.
- Colored arrows appear on the selected object.
- Drag these arrows to move the object along specific axes.



## Rotate Tool (`E`)


---

The Rotate tool lets you rotate objects around their axes:

- Press `E` on keyboard or click the Rotate tool icon.
- Colored circles appear around the object.
- Drag these circles to rotate the object.



## Scale Tool (`R`)


---

The Scale tool is used to resize objects:

- Press `R` on keyboard or click the Scale tool icon.
- Colored cubes appear on the object's corners.
- Drag these cubes to scale the object uniformly or along specific axes.



## Rect Tool (`T`)


---

The Rect tool combines move, rotate, and scale functions for 2D objects:

- Press `T` on keyboard or click the Rect tool icon.
- A bounding box appears around the object.
- Drag the edges to scale, the corners to rotate, or the center to move.



## Transform Tool (`Y`)


---

The Transform tool combines move, rotate, and scale functions for 3D objects:

- Press `Y` on keyboard or click the Transform tool icon.
- All manipulation handles appear at once.
- Choose which transformation to apply by selecting the appropriate handle.



> **💡 PRO TIP:** 
> You can quickly switch between tools using their keyboard shortcuts (`W,` `E`, `R`, `T`, `Y`). This can significantly speed up your level design process!



Now that you're familiar with these tools, let's put them to use in some interactive tasks!



> **TODO:** 
> ✅ Use the tools you've learned (Move, Rotate, Scale), play around with the objects.



> **💡 PRO TIP: Deleting Objects in Unity** To delete objects, you have two options:
> 
> 1. Right-click the object in the Hierarchy and select '`Delete`'
> 2. Select the object and press the '`Delete`' key on your keyboard



> **💡 PRO TIP: Duplicating Objects in Unity** To duplicate objects quickly, you have two options:
> 1. Copy (`Ctrl+C`) and paste (`Ctrl+V`) the object
> 2. Select the object and press `Ctrl+D` (`Cmd+D` on Mac)



Remember, these levels will become even more exciting once you've added functionalities to the obstacles and player.

In the next lesson, you'll learn about Game and Scene views.
