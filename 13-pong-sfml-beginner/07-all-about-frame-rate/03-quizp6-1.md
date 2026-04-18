# ⏳Quiz

quiz


<div class="outscal-quiz" data-total="5">

<div class="oq-q" data-idx="0" data-answers="2">
<h3>Q1. What happens if your game is frame rate dependent?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The game logic executes at the same speed regardless of the frame rate.</button>
  <button type="button" class="oq-opt" data-i="1">The frame rate dynamically adjusts to the game’s logic.</button>
  <button type="button" class="oq-opt" data-i="2">The game logic is tied to the frame rate, meaning faster frame rates cause the game to run faster.</button>
  <button type="button" class="oq-opt" data-i="3">The game&#39;s visuals degrade if the frame rate exceeds a certain threshold.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="0" hidden>
<h3>Q2. Delta time refers to the amount of time that has passed between the rendering of the ____ and the ____.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">previous frame; current frame</button>
  <button type="button" class="oq-opt" data-i="1">game start; current frame</button>
  <button type="button" class="oq-opt" data-i="2">first frame; last frame</button>
  <button type="button" class="oq-opt" data-i="3">current frame; next frame</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="3" hidden>
<h3>Q3. Why is delta time important in game development?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">It ensures smooth rendering of visuals by synchronizing them with the GPU.</button>
  <button type="button" class="oq-opt" data-i="1">It fixes performance issues by automatically adjusting the game logic to match the player&#39;s hardware.</button>
  <button type="button" class="oq-opt" data-i="2">It helps synchronize animations but is unnecessary for other parts of the game.</button>
  <button type="button" class="oq-opt" data-i="3">It allows game logic and movement to be independent of the frame rate, ensuring consistent gameplay across different systems.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="2" hidden>
<h3>Q4. What would happen if you implemented delta time incorrectly, such as failing to reset it every frame?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Objects would move at a constant speed, regardless of the frame rate.</button>
  <button type="button" class="oq-opt" data-i="1">Objects would stop moving because delta time would remain stuck at zero.</button>
  <button type="button" class="oq-opt" data-i="2">Delta time would accumulate, becoming increasingly large, causing objects to move erratically or unrealistically fast.</button>
  <button type="button" class="oq-opt" data-i="3">Delta time would remain consistent, but game physics would be inaccurate.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="1" hidden>
<h3>Q5. A game is running at an average frame rate of 60 frames per second (FPS). The player’s character moves at a speed of 300 units per second. Using delta time to make the movement frame rate independent, calculate how far the character moves in one frame.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">10 units</button>
  <button type="button" class="oq-opt" data-i="1">5 units</button>
  <button type="button" class="oq-opt" data-i="2">50 units</button>
  <button type="button" class="oq-opt" data-i="3">20 units</button>
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
