Alright, it’s time to add the sound to Mr. Blocks🎵 You’ll need a separate sound manager to handle the sound.



## What's a SoundManager?


---



It's responsible for:

1. Playing background music
2. Handling all those sound effects
3. Making sure sounds work smoothly between different game scenes



> 💡 **PRO TIP**: 
> Using a SoundManager keeps your code clean and makes managing sounds super easy!



## Setting Up SoundManager in Unity


---



Let's create the SoundManager:



> **TODO:**
> ✅ Create a new GameObject, name it "SoundManager."



You also need AudioSources to play the sound.



> 📖 🎮 **UNITY DICTIONARY**
> ***Audio Source***: "A Unity component that plays audio clips in a scene, controlling properties like volume, pitch, looping, and 3D spatial sound behavior."



> **TODO:**
> ✅ Add two `AudioSources` as child objects: "Bgm Source" and "Sound FX Source."
> ✅ On "Bgm Source," check the "Loop" box in the Inspector.



Now, you need a Sound Manager script to play the sound!



## Planning SoundManager


---



Before writing any code, let's see what the Sound Manager needs:

1. An Audio Source to play background music.
2. Another Audio Source to play different sound effects.
3. A way to persist between scenes.



Let's tackle these one by one!



## Playing Background Music


---



First, you need a way to play the background music. 

Here's what you'll need:

1. An `AudioSource` for our background music.
2. A method to start playing the music.



Let's implement this:

```csharp
using UnityEngine;

public class SoundManager : MonoBehaviour
{
//Audio source
    public AudioSource backgroundAudioSource;
}
```



You have added an AudioSource, but how to play the background music using this Audio Source?🤔

Firstly, you need to check if the Audio Source and the clip are null and if the BGM is not already playing.
If these conditions are true, then call the `Play()` method of the `backgroundAudioSource` :



```csharp
//Playing the background music
    public void PlayBackgroundMusic()
    {
        if (backgroundAudioSource != null && backgroundAudioSource.clip != null && !backgroundAudioSource.isPlaying)
        {
            backgroundAudioSource.Play();
        }
    }
```



> **TODO** 
> ✅ Implement the logic for playing background music



Now that you've sorted the background music let's add sound effects!



## Adding Sound Effects


---



Let's focus on the "Level Complete" sound for the first sound effect.
It'll play whenever Mr. Blocks finishes a level.

Here's what you'll need:

- Another AudioSource for sound effects.

**Note**: You can use a single Audio Source for all the sound effects, and its clip can be changed from the code.

```csharp
public AudioSource soundFXAudioSource;
```



- An audio clip for the complete sound level.

```csharp
public AudioClip levelCompleteAudio;
```



- A method to play the level complete sound.



> 📖 🎮 **UNITY DICTIONARY**
> ***PlayOneShot***: "A method used to play an audio clip once without interrupting any audio already playing on the AudioSource. It is useful for sound effects, like button clicks or explosions."



```csharp
public void PlayLevelCompleteAudio()
{
    if (soundFXAudioSource != null && levelCompleteAudio != null)
    {
        soundFXAudioSource.PlayOneShot(levelCompleteAudio);
    }
}
```



> **TODO**: 
> ✅ Implement the logic for playing Level Complete audio
> ✅ Add the logic to play the **Game Over** and **Button Click** sound effects



Click here to see the solution.

`**SoundManager.cs**`

```csharp
public AudioClip gameOverAudio;
public AudioClip buttonClick;

public void PlayGameOverAudio()
{
    if (soundFXAudioSource != null && gameOverAudio != null)
    {
        soundFXAudioSource.PlayOneShot(gameOverAudio);
    }
}

public void PlayButtonClickAudio()
{
    if (soundFXAudioSource != null && buttonClick != null)
    {
        soundFXAudioSource.PlayOneShot(buttonClick);
    }
}

```







You have successfully added the logic to play the sound effects!!🥳

Next?🤔

A way for Sound Manager to persist between scenes.

Why?🤔

When a new scene is loaded, all current scene objects get destroyed. 

Therefore, the Sound Manager also gets destroyed when the first level loads. 

To avoid creating a new Sound Manager for each scene, 
you can persist the same manager in all the scenes."



## Making SoundManager Persist


---



