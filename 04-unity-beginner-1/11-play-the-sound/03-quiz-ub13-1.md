# ⏳Quiz

 ub13


<div class="outscal-quiz" data-total="5">

<div class="oq-q" data-idx="0" data-answers="2">
<h3>Q1. What is the primary purpose of the DontDestroyOnLoad method in Unity?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">It prevents a GameObject from being destroyed when the application quits.</button>
  <button type="button" class="oq-opt" data-i="1">It locks a GameObject&#39;s position and rotation, preventing accidental changes during gameplay.</button>
  <button type="button" class="oq-opt" data-i="2">It keeps a GameObject and its children intact when loading a new scene, allowing persistent data or behaviors.</button>
  <button type="button" class="oq-opt" data-i="3">It duplicates a GameObject across all scenes, creating copies in each loaded scene.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="2" hidden>
<h3>Q2. When using DontDestroyOnLoad, which potential issue must you consider to prevent unintended behavior in your game?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">It disables the GameObject&#39;s ability to interact with new scene elements, isolating it.</button>
  <button type="button" class="oq-opt" data-i="1">It can cause memory leaks if overused; freeing up memory manually is necessary.</button>
  <button type="button" class="oq-opt" data-i="2">Multiple instances of the same GameObject may persist across scenes, leading to duplicates and conflicts.</button>
  <button type="button" class="oq-opt" data-i="3">It resets all component values to default, causing loss of game state information.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="0" hidden>
<h3>Q3. Which of the following correctly describes how the AudioSource component works in Unity?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">It plays back audio clips attached to it, allowing control over volume, pitch, and spatial settings.</button>
  <button type="button" class="oq-opt" data-i="1">It processes audio effects like reverb and echo, applied globally to all sounds.</button>
  <button type="button" class="oq-opt" data-i="2">It records audio input from the user&#39;s microphone for in-game communication.</button>
  <button type="button" class="oq-opt" data-i="3"> It manages the game&#39;s audio settings, such as master volume and audio device selection.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="1" hidden>
<h3>Q4. How can you play an audio clip attached to an AudioSource component exactly once, ensuring it doesn&#39;t loop?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Set the loop property to true and call Play().</button>
  <button type="button" class="oq-opt" data-i="1">Set the loop property to false and call Play().</button>
  <button type="button" class="oq-opt" data-i="2">Use PlayOneShot(audioClip) with the loop property enabled.</button>
  <button type="button" class="oq-opt" data-i="3">Adjust the priority to prevent looping and call Play().</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="1" hidden>
<h3>Q5. You use FindObjectOfType&lt;MyComponent&gt;() to locate a component in your scene, but it returns null even though the component exists. What could be a possible reason for this, and how does understanding Unity&#39;s object hierarchy help you resolve the issue?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The component script has syntax errors; FindObjectOfType cannot locate faulty scripts.</button>
  <button type="button" class="oq-opt" data-i="1">The GameObject containing the component is inactive; FindObjectOfType does not find components on inactive GameObjects.</button>
  <button type="button" class="oq-opt" data-i="2">The component is attached to a prefab; FindObjectOfType cannot find components on prefabs.</button>
  <button type="button" class="oq-opt" data-i="3">There are multiple components of the same type; FindObjectOfType cannot determine which one to return.</button>
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
