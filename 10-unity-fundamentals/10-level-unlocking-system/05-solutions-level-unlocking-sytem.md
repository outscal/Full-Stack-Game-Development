# **Solution for Chapter 9**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

<details>
<summary>Chapter 9 - Mini Assignment 1 - Lock Unlock Levels</summary><br>

**Solution**

LevelStatus.cs

```csharp
public enum LevelStatus
{
    Locked,
    Unlocked,
    Completed
}
```

LevelManager.cs

```csharp
public class LevelManager : MonoBehaviour
{
    private static LevelManager instance;
    public static LevelManager Instance{ get{ return instance; } }

    private string Level1 = "Level1";

    private void Awake()
    {
        if(instance==null)
        {
            instance = this;
            DontDestroyOnLoad(instance);
        } else
        {
            Destroy(gameObject);
        }
    }

    private void Start()
    {
        if(GetLevelStatus(Level1) == LevelStatus.Locked)
        {
            SetLevelStatus(Level1, LevelStatus.Unlocked);
        }
    }

    public LevelStatus GetLevelStatus(string levelName)
    {
        LevelStatus levelStatus = (LevelStatus) PlayerPrefs.GetInt(levelName);
        return levelStatus;
    }

    public void SetLevelStatus(string levelName, LevelStatus levelStatus)
    {
        PlayerPrefs.SetInt(levelName, (int) levelStatus);
    }

    public void SetCurrentLevelComplete()
    {
        SetLevelStatus(SceneManager.GetActiveScene().name, LevelStatus.Completed);

        string nextSceneName = NameFromIndex(SceneManager.GetActiveScene().buildIndex + 1);
        SetLevelStatus(nextSceneName, LevelStatus.Unlocked);
    }

    private string NameFromIndex(int BuildIndex)
    {
        string path = SceneUtility.GetScenePathByBuildIndex(BuildIndex);
        int slash = path.LastIndexOf('/');
        string name = path.Substring(slash + 1);
        int dot = name.LastIndexOf('.');
        return name.Substring(0, dot);
    }
}
```

LevelLoader.cs

```csharp
[RequireComponent( typeof( Button ) )]
public class LevelLoader : MonoBehaviour
{
    [SerializeField] private Button button;
    [SerializeField] public string LevelName;

    private void Awake( )
    {
        button.onClick.AddListener( TryLoadLevel );
    }

    private void TryLoadLevel( )
    {
        LevelStatus levelStatus = LevelManager.Instance.GetLevelStatus( LevelName );

        switch ( levelStatus )
        {
            case LevelStatus.Locked:
                Debug.Log( "This Level is Locked" );
                break;
            case LevelStatus.Unlocked:
                SceneManager.LoadScene( LevelName );
                break;
            case LevelStatus.Completed:
                SceneManager.LoadScene( LevelName );
                break;
        }
    }
}
```

</details>

<details>
<summary>Chapter 9 - Assignment - Level Unlocking system with 5 Unique levels</summary><br>

**Solution**

LevelComplete.cs

```csharp
public class LevelComplete : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D other)
    {
        if(other.gameObject.GetComponent<PlayerController>() != null)
        {
            LevelManager.Instance.SetCurrentLevelComplete();
            SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1);
        }
    }
}
```

</details>