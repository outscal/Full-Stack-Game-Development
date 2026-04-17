# **Solutions for Chapter 3**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

<details>
<summary>Chapter 3 - Mini Assignment 1 - Movement</summary>
<p>

**Solution**

```c#
public class PlayerController : MonoBehaviour
{
    [SerializeField] private float moveSpeed;

    [SerializeField] private Rigidbody2D playerRigidbody;
    [SerializeField] private BoxCollider2D boxCollider;
    [SerializeField] private Animator playerAnimator;

    private void Update( )
    {
        float horizontal = Input.GetAxisRaw( "Horizontal" );

        HorizontalAnimation( horizontal );
        MoveCharacter( horizontal );
    }

    private void MoveCharacter( float horizontal )
    {
        // Horizontal character movement
        Vector3 newPosition = transform.position;
        newPosition.x += horizontal * moveSpeed * Time.deltaTime;
        transform.position = newPosition;
    }

    private void HorizontalAnimation( float horizontal )
    {
        //Horizontal animation
        playerAnimator.SetFloat( "Speed", Mathf.Abs( horizontal ) );

        //Flipping the player
        Vector2 scale = transform.localScale;
        if ( horizontal < 0 )
        {
            scale.x = -1f * Mathf.Abs( scale.x );
        }
        else if ( horizontal > 0 )
        {
            scale.x = Mathf.Abs( scale.x );
        }
        transform.localScale = scale;
    }
}

```

</P>
</details>
<br>
<details>
<summary>Chapter 3 - Assignment - Vertical input & Jump</summary>
<p>

**Solution**

```c#
public class PlayerController : MonoBehaviour
{
    [SerializeField] private Rigidbody2D rigidbodyPlayer;
    [SerializeField] private Animator playerAnimator;

    [SerializeField] private float jumpForce;

    private bool isGrounded = false;

    private void Update( )
    {
        float vertical = Input.GetAxisRaw( "Vertical" );
        MovePlayerVertically( vertical );
    }

    public void MovePlayerVertically( float vertical )
    {
        if ( vertical > 0 && isGrounded )
        {
            playerAnimator.SetTrigger( "Jump" );
            rigidbodyPlayer.AddForce( new Vector2( 0, jumpForce ), ForceMode2D.Impulse );
        }
    }

    private void OnCollisionStay2D( Collision2D other )
    {
        if ( other.transform.tag == "platform" )
        {
            isGrounded = true;
        }
    }

    private void OnCollisionExit2D( Collision2D other )
    {
        if ( other.transform.tag == "platform" )
        {
            isGrounded = false;
        }
    }
}
		
```

</P>
</details>