You can do this using `DontDestryoOnLoad` method in the `Awake` method.



> 📖 🎮 **UNITY DICTIONARY **
> **DontDestroyOnLoad**:  "Preserves an Object during scene loading."



Here's how you can use this method:



```csharp
private void Awake()
{
    DontDestroyOnLoad(gameObject);
    PlayBackgroundMusic();
}
```



Now, your sound manager is ready!

But you still need to play the sounds using the Sound Manager.



## Playing the Game Over Sound


---



When do you play the game over sound?🤔

When the player dies!



In the `Player` script:

Firstly, you need to access the Sound Manager present in the Scene



```csharp
    private SoundManager soundManager;

    private void Start()
    {
       	//Rest of the Code

        // Get the SoundManager from the scene
        soundManager = FindObjectOfType<SoundManager>();

        if (soundManager == null)
        {
            Debug.LogError("SoundManager not found in the scene.");
        }
    }
```



Then, you can use the `soundManager` to play the sound!

```csharp
		private void PlayerDied()
		{
		    soundManager.PlayGameOverAudio();
				// Rest of your code
		}
```



Now, you can also use the same sound manager to play the Level Complete audio!



## Playing Level Complete Sound


---

The Level Complete effect can be played when the player completes a Level.



```csharp
		private void LevelComplete()
		{
		    soundManager.PlayLevelCompleteAudio();
				// Rest of your code
		}
```



> **TODO**: `**Player.cs**` 
> ✅ Play the **Game Over** and **Level Complete** sound effects



Lastly, the Button Click sound! 



## Playing BUtton CLick SOund


---

When to play the Button Click sound?🤔

Whenever a button is pressed 🤷🏼

This can be done in the same way as Game Over and Level Complete audio.



> **TODO**: 
> ✅Play the Button Click sound in `MainMenuUI.cs` and `LevelUI.cs`



Click here to see the solution.

`**MainMenuUI.cs**`

```csharp

		private SoundManager soundManager;
    
    private void Awake()
    {
         //Rest of the Code
        soundManager = FindObjectOfType<SoundManager>();
    }

		private void Play()
    {
        soundManager.PlayButtonClickAudio();
         //Rest of the Code
    }

    private void Quit()
    {
        soundManager.PlayButtonClickAudio();
         //Rest of the Code
    }

```



`**LevelUI.cs**`

```csharp
    private SoundManager soundManager;
    
    private void Awake()
    {
         //Rest of the Code
        soundManager = FindObjectOfType<SoundManager>();
    }
    
		private void MainMenuButton()
    {
        soundManager.PlayButtonClickAudio();
         //Rest of the Code
    }

    private void RestartButton()
    {
        soundManager.PlayButtonClickAudio();
        //Rest of the Code
    }
```







Lastly, you must assign the audio clips and sources in the Sound Manager and the Bgm Source.



> **TODO**: 
> ✅In the `Bgm Source` game object assign the `Sound/BGM/InfiniteDoors` as the clip.
> ✅In the Sound Manager, assign all the variables.



You have successfully played the sounds!!🥳

But there’s a problem!



## Two Sound Managers!


---

When you load the main menu from the GameOverUI, you might notice a problem:



1. The original SoundManager persists due to `DontDestroyOnLoad()`.
2. When the main menu loads, a new `SoundManager` is created.
3. Now you have two SoundManagers playing sounds simultaneously!



This can result in:

- Doubled sound effects
- Overlapping background music
- Inconsistent audio behavior



To solve this problem, you must destroy the current sound manager instance, as the Main Menu already has one instance.



## Destroying SoundManager


---

First, add a method to destroy the `SoundManager` in the `SoundManager.cs` script:

```csharp
public class SoundManager : MonoBehaviour
{
    // ... existing code ...

    public void DestroySoundManager()
    {
        Destroy(gameObject);
    }
}
```



Now, you can use it in `LevelUI` Script before loading the Main Menu:



```csharp
private void MainMenuButton()
{
    soundManager.PlayButtonClickAudio();
    soundManager.DestroySoundManager();  // Destroy the current SoundManager
    levelManager.LoadMainMenu();
}
```



> **TODO**: 
> ✅ Update your `LevelUI`, `MainMenuUI` and `LevelUI` scripts.



That's it!!

You have created your first Unity project successfully 🥳
