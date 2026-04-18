# ⏳Quiz

quiz


<div class="outscal-quiz" data-total="7">

<div class="oq-q" data-idx="0" data-answers="0">
<h3>Q1. What happens if you attempt to draw an sf::Sprite without setting a texture?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The sprite appears as a white rectangle.</button>
  <button type="button" class="oq-opt" data-i="1">The program crashes.</button>
  <button type="button" class="oq-opt" data-i="2">The sprite renders nothing on the screen.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="1" hidden>
<h3>Q2. To load an image into an sf::Texture from a file, you must use the ____.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">loadTexture()</button>
  <button type="button" class="oq-opt" data-i="1">loadFromFile()</button>
  <button type="button" class="oq-opt" data-i="2">loadImage()</button>
  <button type="button" class="oq-opt" data-i="3">setTexture()</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="0" hidden>
<h3>Q3. A texture is displayed but appears blurry when scaled. What could fix this issue?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Use texture.setSmooth(true) to enable smoothing.</button>
  <button type="button" class="oq-opt" data-i="1">Use texture.setRepeated(true) to repeat the texture.</button>
  <button type="button" class="oq-opt" data-i="2">Avoid scaling textures in SFML.</button>
  <button type="button" class="oq-opt" data-i="3">Manually adjust the sprite’s vertices for scaling.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="3" hidden>
<h3>Q4. Which of the following statements about sf::Sprite is correct?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">A sprite directly stores the image data.</button>
  <button type="button" class="oq-opt" data-i="1">A sprite automatically handles animations.</button>
  <button type="button" class="oq-opt" data-i="2">A sprite cannot be scaled or rotated.</button>
  <button type="button" class="oq-opt" data-i="3">A sprite requires an sf::Texture to render.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="2" hidden>
<h3>Q5. What happens when the following code is executed?

sf::Sprite sprite;
sf::Texture texture;

if (texture.loadFromFile(&quot;image.png&quot;)) {
    sprite.setTexture(texture);
}
sprite.setTextureRect(sf::IntRect(10, 10, 50, 50));</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The sprite renders nothing because the setTextureRect() call is invalid.</button>
  <button type="button" class="oq-opt" data-i="1">The sprite renders the full texture since no section was explicitly set.</button>
  <button type="button" class="oq-opt" data-i="2">The sprite renders a 50x50 section starting at (10, 10) of the texture.</button>
  <button type="button" class="oq-opt" data-i="3">The program crashes because the texture is uninitialized.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="5" data-answers="2" hidden>
<h3>Q6. Why can’t an sf::Texture be drawn directly using draw()?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">sf::Texture stores image data but does not provide methods for visual transformations or rendering logic.</button>
  <button type="button" class="oq-opt" data-i="1">sf::Texture is not compatible with sf::RenderTarget, which requires a drawable object.</button>
  <button type="button" class="oq-opt" data-i="2">sf::Texture is optimized for GPU memory but lacks a rendering mechanism, which is handled by objects like sf::Sprite.</button>
  <button type="button" class="oq-opt" data-i="3">sf::Texture cannot be used with sf::Drawable as it does not inherit from it.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="6" data-answers="0" hidden>
<h3>Q7. Why does SFML provide sf::Drawable as a base class for its rendering objects?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">sf::Drawable provides a consistent interface for rendering, letting sf::RenderTarget render objects without needing type-specific logic.</button>
  <button type="button" class="oq-opt" data-i="1">sf::Drawable allows derived classes to automatically share texture, color, and transformation settings.</button>
  <button type="button" class="oq-opt" data-i="2">sf::Drawable ensures all rendering objects can directly interact with sf::RenderWindow for better performance.</button>
  <button type="button" class="oq-opt" data-i="3">sf::Drawable enables objects to access GPU memory directly for rendering operations.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-done" hidden>
<h2>Quiz Complete</h2>
<p>You scored <span class="oq-score">0</span> out of <span class="oq-total">7</span>.</p>
</div>
</div>
