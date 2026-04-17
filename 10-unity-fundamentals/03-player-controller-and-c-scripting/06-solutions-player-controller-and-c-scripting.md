# **Solutions for Chapter 1**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

<details>
<summary>Chapter 2 - Mini Assignment 2 - Scripting Animation & Flipping</summary>
<p>

**Solution**

```c#
public class PlayerController : MonoBehaviour
{
    [SerializeField] private Animator playerAnimator; 
    //Take a reference from inspector.
    //Using GetComponent() is not recommended.

    public void Update( )
    {
        float speed = Input.GetAxisRaw( "Horizontal" );

        playerAnimator.SetFloat( "Speed", Mathf.Abs( speed ) );


        //Flipping the player

        Vector3 scale = transform.localScale;
        if ( speed < 0 )
        {
            scale.x = -1f * Mathf.Abs( scale.x );
        }
        else if ( speed > 0 )
        {
            scale.x = Mathf.Abs( scale.x );
        }
        transform.localScale = scale;
    }
}
```

</p>
</details>
<br>
<details>
<summary>Chapter 2 - Assignment 1 - Crouch</summary>
<p>

**Solution**

This is your code without collider resizing:

```c#
public class PlayerController : MonoBehaviour
{
    [SerializeField] private Animator playerAnimator;

    public void Update( )
    {
        float VerticalInput = Input.GetAxis( "Vertical" );

        PlayJumpAnimation( VerticalInput );

        if ( Input.GetKey( KeyCode.LeftControl ) )
        {
            Crouch( true );
        }
        else
        {
            Crouch( false );
        }
    }

    public void Crouch( bool crouch )
    {
        //First, get the offset and size values from your collider while you are standing 
        //and note them down, this is the collider you want when your player is not in 
        //crouch mode.
        //Now, play the crouch animation and resize your collider, note down the values,
        //these are your values when your player is in crouch position
        //We will use these values in the next step.
        playerAnimator.SetBool( "Crouch", crouch );
    }


    public void PlayJumpAnimation( float vertical )
    {
        if ( vertical > 0 )
        {
            playerAnimator.SetTrigger( "Jump" );
        }
    }
}
   
```
Now add the offset and size of the collider you got from above. **These values may vary for you, so don’t copy the values, instead find your own perfect collider size and use those values.**

**Note: The program does not write the complete code, just the parts that are edited.**

```c#
public class PlayerController : MonoBehaviour
{
    [SerializeField] private Animator playerAnimator;
    [SerializeField] private BoxCollider2D boxCol;

    //Collider Variables
    private Vector2 boxColInitSize;
    private Vector2 boxColInitOffset;

    private void Start( )
    {
        //Fetching initial collider properties
        boxColInitSize = boxCol.size;
        boxColInitOffset = boxCol.offset;
    }

    public void Crouch( bool crouch )
    {
        if ( crouch == true )
        {
            float offX = -0.0978f;     //Offset X
            float offY = 0.5947f;      //Offset Y

            float sizeX = 0.6988f;     //Size X
            float sizeY = 1.3398f;     //Size Y

            boxCol.size = new Vector2( sizeX, sizeY );   //Setting the size of collider
            boxCol.offset = new Vector2( offX, offY );   //Setting the offset of collider
        }

        else
        {
            //Reset collider to initial values
            boxCol.size = boxColInitSize;
            boxCol.offset = boxColInitOffset;
        }

        //Play Crouch animation
        playerAnimator.SetBool( "Crouch", crouch );
    }
}
```

</p>
</details>

