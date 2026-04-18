You already know how to play sound effects, but music is different.

*Why?* 🤔

Let's compare `Sound` and `Music` in SFML:



> 📖 🎮 **GAME DEV DICTIONARY** 
> ***sf::Sound***: "Perfect for short sound effects that fit in memory, like collision sounds!" 
> ***sf::Music***: "Streams music from files, ideal for long background tracks that would be too big to load entirely in memory."



Let's break down the differences:



> 💡**PROTIP**: 
> Use `Sound` for effects that need quick response (like collisions) and `Music` for background tracks that play continuously!



Click here to see more differences between Sound and Music.

![ ](//outscal.github.io/Full-Stack-Game-Development/images/05d1982c9662b47d.png)

`**sf::Sound**`** vs **`**sf::Music**`





Now, it’s time to add background music!🎶



## Creating Our Music System


---



First, let's set up our music variables:

`SoundManager.h`

```cpp
namespace Sound
{
		//sound type enum
    class SoundManager
    {
    private:
        static sf::Music backgroundMusic;
        static const string bgmPath = "Assets/Sounds/Pong_bgm.mp3";
        static float backgroundMusicVolume = 50.0f;
```

Setting up is similar to sound effects!

Let's load the background track and initialize required variables:

`SoundManager.cpp`

```cpp
sf::Music SoundManager::backgroundMusic;
const std::string SoundManager::bgmPath = "Assets/Sounds/Pong_bgm.mp3";
float SoundManager::backgroundMusicVolume = 50.0f;

void SoundManager::LoadSoundFromFile()
{
    if (!backgroundMusic.openFromFile(bgmPath))
    {
        std::cerr << "Error loading background music file: " << bgmPath << std::endl;
        return;
    }
}
```

Now for the fun part:

`SoundManager.cpp`

```cpp
void SoundManager::PlayBackgroundMusic()
{
    backgroundMusic.setVolume(backgroundMusicVolume);
    backgroundMusic.setLoop(true);// Music keeps playing
    backgroundMusic.play();// Start the music
}
```

*Why set the loop to true?*

- Music plays continuously
- No awkward silence
- Seamless experience

Now, when does the background music starts playing?🤔

As soon as the game loop starts!

`GameLoop.cpp`

```cpp
void GameLoop::initialize()
{
    //other code
    SoundManager::PlayBackgroundMusic();// Let the music begin!
}
```



> **TODO**
> ✅Create and Implement variables for background music in `SoundManager` 
> ✅Play the background music in `void GameLoop::initialize()`



Your game is complete!!💪🏼

You have successfully created a strong base in SFML🥳
