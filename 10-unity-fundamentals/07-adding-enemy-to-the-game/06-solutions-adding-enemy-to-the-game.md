# **Solutions for Chapter 6**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

<details>
<summary>Chapter 6 - Mini Assignment 1 - Add enemy</summary>
<p>

**Solution**

```c#
public class EnemyController : MonoBehaviour
{
    
    [SerializeField] private Animator enemyAnimator;

    [SerializeField] private float moveSpeed;
    [SerializeField] private GameObject groundDetector;
    [SerializeField] private float rayDistance;

    private int directionChanger = 1;

    void Update( )
    {
        patrolEnemy( );
    }

    private void patrolEnemy( )
    {
        enemyAnimator.SetBool( "IsPatrol", true );

        transform.Translate( directionChanger * Vector2.right * moveSpeed * Time.deltaTime );

        RaycastHit2D hit = Physics2D.Raycast( groundDetector.transform.position, Vector2.down, rayDistance );

        if ( !hit )
        {
            Vector3 scaleVector = transform.localScale;
            scaleVector.x *= -1;
            transform.localScale = scaleVector;
            directionChanger *= -1;
        }
    }
}
```
</p>
</details>

<details>
<summary>Chapter 6 - Mini Assignment 2 - Reload Level</summary>
<p>

EnemyController.cs

```c#
public class EnemyController : MonoBehaviour
{
    private void OnCollisionEnter2D(Collision2D collision)
    {
        if(collision.transform.GetComponent<PlayerController>() != null)
        {
            collision.transform.GetComponent<PlayerController>().DecreaseHealth();
        }
    }   
}
```

PlayerController.cs

```c#
    [SerializeField] private Rigidbody2D playerRigidbody;
    [SerializeField] private Animator playerAnimator;
    [SerializeField] private SpriteRenderer[] hearts;

    [SerializeField] private GameObject deathUIPanel;

    private int health;
    private Camera mainCamera;

    private bool isDead = false;
    private void Start( )
    {
        //Initializing health with the number of hearts
        health = hearts.Length;

        mainCamera = Camera.main;
    }
    public void DecreaseHealth( )
    {
        health--;

        HandleHealthUI( );
        if ( health <= 0 )
        {
            PlayDeathAnimation( );
            PlayerDeath( );
        }
    }

    public void PlayerDeath( )
    {
        isDead = true;
        mainCamera.transform.parent = null;
        deathUIPanel.gameObject.SetActive( true );
        playerRigidbody.constraints = RigidbodyConstraints2D.FreezePosition;
        ReloadLevel( );
    }

    public void PlayDeathAnimation( )
    {
        playerAnimator.SetTrigger( "Die" );
    }

    private void ReloadLevel( )
    {
        SceneManager.LoadScene( SceneManager.GetActiveScene( ).buildIndex );
    }

    public void HandleHealthUI( )
    {
        for (int i = 0; i < hearts.Length; i++)
        {
            hearts[i].color = ( i < health) ? Color.red : Color.black;
        }
    }
```
</p>
</details>
