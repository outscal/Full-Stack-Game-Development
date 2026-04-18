# ⏳ Quiz

<div class="outscal-quiz" data-total="6">

<div class="oq-q" data-idx="0" data-answers="1">
<h3>Q1. How can a developer differentiate between a left mouse button click and a right mouse button click using SFML events?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">By using separate event queues for left and right mouse buttons.</button>
  <button type="button" class="oq-opt" data-i="1">By comparing event.mouseButton.button to sf::Mouse::Left or sf::Mouse::Right within a sf::Event::MouseButtonPressed event.</button>
  <button type="button" class="oq-opt" data-i="2">By checking the position of the mouse cursor during the click.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="3" hidden>
<h3>Q2. In SFML, how does handling the sf::Event::LostFocus event contribute to resource management and user experience in a game application?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0"> It enables the game to save the current state automatically before losing focus.</button>
  <button type="button" class="oq-opt" data-i="1">It ensures that all ongoing animations are completed before the window loses focus.</button>
  <button type="button" class="oq-opt" data-i="2">It prevents the user from interacting with other applications while the game is running.</button>
  <button type="button" class="oq-opt" data-i="3"> It allows the game to pause or reduce resource usage when the window is not active, enhancing performance and user experience.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="1" hidden>
<h3>Q3. How does the handling of sf::Event::TextEntered differ from sf::Event::KeyPressed in SFML, and what implication does this have for implementing text input fields in a game?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">TextEntered captures raw key codes, while KeyPressed captures Unicode characters, making TextEntered unsuitable for text input fields.</button>
  <button type="button" class="oq-opt" data-i="1">TextEntered captures Unicode characters, including special characters and international input, making it essential for accurate text input fields.</button>
  <button type="button" class="oq-opt" data-i="2">Both events function identically, so handling either one is sufficient for text input fields.</button>
  <button type="button" class="oq-opt" data-i="3">KeyPressed is only triggered for alphabetic keys, while TextEntered captures all key presses.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="0" hidden>
<h3>Q4. You are creating a 2D platformer using SFML. 
During gameplay, you notice that holding down a movement key causes the game to stutter intermittently. Upon reviewing your event handling code, you realize that pollEvent() is being called excessively within the game loop. What is the most effective way to resolve this issue while maintaining responsive input handling?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Limit the number of times pollEvent() is called per frame and combine it with real-time input checks using functions like sf::Keyboard::isKeyPressed().</button>
  <button type="button" class="oq-opt" data-i="1">Remove pollEvent() entirely and rely solely on real-time input checks for handling all user inputs.</button>
  <button type="button" class="oq-opt" data-i="2"> Increase the game&#39;s frame rate to ensure pollEvent() can handle more events without stuttering.</button>
  <button type="button" class="oq-opt" data-i="3">Use blocking calls for pollEvent() to prevent excessive polling within the game loop.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="0" hidden>
<h3>Q5. Using sf::Event::TextEntered is the most appropriate way to handle character input for a text box in SFML, as it accounts for internationalization and special characters.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">True</button>
  <button type="button" class="oq-opt" data-i="1">False</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="5" data-answers="3" hidden>
<h3>Q6. You notice that your SFML-based game&#39;s performance drops significantly when handling a large number of sf::Event::TextEntered events rapidly, such as when a user is typing quickly in a chat box. What is the most effective way to mitigate this issue without losing any user input?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0"> Disable the chat box feature to reduce event handling load.</button>
  <button type="button" class="oq-opt" data-i="1">Increase the size of the event queue to accommodate more events.</button>
  <button type="button" class="oq-opt" data-i="2">Switch from event-based input handling to polling-based input handling for text input.</button>
  <button type="button" class="oq-opt" data-i="3">Implement input buffering by storing TextEntered events and processing them in batches each frame.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-done" hidden>
<h2>Quiz Complete</h2>
<p>You scored <span class="oq-score">0</span> out of <span class="oq-total">6</span>.</p>
</div>
</div>
