# ⏳Quiz

quiz


<div class="outscal-quiz" data-total="5">

<div class="oq-q" data-idx="0" data-answers="2">
<h3>Q1. You are optimizing your game&#39;s lifecycle functions to reduce startup time. Currently, the `Initialize()` function loads all game assets (textures, sounds, levels) at once before the game starts, causing a noticeable delay.

What modification to the lifecycle functions can help improve the game&#39;s startup performance without sacrificing user experience?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Reduce the number of assets loaded to only essential ones at startup.</button>
  <button type="button" class="oq-opt" data-i="1"> Load all assets during the Update() phase to distribute the load across frames.</button>
  <button type="button" class="oq-opt" data-i="2">Implement asynchronous loading by loading assets in the background during a loading screen, allowing the game to remain responsive.</button>
  <button type="button" class="oq-opt" data-i="3">Load assets on-demand during gameplay, even if it causes minor hitches when new assets are needed.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="1" hidden>
<h3>Q2. Examine the following game loop structure:

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

What potential issue arises from the order in which the functions are called?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Input handling should occur after rendering to capture late inputs. Move the input handling loop below the rendering commands.</button>
  <button type="button" class="oq-opt" data-i="1">The game state is updated after rendering, causing the rendered frame to display the previous state.</button>
  <button type="button" class="oq-opt" data-i="2">There is no issue with the current order; the game loop is correctly structured.</button>
  <button type="button" class="oq-opt" data-i="3">The window.clear(); function should be called after player.update(); to prevent flickering. Rearrange the order accordingly.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="1" hidden>
<h3>Q3. Consider the following code snippet in SFML:

#include &lt;SFML/Graphics.hpp&gt;int main() {
    sf::RenderWindow window(sf::VideoMode(800, 600), &quot;Lifecycle Test&quot;);

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

What happens if you omit the `window.display()` line from the main loop?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">A compilation error occurs.</button>
  <button type="button" class="oq-opt" data-i="1">The program runs but no rendering happens on the screen.</button>
  <button type="button" class="oq-opt" data-i="2">Only the background color (black) is displayed.</button>
  <button type="button" class="oq-opt" data-i="3">The program crashes with an exception.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="3" hidden>
<h3>Q4. Examine the following code:

sf::RenderWindow window(sf::VideoMode(800, 600), &quot;My Game&quot;);

// In the rendering loop
window.clear();
sf::CircleShape circle(50);
circle.setFillColor(sf::Color::Green);
window.display();

What is rendered to the screen?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">A green circle on a black background.</button>
  <button type="button" class="oq-opt" data-i="1">A green circle, but the background color is uninitialized.</button>
  <button type="button" class="oq-opt" data-i="2">Nothing appears; there is an error in the code.</button>
  <button type="button" class="oq-opt" data-i="3">A black screen with no circle.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="2" hidden>
<h3>Q5. SFML uses double buffering for rendering by default. What is the main advantage of this approach?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">It allows rendering on the GPU and CPU simultaneously.</button>
  <button type="button" class="oq-opt" data-i="1">It automatically manages memory allocation for objects.</button>
  <button type="button" class="oq-opt" data-i="2">It eliminates screen tearing by presenting fully rendered frames.</button>
  <button type="button" class="oq-opt" data-i="3">It enables support for multiple windows</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-done" hidden>
<h2>Quiz Complete</h2>
<p>You scored <span class="oq-score">0</span> out of <span class="oq-total">5</span>.</p>
</div>
</div>
