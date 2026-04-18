# ⏳Quiz

quiz


<div class="outscal-quiz" data-total="7">

<div class="oq-q" data-idx="0" data-answers="3">
<h3>Q1. What does the following code do?

sf::CircleShape circle(50.f);
circle.setPosition(200.f, 100.f);
circle.setOrigin(50.f, 50.f);</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Positions the circle so its top-left corner is at (200, 100).</button>
  <button type="button" class="oq-opt" data-i="1">Positions the circle so its bottom-right corner is at (200, 100).</button>
  <button type="button" class="oq-opt" data-i="2">Positions the circle relative to its parent window’s origin.</button>
  <button type="button" class="oq-opt" data-i="3">Positions the circle so its center is at (200, 100).</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="1" data-answers="1" hidden>
<h3>Q2. In SFML, the function getLocalBounds() returns the bounding box of an object in world coordinates.</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">True</button>
  <button type="button" class="oq-opt" data-i="1">False</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="2" data-answers="3" hidden>
<h3>Q3. You are developing a game where objects need to stay inside the game window. How can you prevent objects from moving outside the bounds?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Use only the object’s position (getPosition()) to check if it exceeds the window&#39;s dimensions and reset its position using setPosition() if necessary.</button>
  <button type="button" class="oq-opt" data-i="1">Use getLocalBounds() to calculate the object&#39;s size in local space and prevent its movement outside the window bounds.</button>
  <button type="button" class="oq-opt" data-i="2">Disable all transformations (e.g., scale, rotation) on the object to ensure it always stays within the window bounds.</button>
  <button type="button" class="oq-opt" data-i="3">Use the object’s position (getPosition()) and size (getGlobalBounds()) to ensure that none of the object’s edges exceed the window’s dimensions, resetting its position using setPosition() if needed.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="3" data-answers="0" hidden>
<h3>Q4. What happens when the following corrected code is executed?

sf::CircleShape circle1;
circle1.setRadius(30.f); // Circle with radius 30
circle1.setPosition(100.f, 100.f);

sf::CircleShape circle2;
circle2.setRadius(30.f); // Circle with radius 30
circle2.setPosition(120.f, 100.f);

if (circle1.getGlobalBounds().intersects(circle2.getGlobalBounds())) {
    std::cout &lt;&lt; &quot;Collision detected!&quot; &lt;&lt; std::endl;
}
</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">A collision is detected because getGlobalBounds() detects overlapping bounding boxes.</button>
  <button type="button" class="oq-opt" data-i="1">No collision is detected because getGlobalBounds() only checks bounding boxes, not the actual circle shapes.</button>
  <button type="button" class="oq-opt" data-i="2">A runtime error occurs because getGlobalBounds() cannot be used for circle shapes.</button>
  <button type="button" class="oq-opt" data-i="3">A collision is detected only if the center points of the circles are closer than their radii.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="4" data-answers="1" hidden>
<h3>Q5. What does the following code snippet do?

sf::CircleShape ball;
ball.setRadius(20.f); // Radius of 20
ball.setOrigin(20.f, 20.f);
ball.setPosition(100.f, 100.f);</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">Positions the ball such that its top-left corner is at (100, 100).</button>
  <button type="button" class="oq-opt" data-i="1">Positions the ball such that its center is at (100, 100).</button>
  <button type="button" class="oq-opt" data-i="2">Positions the ball at (80, 80) since the origin is moved to the radius.</button>
  <button type="button" class="oq-opt" data-i="3">Causes a runtime error due to the setOrigin call.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="5" data-answers="2" hidden>
<h3>Q6. You are using getGlobalBounds() for collision detection but notice that when two rotated rectangles overlap visually, no collision is detected. What could be the issue?</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">You need to implement a pixel-perfect collision detection algorithm to handle rotated rectangles accurately.</button>
  <button type="button" class="oq-opt" data-i="1">The rectangles are overlapping visually, but their origins are not aligned, leading to incorrect collision detection.</button>
  <button type="button" class="oq-opt" data-i="2">The getGlobalBounds() method uses an axis-aligned bounding box, so rotated rectangles may overlap visually without their AABBs intersecting.</button>
  <button type="button" class="oq-opt" data-i="3">The getGlobalBounds() method does not account for scaling or rotation in its calculations.</button>
</div>
<button type="button" class="oq-submit" disabled>Submit</button>
<div class="oq-feedback" hidden></div>
<button type="button" class="oq-next" hidden>Next →</button>
</div>

<div class="oq-q" data-idx="6" data-answers="1" hidden>
<h3>Q7. What will be the result of executing this code snippet?

sf::RectangleShape rect;
rect.setSize(sf::Vector2f(100.f, 50.f)); // Set the rectangle size
rect.setPosition(300.f, 200.f);
rect.setRotation(45.f);

sf::FloatRect bounds = rect.getGlobalBounds();
std::cout &lt;&lt; &quot;Bounds width: &quot; &lt;&lt; bounds.width &lt;&lt; &quot;, height: &quot; &lt;&lt; boubounds.height &lt;&lt; std::endl;</h3>
<div class="oq-opts">
  <button type="button" class="oq-opt" data-i="0">The global bounds match the rectangle&#39;s original width and height (Output: Bounds width: 100, height: 50).</button>
  <button type="button" class="oq-opt" data-i="1">The global bounds are an axis-aligned bounding box around the rotated rectangle (Output: Bounds width: 106.066, height: 106.066).</button>
  <button type="button" class="oq-opt" data-i="2">The global bounds are the same as the local bounds because rotation doesn’t affect bounding boxes (Output: Bounds width: 100, height: 50).</button>
  <button type="button" class="oq-opt" data-i="3">The program crashes because getGlobalBounds() cannot handle rotated objects.</button>
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
