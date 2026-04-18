## Detecting Collisions Using Code


---

Unity provides special functions that get called when collisions occur.




<iframe src="https://www.loom.com/embed/946bcbe1c08d418fa6cc710b7c3f826b" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





Here's a sample script to detect collision:



```csharp
private void OnCollisionEnter2D(Collision2D other)
{
    Debug.Log(gameObject.name + " Collided with: " + other.gameObject.name);
}

```



Suppose that you’ve written the above code in the `Player` script,

- `OnCollisionEnter2D` is called when the `Player` game object collides with any other game object.
- `Collision2D other`: This provides information about another game object that has collided with the `Player` game object.
- `other.gameObject.name`: This gives you the name of the other object involved in the interaction.

So, how can you use this function for implementing Player death🤔

`OnCollisionEnter2D` is called when Mr. Blocks collides with a game object.

If it's a game object with an “Obstacle” tag, you’ll implement `PlayerDied()`



```csharp
private void OnCollisionEnter2D(Collision2D other)
{
    if (other.gameObject.CompareTag("Obstacle"))
    {
        PlayerDied();
    }
}
```



> **TODO:** 
> ✅ Implement the `OnCollisionEnter2D` method to your Player script 
> ✅ Create an empty `private void PlayerDied()` method.



## What Happens on Death?


---

You could:

1. Restart the level
2. Show a game-over screen
3. Make Mr. Blocks disappear

For now, let's keep it simple: Mr. Blocks will vanish! 🎭



## Implementing Player Death


---

When Mr. Blocks dies, you'll make him disappear:

```csharp
private void PlayerDied()
{
    Destroy(gameObject);
}
```



> **TODO:** 
> ✅ Implement the `PlayerDied()` method in your `Player` script



## Putting It All Together


---

Here's the complete Player script with death functionality:

`**Player.cs**`

```csharp
using UnityEngine;
public class Player : MonoBehaviour
{
    private float horizontalInput, verticalInput;
    public float speed;
    
    private void Update() 
    { 
        GetInput(); 
        MovePlayer();
    }
    private void GetInput()
    {
        horizontalInput = Input.GetAxisRaw("Horizontal");
        verticalInput = Input.GetAxisRaw("Vertical");
    }
    private void MovePlayer()
    {
        Vector3 moveDirection = new Vector3(horizontalInput, verticalInput, 0);
        Vector3 moveDelta = moveDirection.normalized * speed * Time.deltaTime;
        transform.position += moveDelta;
    }
    
    private void OnCollisionEnter2D(Collision2D other)
    {
        if (other.gameObject.CompareTag("Obstacle"))
        {
            PlayerDied();
        }
    }
    private void PlayerDied()
    {
        Destroy(gameObject);
    }
}

```





> **TODO:** 
> ✅ Update your Player script with this complete code 
> ✅ Test the game - Mr. Blocks should disappear when hitting an obstacle



Congratulations!! You have successfully implemented collision!! 🥳

In the next lesson, you'll learn another way of detecting interactions in the game world, **Triggers**!
