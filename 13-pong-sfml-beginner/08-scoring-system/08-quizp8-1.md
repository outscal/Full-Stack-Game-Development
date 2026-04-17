# ⏳Quiz

quiz


## Questions


### Q1. Examine the following code snippet. What is its output?

sf::Text text;
text.setString("Game Over");
text.setCharacterSize(32);
text.setFillColor(sf::Color::White);

sf::Font font;
text.setFont(font);

window.draw(text);
- The text "Game Over" is displayed in white with a size of 32.
- The text is not displayed because the font was not loaded. **(correct)**
- The text is displayed in the system's default font.

### Q2. In SFML, text is drawn using the ____ class, which requires a ____ object to set its appearance.
- sf::Font, sf::String
- sf::String, sf::Font
- sf::Text, sf::Font **(correct)**
- sf::String, sf::Text

### Q3. To change the color of text in SFML, you use the ____ method of the sf::Text class.
- setFillColor() **(correct)**
- setColor()
- setTextColor()
- setFontColor()

### Q4. You are creating a heads-up display (HUD) for your game. The text updates frequently (e.g., score or timer). How should you handle fonts to optimize performance?
- Reload the font file every frame to ensure the text is displayed correctly.
- Load the font once into an sf::Font object and reuse it for all text elements. **(correct)**
- Use sf::Text without a font to improve rendering speed.
- Use system fonts directly to save memory.
