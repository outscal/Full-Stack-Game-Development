# ⏳Quiz

quiz


<div class="outscal-quiz" data-total="4">

<div class="oq-q" data-idx="0" data-answers="0">
<h3>Q1. The std::chrono library can measure delta time by taking the difference between two ____.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">std::time_point objects</button>
  <button type="button" class="oq-opt" data-i="1">std::duration objects</button>
  <button type="button" class="oq-opt" data-i="2">std::thread objects</button>
  <button type="button" class="oq-opt" data-i="3">std::timer objects</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="2" hidden>
<h3>Q2. What does the following code do?

#include &lt;chrono&gt;

auto lastTime = std::chrono::high_resolution_clock::now();

while (gameRunning) {
    auto currentTime = std::chrono::high_resolution_clock::now();
    std::chrono::duration&lt;float&gt; deltaTime = currentTime - lastTime;
    lastTime = currentTime;

    std::cout &lt;&lt; &quot;Delta Time: &quot; &lt;&lt; deltaTime.count() &lt;&lt; &quot; seconds&quot; &lt;&lt; std::endl;
}</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Prints the elapsed time since the application started.</button>
  <button type="button" class="oq-opt" data-i="1">Prints the frame rate of the application.</button>
  <button type="button" class="oq-opt" data-i="2">Prints the time elapsed between the last frame and the current frame (delta time).</button>
  <button type="button" class="oq-opt" data-i="3">Causes a runtime error because std::chrono::duration is not compatible with std::chrono::high_resolution_clock.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="3" hidden>
<h3>Q3. Why might using std::chrono::system_clock for delta time cause issues in your game loop?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">It doesn’t support measuring nanoseconds, which are critical for delta time.</button>
  <button type="button" class="oq-opt" data-i="1">It’s less precise than std::time.</button>
  <button type="button" class="oq-opt" data-i="2">It requires manual synchronization with the graphics card.</button>
  <button type="button" class="oq-opt" data-i="3">It can be adjusted by the operating system, causing jumps or inconsistencies in time measurements.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="2" hidden>
<h3>Q4. What will happen if you calculate delta time like this?

#include &lt;chrono&gt;
auto currentTime = std::chrono::high_resolution_clock::now();
std::chrono::duration&lt;float&gt; deltaTime = currentTime.time_since_epoch();</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Delta time will correctly represent the time elapsed since the last frame and will be updated every loop.</button>
  <button type="button" class="oq-opt" data-i="1">Delta time will be the total time elapsed since the program started running.</button>
  <button type="button" class="oq-opt" data-i="2">Delta time will represent the time elapsed since a fixed point in time defined by system, making it unsuitable for frame-to-frame calculations.</button>
  <button type="button" class="oq-opt" data-i="3">The code will cause a runtime error because time_since_epoch() cannot be used with std::chrono::high_resolution_clock.</button>
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
