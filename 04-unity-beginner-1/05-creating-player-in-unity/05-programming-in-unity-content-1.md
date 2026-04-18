In Unity, we use **scripts** to add custom behaviours to a **Game Object**.

But how do these scripts know how to interact with a Game Object?🤔

That's where `**MonoBehaviour**` comes in.



# What is MonoBehaviour?


---

> 📖🎮**UNITY DICTIONARY**: `MonoBehaviour`
> 
> - It is a special class that allows interaction with the Unity engine
> - It enables your scripts to be attached to Game Objects



Now that you know what `MonoBehaviour` is, let's see how it's different from regular C# classes.



## Plain C# Classes vs. MonoBehaviour Scripts


---

Let's compare these two types of scripts:

1. Plain C# Classes:
2. - Don't work directly with Unity's Game Objects or interact with the Unity Editor
3. `MonoBehaviour` Scripts:
4. - Can be attached to Game Objects
  - `MonoBehaviour` scripts are special because they give us access to Unity's event functions.

What are Event Functions?🤔

Let's understand two of the most important ones.



## Event Functions: Start() and Update()


---

`MonoBehaviour` gives us access to special functions called event functions.

Two of the important ones are `Start()` and `Update()`



**What is Start()?**

- Execute once when the **script** **and** the **game object** become active in the scene.

Here’s a demonstration of the `Start()` method:



```csharp
private void Start()
{
    Debug.Log("I am Mr. Blocks!");
}
```



![Start](/Full-Stack-Game-Development/images/80e8b113f1182670.png)

**Start Method**



**What is Update()?**

- Runs continuously, once per frame once the **game object** **and** the **script** are active.



> 📖🎮**UNITY DICTIONARY**: 
> **Frame: **Frame*** ***is like a single picture in a flip book. Your game shows many frames per second to create smooth motion. Most games aim for 60 frames per second (FPS) or higher. Remember, when `Update()` runs "every frame," it's happening 60 times each second(for 60 FPS)!



You'll learn more about frames in more detail in the ***Obstacle Behaviour*** chapter!



Here’s a demonstration of the `Update()` method:



```csharp
private void Update()
{
    Debug.Log("I am Mr. Blocks!");
}
```





![ ](/Full-Stack-Game-Development/images/f953eae3a6f553f7.gif)

**Update Method**



These were only two of the event functions, there are more methods that you’ll explore along the module.

In the next lesson, you’ll learn to take input from a Keyboard!

See you there 👋🏼
