# **Solution for Chapter 5**

## Chapter 5 - Mini Assignment - Collectable

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

**[Task] - Add item i.e. here we added a key to be picked up by the player to increase the score**
1. Add a key as a game object.
2. Make it collectable.
3. Add a script and when we detect a collision between key and player so destroy the key when the player touches it.
4. Increment a score after collecting the key.

**[Submission]**

- Push on the Branch you previously created as Feature5-Collectable and put your code there make a pull request to your own repository, not the Outscal one
- Share the pull request link here as an answer to this question and turn it in.

Solution

```c#
public class KeyController : MonoBehaviour
{
    [SerializeField] private PlayerController playerController;

    //OnTrigger Method to Detect the collision between Key and Player 

    private void OnTriggerEnter2D( Collider2D collision )
    {
        if ( collision.gameObject.GetComponent<PlayerController>( ) != null )
        {
            playerController.GetKey( );     
            //playerController needs to have a public method GetKey()

            Destroy( gameObject );
            //Destroy keyword will destroy the key gameobject after collision 
        }
    }
}
```
```c#
public class PlayerController : MonoBehaviour
{
    [SerializeField] private ScoreController scoreController;
    public void GetKey( )
    {
        scoreController.IncreaseScore( 10 );
    }
}
```
```c#
public class ScoreController : MonoBehaviour
{
    [SerializeField] private TextMeshProUGUI scoreText;

    private int score = 0;

    private void Start( )
    {
        RefreshUI( );
    }

    public void IncreaseScore( int increment )
    {
        score += increment;
        RefreshUI( );
    }

    private void RefreshUI( )
    {
        scoreText.text = "Score: " + score;
    }
}
```