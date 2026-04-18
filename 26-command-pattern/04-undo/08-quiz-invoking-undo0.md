# Quiz - Invoking Undo

Quiz - Invoking Undo


<div class="outscal-quiz" data-total="2">

<div class="oq-q" data-idx="0" data-answers="1,2,3">
<h3>Q1. What&#39;s the problem with the below implementation of undo method in command invoker?

public void Undo() { commandRegistry.Pop().Undo(); }</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">It will work as intended.</button>
  <button type="button" class="oq-opt" data-i="1">No base conditions are present.</button>
  <button type="button" class="oq-opt" data-i="2">If the command registry is empty we will get a stack underflow exception.</button>
  <button type="button" class="oq-opt" data-i="3">If the last executed command does not belongs to the current active player it will create weird bugs.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="1" hidden>
<h3>Q2. In a real-time strategy game like age of empires, a player orders multiple units to move and attack an enemy base simultaneously. 
If you decide to undo this complex action, which strategy should be employed?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Store each unit&#39;s individual actions and reverse them in the exact order they were executed.</button>
  <button type="button" class="oq-opt" data-i="1">Implement a &quot;group command&quot; that encapsulates all unit commands and can be undone as a single operation.</button>
  <button type="button" class="oq-opt" data-i="2">Disable the undo feature for complex group actions to avoid issues.</button>
  <button type="button" class="oq-opt" data-i="3">Record a snapshot of the entire game state before the complex action and revert to it during undo.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-done" hidden>
<h2>Quiz Complete</h2>
<p>You scored <span class="oq-score">0</span> out of <span class="oq-total">2</span>.</p>
</div>
</div>
