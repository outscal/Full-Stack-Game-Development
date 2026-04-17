# ⏳Quiz

quiz


## Questions


### Q1. What happens if you attempt to draw an sf::Sprite without setting a texture?
- The sprite appears as a white rectangle. **(correct)**
- The program crashes.
- The sprite renders nothing on the screen.

### Q2. To load an image into an sf::Texture from a file, you must use the ____.
- loadTexture()
- loadFromFile() **(correct)**
- loadImage()
- setTexture()

### Q3. A texture is displayed but appears blurry when scaled. What could fix this issue?
- Use texture.setSmooth(true) to enable smoothing. **(correct)**
- Use texture.setRepeated(true) to repeat the texture.
- Avoid scaling textures in SFML.
- Manually adjust the sprite’s vertices for scaling.

### Q4. Which of the following statements about sf::Sprite is correct?
- A sprite directly stores the image data.
- A sprite automatically handles animations.
- A sprite cannot be scaled or rotated.
- A sprite requires an sf::Texture to render. **(correct)**

### Q5. What happens when the following code is executed?

sf::Sprite sprite;
sf::Texture texture;

if (texture.loadFromFile("image.png")) {
    sprite.setTexture(texture);
}
sprite.setTextureRect(sf::IntRect(10, 10, 50, 50));
- The sprite renders nothing because the setTextureRect() call is invalid.
- The sprite renders the full texture since no section was explicitly set.
- The sprite renders a 50x50 section starting at (10, 10) of the texture. **(correct)**
- The program crashes because the texture is uninitialized.

### Q6. Why can’t an sf::Texture be drawn directly using draw()?
- sf::Texture stores image data but does not provide methods for visual transformations or rendering logic.
- sf::Texture is not compatible with sf::RenderTarget, which requires a drawable object.
- sf::Texture is optimized for GPU memory but lacks a rendering mechanism, which is handled by objects like sf::Sprite. **(correct)**
- sf::Texture cannot be used with sf::Drawable as it does not inherit from it.

### Q7. Why does SFML provide sf::Drawable as a base class for its rendering objects?
- sf::Drawable provides a consistent interface for rendering, letting sf::RenderTarget render objects without needing type-specific logic. **(correct)**
- sf::Drawable allows derived classes to automatically share texture, color, and transformation settings.
- sf::Drawable ensures all rendering objects can directly interact with sf::RenderWindow for better performance.
- sf::Drawable enables objects to access GPU memory directly for rendering operations.
