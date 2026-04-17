# ⏳ Quiz

## Questions


### Q1. How can a developer differentiate between a left mouse button click and a right mouse button click using SFML events?
- By using separate event queues for left and right mouse buttons.
- By comparing event.mouseButton.button to sf::Mouse::Left or sf::Mouse::Right within a sf::Event::MouseButtonPressed event. **(correct)**
- By checking the position of the mouse cursor during the click.

### Q2. In SFML, how does handling the sf::Event::LostFocus event contribute to resource management and user experience in a game application?
-  It enables the game to save the current state automatically before losing focus.
- It ensures that all ongoing animations are completed before the window loses focus.
- It prevents the user from interacting with other applications while the game is running.
-  It allows the game to pause or reduce resource usage when the window is not active, enhancing performance and user experience. **(correct)**

### Q3. How does the handling of sf::Event::TextEntered differ from sf::Event::KeyPressed in SFML, and what implication does this have for implementing text input fields in a game?
- TextEntered captures raw key codes, while KeyPressed captures Unicode characters, making TextEntered unsuitable for text input fields.
- TextEntered captures Unicode characters, including special characters and international input, making it essential for accurate text input fields. **(correct)**
- Both events function identically, so handling either one is sufficient for text input fields.
- KeyPressed is only triggered for alphabetic keys, while TextEntered captures all key presses.

### Q4. You are creating a 2D platformer using SFML. 
During gameplay, you notice that holding down a movement key causes the game to stutter intermittently. Upon reviewing your event handling code, you realize that pollEvent() is being called excessively within the game loop. What is the most effective way to resolve this issue while maintaining responsive input handling?
- Limit the number of times pollEvent() is called per frame and combine it with real-time input checks using functions like sf::Keyboard::isKeyPressed(). **(correct)**
- Remove pollEvent() entirely and rely solely on real-time input checks for handling all user inputs.
-  Increase the game's frame rate to ensure pollEvent() can handle more events without stuttering.
- Use blocking calls for pollEvent() to prevent excessive polling within the game loop.

### Q5. Using sf::Event::TextEntered is the most appropriate way to handle character input for a text box in SFML, as it accounts for internationalization and special characters.
- True **(correct)**
- False

### Q6. You notice that your SFML-based game's performance drops significantly when handling a large number of sf::Event::TextEntered events rapidly, such as when a user is typing quickly in a chat box. What is the most effective way to mitigate this issue without losing any user input?
-  Disable the chat box feature to reduce event handling load.
- Increase the size of the event queue to accommodate more events.
- Switch from event-based input handling to polling-based input handling for text input.
- Implement input buffering by storing TextEntered events and processing them in batches each frame. **(correct)**
