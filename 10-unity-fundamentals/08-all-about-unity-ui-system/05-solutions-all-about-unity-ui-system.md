# **Solutions for Chapter 7**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

<details>
<summary>Chapter 7 - Mini Assignment 1 - Lobby Screen</summary>
<p>

**Solution**

```c#
public class LobbyManager : MonoBehaviour
{
    [SerializeField] private Button playButton;
    [SerializeField] private string levelName;

    private void Start( )
    {
        playButton.onClick.AddListener( LoadLevel );
    }

    private void LoadLevel( )
    {
        SceneManager.LoadScene( levelName );
        //you can put the buildIndex of the level instead of LevelName as well.
    }

    public void Quit( )
    {
        Application.Quit( );
    }
}
```

</p>
</details>

<details>
<summary>Chapter 7 - Assignment - Game Over UI with a Restart button on Player Death. </summary>
<p>

**Solution**

```c#
public class GameOverController : MonoBehaviour
{
  [SerializeField] private Button restartButton;
  [SerializeField] private Button quitButton;

  private void Awake( )
  {
      restartButton.onClick.AddListener( ReloadLevel );
      quitButton.onClick.AddListener( MainMenu );
  }

  public void PlayerDied( )
  {
      this.gameObject.SetActive( true );
  }

  private void ReloadLevel( )
  {
      int currentSceneIndex = SceneManager.GetActiveScene( ).buildIndex;
      SceneManager.LoadScene( currentSceneIndex );
  }

  public void MainMenu( )
  {
      SceneManager.LoadScene( 0 );
  }
}

```

In your **PlayerController, add the following code:** 

```c#
public class PlayerController : MonoBehaviour
{
    [SerializeField] private Animator playerAnimator;
    [SerializeField] private GameOverController gameOverController;
    public void KillPlayer( )
    {
        Debug.Log( "GAME OVER" );
        playerAnimator.SetTrigger( "DeathTrigger" );
        gameOverController.PlayerDied( );
        this.enabled = false;
    }
}
```

</p>
</details>
