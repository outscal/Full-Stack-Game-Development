# ⏳Quiz

quiz


<div class="outscal-quiz" data-total="5">

<div class="oq-q" data-idx="0" data-answers="1">
<h3>Q1. In Unity&#39;s **Hierarchy** window, you can organize GameObjects in a parent-child relationship. Suppose you have a parent GameObject with a non-uniform scale (e.g., X: 2, Y: 1, Z: 1) and a child GameObject with a uniform scale (X: 1, Y: 1, Z: 1). If you rotate the parent GameObject by 90 degrees around the Y-axis, how does this transformation affect the scale and orientation of the child GameObject in world space?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The child&#39;s scale remains uniform, but its orientation changes due to the parent&#39;s rotation.</button>
  <button type="button" class="oq-opt" data-i="1">The child inherits the non-uniform scale and rotation, causing distortion in its shape.</button>
  <button type="button" class="oq-opt" data-i="2">The child&#39;s world scale becomes non-uniform, and its orientation remains unchanged.</button>
  <button type="button" class="oq-opt" data-i="3">The child&#39;s local scale and orientation remain the same, with no impact from the parent.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="0" hidden>
<h3>Q2. In the Inspector, some components have a small &quot;lock&quot; icon in the upper right corner. What is the purpose of this lock, and how can it be used to enhance your workflow when working with multiple GameObjects and components?In the Inspector, some components have a small &quot;lock&quot; icon in the upper right corner. What is the purpose of this lock, and how can it be used to enhance your workflow when working with multiple GameObjects and components?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Locking the Inspector prevents it from updating when other GameObjects are selected, allowing you to drag and drop references into the locked Inspector.</button>
  <button type="button" class="oq-opt" data-i="1">It secures the component&#39;s properties, making them read-only to prevent accidental changes.</button>
  <button type="button" class="oq-opt" data-i="2">The lock hides the component from the Inspector to declutter the interface.</button>
  <button type="button" class="oq-opt" data-i="3">- It locks the GameObject&#39;s Transform, preventing any movement, rotation, or scaling.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="2" hidden>
<h3>Q3. The Rotate Tool in Unity provides different rotation handle orientations. When working with nested GameObjects, how does using the Global rotation handle differ from the Local rotation handle in terms of the resulting transformation, and why might this distinction be important when animating objects?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Global rotation modifies the GameObject&#39;s world rotation, affecting its global transformation, which is important for animations that rely on world coordinates.</button>
  <button type="button" class="oq-opt" data-i="1">Using Global rotation can cause gimbal lock, while Local rotation prevents it due to quaternion calculations.</button>
  <button type="button" class="oq-opt" data-i="2"> Local rotation changes the object&#39;s rotation relative to its parent, preserving hierarchical animations.</button>
  <button type="button" class="oq-opt" data-i="3">There is no difference; both handles affect the rotation in the same way.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="1" hidden>
<h3>Q4. The Scale Tool can uniformly or non-uniformly scale GameObjects. What potential issues might arise when non-uniformly scaling a GameObject that has child objects or is part of a prefab, and how does this relate to concepts of inheritance and transformation hierarchies in Unity?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Scaling a parent GameObject has no effect on its children due to encapsulation principles.</button>
  <button type="button" class="oq-opt" data-i="1">Non-uniform scaling can cause child objects to inherit distorted scales, leading to rendering artifacts and complicating prefab instances.</button>
  <button type="button" class="oq-opt" data-i="2">Prefabs automatically adjust to compensate for parent scaling, maintaining their original appearance.</button>
  <button type="button" class="oq-opt" data-i="3">Non-uniform scaling only affects the collider components, not the visual representation.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="0" hidden>
<h3>Q5. When using the View Tool (hand icon) in Unity&#39;s Scene view, you can navigate around your scene. However, there&#39;s a feature called Flythrough mode activated by holding the right mouse button and using WASD keys. How does Flythrough mode enhance scene navigation, and what advantages does it offer when working with large or complex scenes compared to traditional panning and zooming?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Flythrough mode allows for intuitive first-person navigation, making it easier to traverse and inspect large scenes quickly.</button>
  <button type="button" class="oq-opt" data-i="1">It locks the camera to predefined paths, limiting navigation but improving performance.</button>
  <button type="button" class="oq-opt" data-i="2">Flythrough mode provides an orthographic view, which is better for level design but not for inspecting object details.</button>
  <button type="button" class="oq-opt" data-i="3">It slows down the navigation speed, offering more precision but taking longer to move across the scene.</button>
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
