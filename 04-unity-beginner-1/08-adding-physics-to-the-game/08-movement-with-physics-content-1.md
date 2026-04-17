Remember how Mr. Blocks has been moving around?

Currently, you're moving Mr. Blocks like this:



```csharp
private void Update()
{
    GetInput();
    MovePlayer();
}

private void MovePlayer()
{
    Vector3 moveDirection = new Vector3(horizontalInput, verticalInput, 0);
    Vector3 moveDelta = moveDirection.normalized * speed * Time.deltaTime;
    transform.position += moveDelta;
}
```



This works, but you can make it better with physics!



## Why Use Physics for Movement?


---

Let's think about how physics could help our movement:

1. **Simpler Code**: Instead of calculating position changes, you can just apply forces or set velocities and let the physics engine do the rest.
2. **Consistent Behaviour**: Since the Player game object is a `Rigidbody`, it is affected by physics. If you move the player by changing its position, this could result in inconsistent behavior when the `Player` game object interacts with other game objects.
3. **Automatic Interactions**: Physics handles object interactions for us. If we add moving platforms or pushable objects later, they'll interact with Mr. Blocks naturally.

These benefits make our game feel more natural and save us from writing complex code for object interactions.

It’s time to implement `Rigidbody`!



## Accessing Components


---

You need to access the `Rigidbody2D` component from the `Player` script.



> **Pro Tip**💡
> **GetComponent:** `GetComponent<T>()` is a method in Unity that allows you to access other components attached to the same `GameObject` as the script.



Here's how it works:



```csharp
private Rigidbody2D rb;

void Start()
{
    rb = GetComponent<Rigidbody2D>();
}
```



This code finds the Rigidbody2D component on the same `GameObject` and stores a reference to it in the `rb` variable.



> **TODO:** 
> ✅ Initialize rigidbody using `GetCompenent` in `Start()` method.



## Physics-Based Movement


---

Instead of changing position directly, you can use Rigidbody2D's velocity property:



> 📖 🎮** GAME DEV DICTIONARY** 
> ***Velocity***: "The speed and direction of an object's movement. In 2D games, it's represented as a Vector2 (x and y components).”



```csharp
private void MovePlayer()
{
    Vector2 newVelocity = new Vector2(horizontalInput, verticalInput).normalized * speed;
    rb.velocity = newVelocity;
}
```



This sets the velocity of Mr. Blocks, letting the physics engine handle his movement.



> **TODO:** 
> ✅ Update your `MovePlayer` method to use Rigidbody2D



## Introducing FixedUpdate


---

Now that you're using Rigidbody2D, you can move the movement code to `FixedUpdate`:



> **Pro Tip**💡
> `FixedUpdate` : An Event function called at a fixed time interval, independent of frame rate.
> It's perfect for physics calculations because it keeps them consistent, even if your game's frame rate varies.



```csharp
private void Update() => GetInput();
private void FixedUpdate() => MovePlayer();
```



> **TODO:** 
> ✅ Update your `Player` script to use `FixedUpdate` for movement



## Putting It All Together


---

Here's our complete updated Player script:



Complete Code

`**Player.cs**`

```csharp
public class Player : MonoBehaviour
{
    private Rigidbody2D rb;
    public float speed = 5f;
    private float horizontalInput, verticalInput;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    private void Update() => GetInput();

    private void FixedUpdate() => MovePlayer();

    private void GetInput()
    {
        horizontalInput = Input.GetAxisRaw("Horizontal");
        verticalInput = Input.GetAxisRaw("Vertical");
    }

    private void MovePlayer()
    {
        Vector2 newVelocity = new Vector2(horizontalInput, verticalInput).normalized * speed;
        rb.velocity = newVelocity;
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
    
    private void OnTriggerEnter2D(Collider2D other)
		{
		    if (other.gameObject.CompareTag("Finish"))
		    {
		        LevelComplete();
		    }
		}
	private void LevelComplete()
	{
	    Debug.Log("Level Complete!");
	}
}


```





> **TODO:** 
> ✅ Update your Player script with this complete code 
> ✅ Adjust the speed variable in the Unity Inspector to find the right movement speed 
> ✅ Test the game - Mr. Blocks should now move smoothly and interact naturally with obstacles





Great job! Mr. Blocks is now moving with the power of physics.

In the next chapter, you’ll complete the first level and create more levels!
