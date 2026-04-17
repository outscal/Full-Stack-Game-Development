*Have you ever played a game without sound?*

Something feels missing, right?

These aren't just sounds - they're part of gaming history!

Let’s see how you can add sounds to your game!



## Creating Sound Manager


---



Before you make our game musical, let's understand how SFML handles sound:

Think of it like a music player:

- `SoundBuffer` → Like your music file
- `Sound` → Like your player that reads the file



> 📖 🎮 **GAME DEV DICTIONARY** 
> ***SoundBuffer***: "A container that holds audio data loaded from a file." 
> ***Sound***: "The player that can play, pause, and control the audio stored in the `SoundBuffer`"



Let's build it:

Here's the folder structure:

`Header/Sound/SoundManager.h`

`Source/Sound/SoundManager.h`



`SoundManager.h`

```cpp
#pragma once
#include <SFML/Audio.hpp>
#include <string>

namespace Sound
{
    enum class SoundType
    {
        BALL_BOUNCE
    };

    class SoundManager
    {
    private:
        static sf::Music backgroundMusic;
        static sf::Sound soundEffect;
        static sf::SoundBuffer ballBounce;

        static float backgroundMusicVolume;
        static const std::string bgmPath;
        static const std::string ballBouncePath;
				
				static void Initialize();
				static void LoadSoundFromFile();
    
    public:
        static void PlaySoundEffect(SoundType soundType);
        static void PlayBackgroundMusic();
    };
}
```





**Note: **You'll understand the purpose of each method and variable as you progress in this chapter.



## Implementing Sound Manager


---

First, you need to initialize everything:

`SoundManager.cpp`

```cpp
#include "../../Header/Sounds/SoundManager.h"
#include <iostream>

namespace Sound
{

sf::SoundBuffer SoundManager::ballBounce;
sf::Sound SoundManager::soundEffect;

const std::string SoundManager::ballBouncePath = "Assets/Sounds/Ball_Bounce.wav";

void SoundManager::Initialize()
{
    LoadSoundFromFile();
}
}
```

**Note: **Notice that the variables are declared again in the `.``**cpp**`** **file.

Why?🤔

When you include a header file in multiple `.``**cpp**`** **files, 
each `.``**cpp**`** **file gets its own copy of the contents of that header during compilation. 

If you **define a static variable** (not just declare it) in the header file, it results in multiple definitions of the same variable.

By default, `**static**`** **member variables have **external linkage**. 
This means the variable is visible across the project once it is defined. 
Placing the definition in the header causes multiple definitions, which is not allowed for a **static **variable.



Then, load the file in `ballBounce`:

`SoundManager.cpp`

```cpp
void SoundManager::LoadSoundFromFile()
{
    if (!ballBounce.loadFromFile(ballBouncePath))
        std::cerr << "Error loading sound file: " << ballBouncePath << std::endl;
}
```

*Why check if the file loaded?*

- Missing files shouldn't crash the game
- Players should still be able to play
- We can show an error message instead



## Playing Sounds


---



Here's where the magic happens:

`SoundManager.cpp`

```cpp
void SoundManager::PlaySoundEffect(SoundType soundType)
{
    switch (soundType)
    {
    case SoundType::BALL_BOUNCE:
        soundEffect.setBuffer(ballBounce);
        break;
    default:
        std::cerr << "Invalid sound type" << std::endl;
        return;
    }

    soundEffect.play();
}
```

You might have noticed I have used an enum(`SoundType`) for sound effect, why?🤔

Well, currently, you only have one kind of sound effect. 

In the future, if you decide to add a game over sound, then you’ll just need to add it as type in the `SoundType` enum!



> **TODO** 
> ✅In `Header/Sound` create and implement the `SoundManager.h` file. 
> ✅In `Source/Sound` create and implement the `SoundManager.cpp` file.



You can now just use the Sound Manager to play the ball bounce sound.



## Making the Ball Bounce


---



Let's add sound to our ball collisions:

Note: Don’t forget to include `SoundManager.h` in `Ball.h`

`Ball.cpp`

```cpp
void Ball::handlePaddleCollision(Paddle* player1, Paddle* player2)
{
    // ... collision detection code ...

    if (ball_bounds.intersects(Player1PaddleBounds) && velocity.x < 0)
    {
        //old code
        SoundManager::PlaySoundEffect(SoundType::BALL_BOUNCE);
    }
}

void Ball::handleBoudaryCollision()
{
    //old code

    if (ball_bounds.top <= top_boundary || ball_bounds.top + ball_bounds.height >= bottom_boundary)
    {
		    //old code
        SoundManager::PlaySoundEffect(SoundType::BALL_BOUNCE);
    }
}
```



> **TODO** 
> ✅In `Ball.cpp` add the code to play ball bounce sound effect 
> ✅Test the sound



What happened? Sound didn’t play?🤔

Of course, you need to initialize the `SoundManager` first!

`GameLoop.cpp`

```cpp
void GameLoop::initialize()
{
	//other managers
	SoundManager::Initialize();


	game_window_manager->initialize();
}
```

Now, test the sound!

Great! You have added a bouncing sound successfully!

In the next lesson, you’ll add background music!!🎵
