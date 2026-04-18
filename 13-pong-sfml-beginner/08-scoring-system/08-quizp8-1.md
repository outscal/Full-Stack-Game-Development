# ⏳Quiz

quiz


<div class="outscal-quiz" data-total="4">

<div class="oq-q" data-idx="0" data-answers="1">
<h3>Q1. Examine the following code snippet. What is its output?

sf::Text text;
text.setString(&quot;Game Over&quot;);
text.setCharacterSize(32);
text.setFillColor(sf::Color::White);

sf::Font font;
text.setFont(font);

window.draw(text);</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The text &quot;Game Over&quot; is displayed in white with a size of 32.</button>
  <button type="button" class="oq-opt" data-i="1">The text is not displayed because the font was not loaded.</button>
  <button type="button" class="oq-opt" data-i="2">The text is displayed in the system&#39;s default font.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="2" hidden>
<h3>Q2. In SFML, text is drawn using the ____ class, which requires a ____ object to set its appearance.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">sf::Font, sf::String</button>
  <button type="button" class="oq-opt" data-i="1">sf::String, sf::Font</button>
  <button type="button" class="oq-opt" data-i="2">sf::Text, sf::Font</button>
  <button type="button" class="oq-opt" data-i="3">sf::String, sf::Text</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="0" hidden>
<h3>Q3. To change the color of text in SFML, you use the ____ method of the sf::Text class.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">setFillColor()</button>
  <button type="button" class="oq-opt" data-i="1">setColor()</button>
  <button type="button" class="oq-opt" data-i="2">setTextColor()</button>
  <button type="button" class="oq-opt" data-i="3">setFontColor()</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="1" hidden>
<h3>Q4. You are creating a heads-up display (HUD) for your game. The text updates frequently (e.g., score or timer). How should you handle fonts to optimize performance?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Reload the font file every frame to ensure the text is displayed correctly.</button>
  <button type="button" class="oq-opt" data-i="1">Load the font once into an sf::Font object and reuse it for all text elements.</button>
  <button type="button" class="oq-opt" data-i="2">Use sf::Text without a font to improve rendering speed.</button>
  <button type="button" class="oq-opt" data-i="3">Use system fonts directly to save memory.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-done" hidden>
<h2>Quiz Complete</h2>
<p>You scored <span class="oq-score">0</span> out of <span class="oq-total">4</span>.</p>
</div>
</div>
