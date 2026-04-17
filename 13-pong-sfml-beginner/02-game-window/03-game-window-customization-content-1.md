How to customize the game window?🤔

Let’s explore some of its different properties!



## Understanding Window Properties


---



Before you write any code, let's think about what you want to achieve:

What do you need to customize?

- Background **color**
- Window **title**
- Window **size** for different displays

Why do you need these customizations?

- Color affects gameplay experience
- Title provides game information
- Size accommodates different screens

How will you implement these?

- Using SFML's window management features
- Implementing step-by-step customizations
- Testing each change individually



## Customizing the Window


---



Let's first understand color manipulation:

```cpp
// GameWindowManager.cpp
void GameWindowManager::render() {
    // Clear window with orange color (R:200, G:50, B:50, A:255)
    game_window->clear(sf::Color(200, 50, 50, 255));
		
		//draw shapes, sprites, etc 
		
    // Display the changes
    game_window->display();
}
```

Let's break down what's happening:

- Color values range from 0 to 255(RGB)
- Alpha (255) makes the color fully opaque



> 📖 🎮 **GAME DEV DICTIONARY **
> ***RGBA***: "Red, Green, Blue, Alpha - four numbers that define a color. RGB sets the color, Alpha controls transparency (255 is fully visible, 0 is invisible)."



> 💡**PROTIP**: 
> `clear()`, `draw()`, `display()` 
> `clear()`: clears the screen. 
> `draw()`: draws an object on the window. 
> `display()`: displays the changes rendered on the window. This cycle repeats on every frame, ensuring that the window displays an updated game window after every frame.



**Note**: You’ll further use the `draw()` function in this module to draw the paddles and the ball.



> **TODO**: Window Color Implementation 
> ✅ Update the render function in `GameWindowManager.cpp` 
> ✅ Add color clearing functionality 
> ✅ Test different color combinations



Now, let’s see how you can change the title of the game window!



## Window Title Customization


---



> **TODO**: Window Title Update 
> ✅ Modify `createGameWindow` function 
> ✅ Update window title 
> ✅ Test title display



```cpp
void GameWindowManager::createGameWindow() {
    game_window->create(
        sf::VideoMode(game_window_width, game_window_height),
        game_title
    );
}
```

Now, let’s customize the size of the display for full screen!



## Customizing Size


---



Let’s see a different way of customizing the size of the game window:

```cpp
void GameWindowManager::createGameWindow() {
    game_window->create(
        sf::VideoMode::getDesktopMode(),    // Get screen resolution
        game_title,                        // Window title
        sf::Style::Fullscreen               // Fullscreen mode
    );
}
```

Here's what’s happening:

- Getting the desktop's resolution automatically
- Setting fullscreen mode flag
- Maintaining aspect ratio



> 🎮 **FACT**: 
> The first fullscreen PC game was "King's Quest" (1984), marking a major milestone in gaming history!



> **TODO**: Fullscreen Mode 
> ✅ Update `createGameWindow` 
> ✅ Add `getDesktopMode` 
> ✅ Implement fullscreen toggle



You have created a full-screen game window!

But wait... there's a catch! 😏

Try running your game now. Notice something? You're trapped! There's no way to exit fullscreen mode.

Think About 🤔:

How frustrating is this for players?

In the next lesson, you’ll make your game less frustrating by adding the feature to exit the game!
