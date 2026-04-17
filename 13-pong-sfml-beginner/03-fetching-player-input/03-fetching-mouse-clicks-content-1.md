Before you jump into implementation, let's see what are you going to implement in this lesson:

A way to detect **when** the player clicks. A way to know **where** they clicked.



## Detecting Mouse Clicks


---



Here's how you can detect those clicks:

`EventManager.cpp`

```cpp
bool EventManager::isLeftMouseButtonClicked()
{
// Detect if the left mouse button is clicked
    return (sf::Mouse::isButtonPressed(sf::Mouse::Left));
}

```

Let's understand what each part does:

`sf::Mouse::isButtonPressed` checks for a mouse button presses. 

We pass `sf::Mouse::Left` to detect left clicks. The function returns `true` when clicked.

Now, let’s see how you can get the position of the click.



## Get Click Position


---



Now, let's see how to track where these clicks happen in the game window:




[Watch video](https://www.loom.com/embed/400aafa407ea4a318b8d71997332eb46?sid=0586c3ee-e8d9-4466-808e-9def500a771e)





In the video, you can see that the mouse position is printed in pixels.

Just like a coordinate system, the click position is calculated.

But, there's a catch!!

Unlike the regular coordinate system, 

The top-left corner is considered as (X:0, Y:0).

This is how you can visualize the coordinate system in SFML:



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/12_06_2024__06_32_03.png)

**Position calculation in 1280x720 Game Window**



Notice how going downwards increases the y position?

That's the catch!

And, of course, anything outside of the game window has a negative position.



`EventManager.cpp`

```cpp

void EventManager::pollEvents(sf::RenderWindow* game_window) {
    sf::Event event;
    while (game_window->pollEvent(event)) {
//previous code

// Handle left mouse button click
        if (isLeftMouseButtonClicked())
        {
            sf::Vector2i position = sf::Mouse::getPosition(*game_window);

// Log the mouse position
        std::cout << "Left mouse click at: " << position.x << ", " << position.y << std::endl;
        }
    }
}
```



> 💡**ProTip**: 
> `sf::Vector2` is a simple class that defines a mathematical vector with two coordinates (x and y). 
> `sf::Vector2<float>` is `sf::Vector2f` 
> `sf::Vector2<int>` is `sf::Vector2i` 
> `sf::Vector2<unsigned int>` is `sf::Vector2u`



> **TODO: **
> **✅**Implement the`isLeftMouseButtonClicked()` function. 
> **✅**Print the click position.



In the next chapter, you'll learn about the lifecycle functions in a game loop.
