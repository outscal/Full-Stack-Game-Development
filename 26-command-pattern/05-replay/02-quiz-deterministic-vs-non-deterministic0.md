# Quiz - Deterministic vs Non-Deterministic

Quiz - Deterministic vs Non-Deterministic


<div class="outscal-quiz" data-total="2">

<div class="oq-q" data-idx="0" data-answers="2">
<h3>Q1. Can the Command Pattern be used for implementing undo and replay features in non-deterministic game engines?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Yes, by recording and replaying individual player actions just like in deterministic engines.</button>
  <button type="button" class="oq-opt" data-i="1">Yes, by periodically taking snapshots of the game state to provide some level of consistency.</button>
  <button type="button" class="oq-opt" data-i="2">No, the Command Pattern is not suitable for non-deterministic game engines.</button>
  <button type="button" class="oq-opt" data-i="3">Yes, by creating branching timelines to account for the multiple possible outcomes.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="2" hidden>
<h3>Q2. Can the Command Pattern be used for implementing undo and replay features in games with continuous gameplay?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Yes, by storing player actions as command objects and replaying them in the same order as they were originally executed.</button>
  <button type="button" class="oq-opt" data-i="1">No, the Command Pattern is only suitable for games with discrete gameplay, and it cannot handle continuous gameplay.</button>
  <button type="button" class="oq-opt" data-i="2">Yes, by employing a time-stamped command queue to maintain the sequence of actions for replay.</button>
  <button type="button" class="oq-opt" data-i="3">Yes, as long as you have a Time-Traveling Unicorn</button>
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
