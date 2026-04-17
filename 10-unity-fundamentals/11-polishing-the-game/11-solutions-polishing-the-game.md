# **Solutions for Chapter 10**


**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.


<details>
<summary>Chapter 10 - Assignment - Adding Sounds</summary>
<p>

**Solution**

```csharp
public class SoundManager : MonoBehaviour
{
    private static SoundManager instance;

    public static SoundManager Instance { get { return instance; } }

    [SerializeField] private SoundType[] sounds;

    [SerializeField] private bool IsMute = false;
    [SerializeField] private float Volume = 1f;

    [SerializeField] private AudioSource soundEffect;
    [SerializeField] private AudioSource soundMusic;

    private void Awake()
    {
        if(instance == null)
        {
            instance = this;
            DontDestroyOnLoad(gameObject);
        }
        else
        {
            Destroy(gameObject);
        }
    }

    private void Start()
    {
        SetVolume(0.3f);
        PlayMusic(SoundManager.Sounds.Music);    
    }

    public void Mute(bool status)
    {
        IsMute = status;
    }

    public void SetVolume(float volume)
    {
        soundMusic.volume = volume;
    }

    public void PlayMusic(Sounds sound)
    {
        if (IsMute)
            return;

        AudioClip clip = getSoundClip(sound);
        if(clip != null)
        {
            soundMusic.clip = clip;
            soundMusic.Play();
        }
    }

    public void Play(Sounds sound)
    {
        if (IsMute)
            return;

        AudioClip clip = getSoundClip(sound);
        if(clip != null)
        {
            soundEffect.PlayOneShot(clip);
        }
    }

    private AudioClip getSoundClip(Sounds sound)
    {
        SoundType returnSound =  Array.Find(sounds, item => item.soundType == sound);
        return returnSound.soundClip;
    }

    [Serializable] 
    public class SoundType
    {
        public Sounds soundType;
        public AudioClip soundClip;
    }

    public enum Sounds
    {
        ButtonClick,
        PlayerMove,
    }
}
```

```csharp
public class PlayerController : MonoBehaviour
{
    public void MovementSound()
    {
        SoundManager.Instance.Play(SoundManager.Sounds.PlayerMove);
    }
}
```


</p>
</details>
<br>
<details>
<summary>Chapter 10 - Assignment - Finishing and adding creativity</summary>
<p>

**Solution**

```csharp
public class SoundManager : MonoBehaviour
{
    private static SoundManager instance;

    public static SoundManager Instance { get { return instance; } }

    [SerializeField] private SoundType[] sounds;

    [SerializeField] private bool IsMute = false;
    [SerializeField] private float Volume = 1f;

    [SerializeField] private AudioSource soundEffect;
    [SerializeField] private AudioSource soundMusic;

    private void Awake( )
    {
        if ( instance == null )
        {
            instance = this;
            DontDestroyOnLoad( gameObject );
        }
        else
        {
            Destroy( gameObject );
        }
    }

    private void Start( )
    {
        SetVolume( 0.3f );
        PlayMusic( SoundManager.Sounds.Music );
    }

    public void Mute( bool status )
    {
        IsMute = status;
    }

    public void SetVolume( float volume )
    {
        soundMusic.volume = volume;
    }

    public void PlayMusic( Sounds sound )
    {
        if ( IsMute )
            return;

        AudioClip clip = getSoundClip( sound );
        if ( clip != null )
        {
            soundMusic.clip = clip;
            soundMusic.Play( );
        }
    }

    public void Play( Sounds sound )
    {
        if ( IsMute )
            return;

        AudioClip clip = getSoundClip( sound );
        if ( clip != null )
        {
            soundEffect.PlayOneShot( clip );
        }
    }

    private AudioClip getSoundClip( Sounds sound )
    {
        SoundType returnSound = Array.Find( sounds, item => item.soundType == sound );
        return returnSound.soundClip;
    }

    [Serializable]
    public class SoundType
    {
        public Sounds soundType;
        public AudioClip soundClip;
    }

    public enum Sounds
    {
        ButtonClick,
        PlayerMove,
        Music,
        PlayerDeath,
        EnemyDeath,
        Jump,
        Pickup,
        EnemyCollision,
        LevelWin
    }
}
```

```csharp
public class PlayerController : MonoBehaviour
{
    public void MovementSound()
    {
        SoundManager.Instance.Play(SoundManager.Sounds.PlayerMove);
    }
		
	public void PickUpKey()
    {
        SoundManager.Instance.Play(SoundManager.Sounds.Pickup);        
    }

    public void KillPlayer()
    {
        SoundManager.Instance.Play(SoundManager.Sounds.PlayerDeath);        
    }  
		
    public void JumpSound()
    {
        SoundManager.Instance.Play(SoundManager.Sounds.Jump);
    }
}
```

```csharp
public class LevelOverController : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if(collision.gameObject.CompareTag("Player"))
        {
            SoundManager.Instance.Play(SoundManager.Sounds.LevelWin);            
        }
    }
}
```
</p>
</details>


