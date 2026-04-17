# **Solution for Chapter 4**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

**Chapter 4 - Assignment- Death After Falling From Platform**

```c#
public class DeathCollider : MonoBehaviour
{
    private void OnTriggerEnter2D( Collider2D collision )
    {
        if ( collision.gameObject.GetComponent<PlayerController>( ) != null )
        {
            //Reloading the Current Scene.
            int currentSceneIndex = SceneManager.GetActiveScene( ).buildIndex;
            SceneManager.LoadScene( currentSceneIndex );
        }
    }
}
```