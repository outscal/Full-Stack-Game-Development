Currently, the ball looks like a circle drawn and colored by a 5-year-old kid🎨

Let's make the Ball visually appealing using SFML's texture system.



Click here to see the updated `Ball.h`

`Ball.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "../../Header/Gameplay/Paddle/Paddle.h"
using namespace sf;
using namespace std;

namespace Gameplay
{
    class Ball
    {
    private:
        Texture pong_ball_texture;
        Sprite pong_ball_sprite;

        string texture_path = "Assets/Textures/Ball.png";

        const float scale_x = 0.06f;
        const float scale_y = 0.06f;

        const float position_x = 615.0f;
        const float position_y = 325.0f;

        void loadTexture();
        void initializeVariables();

    public:

        Ball();

        void update();
        void render(RenderWindow* game_window);
    };
}
```







![ ](//outscal.github.io/Full-Stack-Game-Development/images/881719fc1e4d6fe3.gif)

**Better Ball**



> **TODO**: Let's See What We're Creating! 
> ✅Navigate to your project folder and open `Assets/Textures` 
> ✅Locate and open `Ball.png` 
> ✅Compare it with your circle



`Ball.png` is the file you will use to make the ball visually appealing.

*But, How does SFML handle images in games?*

You need to understand textures to know this.



## What is a Texture?


---



A texture in SFML is an image stored in your computer's memory. When SFML loads an image:

- A texture lives in the graphics card memory, therefore it is very fast to draw
- Allows the game to use this data repeatedly without reloading the file



## Loading Our Ball Texture


---



You can use the Texture class and a string variable to store the texture:

`Ball.h`

```cpp
private:
    Texture pong_ball_texture;
    const string texture_path = "Assets/Textures/Ball.png";
```

*How do we get this image into memory?*

SFML provides the `loadFromFile` method. Let's implement it:



> 📖 🎮 **GAME DEV DICTIONARY **
> ***loadFromFile***: "SFML method that reads image data into graphics memory for rendering."



`Ball.cpp`

```cpp
void Ball::loadTexture()
{
    if (!pong_ball_texture.loadFromFile(texture_path))
    {
        throw std::runtime_error("Failed to load ball texture!");
    }
}
```



The ball’s texture is ready to be drawn!

But, there’s a catch!

*Can you draw a texture directly to the window?*

No! Textures aren't drawable objects. We need something called a **Sprite**.

But what's a sprite?🤔



## Understanding Sprites


---



`SFML` gives you a powerful tool called `Sprite`.

A sprite is a rectangular entity that can display a texture (an image).



![Sprite](//outscal.github.io/Full-Stack-Game-Development/images/5f94911f8a9d47a8.png)

**Sprite**



Why can the texture not be drawn directly on the game window?🤔

Well, that's because the texture is not a `Drawable` object!

But what is a drawable object?🤔



![Drawable](//outscal.github.io/Full-Stack-Game-Development/images/12a9fe524c612f3a.png)

**Drawable Classes**



`sf::Drawable` is a very simple base class that allows objects of derived classes(like `Shape`, `Sprite`, etc.) to be drawn to a `sf::RenderTarget`.

Now, what’s a render target?! 🤨

As the name suggests, it is a **target** on which **drawable** objects are **rendered**!

For example, The game window is an object of `**RenderWindow**`** **that is inherited from `**RenderTarget**`.

Hence, you can render **Shapes, sprites, etc(drawable objects)** on the **game window(render target)** without using complex OpenGL commands directly!

Okay, this much knowledge is more than enough!

To know more about this, refer to the [SFML documentation](https://).

Now, let’s set up the sprite!



## Setting Up the Sprite


---



Now, let’s actually see how you can add a sprite:

`Ball.h`

```cpp
private:
    Sprite pong_ball_sprite;
```

*But how big should our sprite be?*

We need scaling factors:

`Ball.h`

```cpp
private:
    const float scale_x = 0.2f; // 20% of original size
    const float scale_y = 0.2f; // 20% of original size
```

Now that we have our texture loaded, let's configure the sprite to display it.

*What steps do we need to initialize a sprite?*

1. Link it to a texture
2. Set its size/scale
3. Position it on screen

Let's create a method to handle this:

`Ball.cpp`

```cpp
void Ball::initializeVariables()
{
    pong_ball_sprite.setTexture(pong_ball_texture);  // Link texture to sprite
    pong_ball_sprite.setScale(scale_x, scale_y);     // Set size
    pong_ball_sprite.setPosition(position_x, position_y); // Set position
}
```



> 📖 🎮 **GAME DEV DICTIONARY **
> ***setTexture***: "SFML method that assigns a texture to a sprite for rendering." 
> ***setScale***: "SFML method that adjusts sprite size relative to texture dimensions."
> ***setPosition***: "SFML method that completely overwrites the previous position "



*When should you initialize these variables?*

In the constructor, right after loading the texture:

`Ball.cpp`

```cpp
Ball::Ball()
{
    loadTexture();
    initializeVariables();
}
```

Now, the sprite is ready to be rendered!



## Rendering Ball Sprite


---



Our ball previously used CircleShape for rendering. Now it's time to switch to the sprite.

*How do we render a sprite in SFML?*

Replace the old render method with:

`Ball.cpp`

```cpp
void Ball::render(RenderWindow* game_window)
{
    game_window->draw(pong_ball_sprite);
}
```



That's it! SFML handles all the texture rendering internally.



> **TODO **
> **✅**Update `Ball.h` with new texture and sprite properties 
> ✅Implement `loadTexture` and `initializeVariables` in `Ball.cpp` 
> ✅Replace Circle rendering with Sprite rendering



Okay, the ball looks much better now!😌

It’s time to move these static objects!!
