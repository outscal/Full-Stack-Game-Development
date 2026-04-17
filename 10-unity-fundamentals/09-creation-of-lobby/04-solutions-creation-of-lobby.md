# **Solution for Chapter 8**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

**Chapter 8 - Assignment -Lobby screen**

**Solution**

```csharp
public class LobbyController : MonoBehaviour
{
    [SerializeField] private GameObject LevelSelection;
    [SerializeField] private Button buttonPlay;
    [SerializeField] private Button buttonQuit;
    
    private void Awake( )
    {
        buttonPlay.onClick.AddListener( PlayGame );
        buttonQuit.onClick.AddListener( QuitGame );
    }

    private void QuitGame( )
    {
        Application.Quit( );
    }

    private void PlayGame( )
    {
        //Level Selection is a parent gameobject acting as a pop-up menu for selecting levels
        //Buttons for the levels are child of Level Selection.
        LevelSelection.SetActive( true );
    }
}
```