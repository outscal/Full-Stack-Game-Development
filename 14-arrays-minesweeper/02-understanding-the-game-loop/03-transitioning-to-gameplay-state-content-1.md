Currently, you're in the Splash Screen state:

`**GameLoop.cpp**`

![ ](/Full-Stack-Game-Development/images/8da6f2fde648cbf6.png)





In this lesson, you'll transition from the *Splash Screen* state to the *Gameplay* state.

But, how to do that? 🤔

Well, for that you need to open the `SplashScreenManager.cpp` file.

Here's the path of the `SplashScreenManager.cpp` file: `**source/UI/SplashScreen/SplashScreenManager.cpp**`



## Transitioning to Gameplay!


---

For transitioning to the Gameplay state, 
you need to understand the `drawLogo()` method of the `SplashScreenManager` class.

- using delta time, `elapsed_time` is increasing at every frame.
- Until the `elapsed_time` reaches a `logo_animation_duration`, the logo is being drawn.
- As soon as the `logo_animation_duration` is reached the `elapsed_time` is being reset.  



`SplashScreenManager.cpp`

```cpp
    void SplashScreenManager::drawLogo()
    {
        elapsed_time = elapsed_time + Time::TimeManager::getDeltaTime();

        if (elapsed_time < logo_animation_duration)
            game_window->draw(logo_sprite);
    }
```



Currently, the logo is drawn again after the `logo_animation_duration` is reached.

But, you need to change the state to the Gameplay state instead of redrawing the logo.

You can use the `setGameState()` method of the `GameLoop` class to transition to the `Gameplay` state:



`SplashScreenManager.cpp`

```cpp
void SplashScreenManager::drawLogo()
{
     elapsed_time = elapsed_time + Time::TimeManager::getDeltaTime();

    if (elapsed_time < logo_animation_duration)
    		game_window->draw(logo_sprite);
    else
        GameLoop::setGameState(GameState::GAMEPLAY); //Change the game state
}
```



You have set the game state to the Gameplay state.

But,

ideally, the state should transition from the `Splash Screen` ->`Main Menu` ->`Gameplay` state.

But the ideal is boring🥱

So, we’ll build the gameplay first!😉



> **TODO:** 
> ✅ In `SplashScreenManager.cpp` update the `drawLogo()` method. 
> ✅ Run the code.



That turned dark!

Don’t worry 😌

You’ll create the complete gameplay from scratch!

Sounds exciting?

**See you in the next chapter! 💪**
