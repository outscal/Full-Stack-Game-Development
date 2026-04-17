# Introduction to Input


---

Let's start with a simple way to detect when a player presses a key using `Input.GetKey()`



> 📖 🎮 **UNITY DICTIONARY **
> `**Input.GetKey()**`: A method that detects if a specific key is being held down.



Let’s see how you can detect input using `Input.GetKey()` method.



## Detecting Key Presses


---

Let’s start with the **W** key.

Here's how you can check for W key press:

```csharp
void Update()
{
    if (Input.GetKey("w"))
    {
        Debug.Log("W key is held down");
    }
}
```



> **TODO:**
> ✅Add the code to detect input in the `Player.cs` script.
> ✅After this lesson, remove this code



Now, when you run this code and press the 'W' key, you'll see a message in the Unity Console.

But, there’s a problem with this code. Can you think of the problem?🤔



***Hint***Instead of **w**, try giving **W** as the parameter and see the output in the console.



What happened?

Got an error? W is unknown?!🤨

That’s one of the problems: in string references like “w,” even the slightest mistake will result in an error!

One of the problems? What are the other problems?🤔

Well, there’s one more problem, which is even bigger than the first one!

String references increase the runtime of the code, there’s a better way than using string references!



## Using KeyCode for Better Performance


---



> 📖 🎮 **UNITY DICTIONARY**
>  `KeyCode`: A predefined reference in Unity for identifying specific keyboard keys (like W) in scripts. Using `KeyCode` is generally preferred as it's more performant than string comparisons.



Unity provides a more efficient way using `KeyCode`:

```csharp
void Update()
{
    if (Input.GetKey(KeyCode.W))
    {
        Debug.Log("W key is held down");
    }
}

```

Is this the best way of getting input?

Well, in the case of Mr. Blocks, not really.

Why?🤔

You’ll need to create multiple if blocks for different keys.

Let’s say you want input for W, A, S, D, and the arrow keys. You’d need 4 ****if blocks.

Unity provides an input system for the same purpose, using which you can get the input using, 2 LINES. Yes, just 2 lines!

In the next lesson, you’ll learn Unity’s Input system!
