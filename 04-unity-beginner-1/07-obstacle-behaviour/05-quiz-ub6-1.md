# ⏳Quiz

ub6


<div class="outscal-quiz" data-total="5">

<div class="oq-q" data-idx="0" data-answers="2">
<h3>Q1. When you rotate a sprite by adjusting its Transform.rotation each frame, inconsistent rotation speeds may occur on different devices. What causes this inconsistency, and how does it relate to frame rate dependency?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Unity&#39;s physics engine processes rotations differently across devices.</button>
  <button type="button" class="oq-opt" data-i="1">Floating-point calculations vary on different CPUs.</button>
  <button type="button" class="oq-opt" data-i="2">Higher frame rates lead to more updates per second, causing faster rotation—illustrating frame rate-dependent logic.</button>
  <button type="button" class="oq-opt" data-i="3">Time.deltaTime is inaccurate on some devices.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="1" hidden>
<h3>Q2. You want a sprite to rotate smoothly at a rate of 120 degrees per second. If your game runs at a constant frame rate of 60 frames per second, how many degrees should the sprite rotate each frame to achieve the desired rotation speed?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">0.5 degrees per frame</button>
  <button type="button" class="oq-opt" data-i="1">2 degrees per frame</button>
  <button type="button" class="oq-opt" data-i="2">3 degrees per frame</button>
  <button type="button" class="oq-opt" data-i="3">6 degrees per frame</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="1" hidden>
<h3>Q3. When rotating a sprite around a point other than its center, why is it necessary to adjust the sprite&#39;s pivot point, and how does this affect the rotation?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The pivot point doesn&#39;t affect rotation; the sprite always rotates around its center.</button>
  <button type="button" class="oq-opt" data-i="1">Adjusting the pivot point changes the center of rotation, allowing rotation around a different point like an edge.</button>
  <button type="button" class="oq-opt" data-i="2">Changing the pivot point affects the sprite&#39;s scale but not its rotation.</button>
  <button type="button" class="oq-opt" data-i="3">Pivot points are only relevant for UI elements, not sprites.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="1" hidden>
<h3>Q4. Why is it important to multiply movement or rotation amounts by Time.deltaTime when applying them in the Update() method?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">To make the movement or rotation faster.</button>
  <button type="button" class="oq-opt" data-i="1">To make the movement or rotation frame rate independent, ensuring consistency across devices.</button>
  <button type="button" class="oq-opt" data-i="2">To synchronize physics calculations.</button>
  <button type="button" class="oq-opt" data-i="3">It&#39;s not important; Time.deltaTime has no effect.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="0" hidden>
<h3>Q5. You want a sprite to rotate exactly 360 degrees over 2 seconds, regardless of frame rate. Why might adding a fixed rotation each frame not achieve this, and how does understanding time-based calculations help implement accurate rotation?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Fixed increments ignore elapsed time; using rotation speed multiplied by Time.deltaTime ensures consistent rotation over time.</button>
  <button type="button" class="oq-opt" data-i="1">High frame rates cause over-rotation; using a modulo operation resets rotation.</button>
  <button type="button" class="oq-opt" data-i="2">Fixed values are too small on high-res displays; adjusting for screen DPI solves the issue.</button>
  <button type="button" class="oq-opt" data-i="3">Incrementing per frame doesn&#39;t consider the sprite&#39;s initial rotation; resetting rotation each frame fixes it.</button>
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
