# ⏳Quiz

quiz


## Questions


### Q1. What does the following code do?

sf::CircleShape circle(50.f);
circle.setPosition(200.f, 100.f);
circle.setOrigin(50.f, 50.f);
- Positions the circle so its top-left corner is at (200, 100).
- Positions the circle so its bottom-right corner is at (200, 100).
- Positions the circle relative to its parent window’s origin.
- Positions the circle so its center is at (200, 100). **(correct)**

### Q2. In SFML, the function getLocalBounds() returns the bounding box of an object in world coordinates.
- True
- False **(correct)**

### Q3. You are developing a game where objects need to stay inside the game window. How can you prevent objects from moving outside the bounds?
- Use only the object’s position (getPosition()) to check if it exceeds the window's dimensions and reset its position using setPosition() if necessary.
- Use getLocalBounds() to calculate the object's size in local space and prevent its movement outside the window bounds.
- Disable all transformations (e.g., scale, rotation) on the object to ensure it always stays within the window bounds.
- Use the object’s position (getPosition()) and size (getGlobalBounds()) to ensure that none of the object’s edges exceed the window’s dimensions, resetting its position using setPosition() if needed. **(correct)**

### Q4. What happens when the following corrected code is executed?

sf::CircleShape circle1;
circle1.setRadius(30.f); // Circle with radius 30
circle1.setPosition(100.f, 100.f);

sf::CircleShape circle2;
circle2.setRadius(30.f); // Circle with radius 30
circle2.setPosition(120.f, 100.f);

if (circle1.getGlobalBounds().intersects(circle2.getGlobalBounds())) {
    std::cout << "Collision detected!" << std::endl;
}

- A collision is detected because getGlobalBounds() detects overlapping bounding boxes. **(correct)**
- No collision is detected because getGlobalBounds() only checks bounding boxes, not the actual circle shapes.
- A runtime error occurs because getGlobalBounds() cannot be used for circle shapes.
- A collision is detected only if the center points of the circles are closer than their radii.

### Q5. What does the following code snippet do?

sf::CircleShape ball;
ball.setRadius(20.f); // Radius of 20
ball.setOrigin(20.f, 20.f);
ball.setPosition(100.f, 100.f);
- Positions the ball such that its top-left corner is at (100, 100).
- Positions the ball such that its center is at (100, 100). **(correct)**
- Positions the ball at (80, 80) since the origin is moved to the radius.
- Causes a runtime error due to the setOrigin call.

### Q6. You are using getGlobalBounds() for collision detection but notice that when two rotated rectangles overlap visually, no collision is detected. What could be the issue?
- You need to implement a pixel-perfect collision detection algorithm to handle rotated rectangles accurately.
- The rectangles are overlapping visually, but their origins are not aligned, leading to incorrect collision detection.
- The getGlobalBounds() method uses an axis-aligned bounding box, so rotated rectangles may overlap visually without their AABBs intersecting. **(correct)**
- The getGlobalBounds() method does not account for scaling or rotation in its calculations.

### Q7. What will be the result of executing this code snippet?

sf::RectangleShape rect;
rect.setSize(sf::Vector2f(100.f, 50.f)); // Set the rectangle size
rect.setPosition(300.f, 200.f);
rect.setRotation(45.f);

sf::FloatRect bounds = rect.getGlobalBounds();
std::cout << "Bounds width: " << bounds.width << ", height: " << boubounds.height << std::endl;
- The global bounds match the rectangle's original width and height (Output: Bounds width: 100, height: 50).
- The global bounds are an axis-aligned bounding box around the rotated rectangle (Output: Bounds width: 106.066, height: 106.066). **(correct)**
- The global bounds are the same as the local bounds because rotation doesn’t affect bounding boxes (Output: Bounds width: 100, height: 50).
- The program crashes because getGlobalBounds() cannot handle rotated objects.
