# ⏳Quiz

ub7


<div class="outscal-quiz" data-total="4">

<div class="oq-q" data-idx="0" data-answers="1">
<h3>Q1. You want to move a sprite smoothly from point A to point B over a period of time. Using Vector3.Lerp in the Update() method, you notice the sprite starts moving quickly and slows down as it approaches point B. Why does this happen, and how can understanding the mathematical function behind Lerp help you achieve a constant movement speed?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Lerp uses linear interpolation, so the speed should be constant; the issue must be elsewhere.</button>
  <button type="button" class="oq-opt" data-i="1">Lerp needs a consistent interpolation parameter over time; using Time.deltaTime incorrectly causes deceleration.</button>
  <button type="button" class="oq-opt" data-i="2">The sprite slows down due to floating-point precision loss near point B; increasing precision fixes it.</button>
  <button type="button" class="oq-opt" data-i="3"> Lerp inherently creates easing effects; using MoveTowards ensures constant speed.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="1" hidden>
<h3>Q2. While scaling a sprite uniformly over time to double its size, you observe that the sprite becomes pixelated and loses quality. Why might this occur, and how does understanding the concept of texture filtering and sprite import settings help in preserving visual quality during scaling?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Scaling doesn&#39;t affect sprite quality; the issue is with the camera settings.</button>
  <button type="button" class="oq-opt" data-i="1">Sprites are raster images; scaling enlarges pixels. Adjusting texture filtering can help.</button>
  <button type="button" class="oq-opt" data-i="2">The sprite&#39;s mesh becomes distorted when scaled; using higher-quality meshes prevents pixelation.</button>
  <button type="button" class="oq-opt" data-i="3">Unity doesn&#39;t support scaling sprites; using vector graphics is necessary.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="1" hidden>
<h3>Q3. You need to move a sprite from point A to point B in a straight line at a constant speed, ensuring it stops exactly at point B. Why might using Vector3.MoveTowards in the Update() method be more appropriate than using transform.Translate, and how does understanding MoveTowards help achieve precise movement?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">MoveTowards ignores frame rate; the sprite moves instantly to point B.</button>
  <button type="button" class="oq-opt" data-i="1">MoveTowards moves the sprite incrementally toward the target each frame, stopping precisely at point B regardless of frame rate.</button>
  <button type="button" class="oq-opt" data-i="2">transform.Translate automatically adjusts for frame rate, making it better for precise movement.</button>
  <button type="button" class="oq-opt" data-i="3">Using transform.position directly ensures constant speed and precise stopping.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="2" hidden>
<h3>Q4. When scaling a sprite non-uniformly (e.g., scaling only on the X-axis), the sprite appears stretched and distorted. Why does non-uniform scaling cause this distortion, and how can you mitigate the issue?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Unity doesn&#39;t support non-uniform scaling; only uniform scaling works.</button>
  <button type="button" class="oq-opt" data-i="1">Pivot point shifts during scaling; fixing it prevents distortion.</button>
  <button type="button" class="oq-opt" data-i="2">Non-uniform scaling changes aspect ratio; adjust artwork or maintain aspect ratio to avoid stretching.</button>
  <button type="button" class="oq-opt" data-i="3">Camera&#39;s field of view affects scaling; adjusting camera fixes it.</button>
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
