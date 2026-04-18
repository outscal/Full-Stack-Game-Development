# What's a Script?


---

Scripts add custom behaviour to Game Objects.

You'll write these scripts in C#, Unity's primary programming language.

You’ll understand scripts in more detail in the next lesson.

Now, let's create our first script for Mr. Blocks!



# Creating Your First Script


---

To create a script, you must create a new C# file in our Unity project.

You can name it `Player` and put it in a separate folder `Assets/Scripts` to keep things organized.




<iframe src="https://www.loom.com/embed/1e2b365665ee49b7b6925d33d72a8d88" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **TODO:** 
> ✅ In the `Project` window Inside `Assets/Scripts` folder, right-click and select `Create > C# Script` 
> ✅ Name it `Player` 
> ✅ Double-click on the script to open in Visual Studio.



Great job! You've created your first script.

This is what your new script will look like:

```csharp

using UnityEngine;

public class Player : MonoBehaviour
{
    void Start()
    {

    }

    void Update()
    {

    }
}

```

**Note:** Don’t worry about the magic words like `Start`, `Update` and `MonoBehaviour`, you’ll learn about them in the next lesson.



# Attaching the Script to Mr. Blocks


---

For Mr. Blocks to use the script, you need to attach it to the `Player` Game Object in Unity.




<iframe src="https://www.loom.com/embed/87d251da1add44768584b7e75486d512" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





> **PROTIP**💡 
> You can also Drag the `Player` script from the `Project` window and drop it on the `Player` game object.



> **TODO:** 
> ✅ Select `Player` Game Object in the `Hierarchy` 
> ✅ In the `Inspector`, click `Add Component` 
> ✅ Search for `Player` and select it



You have created the Player Character’s Script, But it doesn’t do anything!!

In the next lesson, you’ll understand how scripts work in Unity.

**See you there!👋🏻**
