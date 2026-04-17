# ⏳Quiz

quiz


## Questions


### Q1. You are optimizing your game's lifecycle functions to reduce startup time. Currently, the `Initialize()` function loads all game assets (textures, sounds, levels) at once before the game starts, causing a noticeable delay.

What modification to the lifecycle functions can help improve the game's startup performance without sacrificing user experience?
- Reduce the number of assets loaded to only essential ones at startup.
-  Load all assets during the Update() phase to distribute the load across frames.
- Implement asynchronous loading by loading assets in the background during a loading screen, allowing the game to remain responsive. **(correct)**
- Load assets on-demand during gameplay, even if it causes minor hitches when new assets are needed.

### Q2. Examine the following game loop structure:

while (window.isOpen())
{
    // Handle input
    sf::Event event;
    while (window.pollEvent(event))
    {
        if (event.type == sf::Event::Closed)
            window.close();
    }

    // Render the game
    window.clear();
    window.draw(playerSprite);
    window.display();

    // Update game state
    player.update();
}

What potential issue arises from the order in which the functions are called?
- Input handling should occur after rendering to capture late inputs. Move the input handling loop below the rendering commands.
- The game state is updated after rendering, causing the rendered frame to display the previous state. **(correct)**
- There is no issue with the current order; the game loop is correctly structured.
- The window.clear(); function should be called after player.update(); to prevent flickering. Rearrange the order accordingly.

### Q3. Consider the following code snippet in SFML:

#include <SFML/Graphics.hpp>int main() {
    sf::RenderWindow window(sf::VideoMode(800, 600), "Lifecycle Test");

    while (window.isOpen()) {
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear(sf::Color::Black);
        // Rendering logic here
        window.display();
    }
    return 0;
}

What happens if you omit the `window.display()` line from the main loop?
- A compilation error occurs.
- The program runs but no rendering happens on the screen. **(correct)**
- Only the background color (black) is displayed.
- The program crashes with an exception.

### Q4. Examine the following code:

sf::RenderWindow window(sf::VideoMode(800, 600), "My Game");

// In the rendering loop
window.clear();
sf::CircleShape circle(50);
circle.setFillColor(sf::Color::Green);
window.display();

What is rendered to the screen?
- A green circle on a black background.
- A green circle, but the background color is uninitialized.
- Nothing appears; there is an error in the code.
- A black screen with no circle. **(correct)**

### Q5. SFML uses double buffering for rendering by default. What is the main advantage of this approach?
- It allows rendering on the GPU and CPU simultaneously.
- It automatically manages memory allocation for objects.
- It eliminates screen tearing by presenting fully rendered frames. **(correct)**
- It enables support for multiple windows
