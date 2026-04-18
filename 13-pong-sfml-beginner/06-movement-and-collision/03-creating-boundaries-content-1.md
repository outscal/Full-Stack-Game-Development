*Your ball and paddles are moving... maybe a bit too much?*



## Creating the Boundaries


---



*What's the simplest shape for a boundary?*

Think about it:

- We need straight lines
- They should be visible
- They need specific positions



![ ](/Full-Stack-Game-Development/images/03f34530cfcfc26e.png)

**Boundaries**



> 💡**PROTIP**: 
> Use `RectangleShape` to create thin, line-like boundaries!



In this lesson, you just need to add four rectangle shapes with just different position and dimensions(width and height). 

You have done this before with paddles, so do this lesson as a quick sprint!🏃🏼‍➡️



Click here to see the folder structure.

![ ](/Full-Stack-Game-Development/images/a4373f7a8d070b32.png)

**Folder Structure**





## Defining Boundary Class


---

First, let's set up our boundary properties and the lifecycle functions of the Boundary class:

`Boundary.h`

```cpp
namespace Gameplay
{
	class Boundary
	{
		private:
		//horizontal
    RectangleShape topBoundary;
    //vertical
    RectangleShape leftBoundary;
    RectangleShape centerLine;

    // Horizontal boundary dimensions (top and bottom)
    const float horizontal_boundary_width = 1280.0f;
    const float horizontal_boundary_height = 20.0f;

    // Vertical boundaries dimensions (left and right)
    const float vertical_boundary_width = 20.0f;
    const float vertical_boundary_height = 720.0f;

	public:
		Boundary();
		void render(RenderWindow* game_window);
	}
```

*Why these specific dimensions?*

- Width matches game window
- Height creates visible but not intrusive borders



## Positioning the Boundaries


---

Let's think about where each boundary should go:

`Boundary.h`

```cpp
   private:
    // Top boundary starts at the window's top-left corner
    const float top_position_x = 0.0f;
    const float top_position_y = 0.0f;

    // Left boundary also starts at top-left
    const float left_position_x = 0.0f;
    const float left_position_y = 0.0f;

```

Now, you can use the properties of the rectangle to create the boundaries.



## Creating Individual Boundaries


---

First, you need functions and properties for creating the boundaries and a center line:

`Boundary.h`

```cpp
		//Boundary Colors
		const Color boundary_color = Color::Blue;
		const Color center_line_color = Color::White;
		
		//center lines properties
		const float center_line_width = 10.0f;
		const float center_line_height = 680.0f;

		const float center_line_position_x = 640.0f;
		const float center_line_position_y = 20.0f;
		
		//create boundaries and the center line
		void createTopBoundary();
		void createBottomBoundary();
		void createLeftBoundary();
		void createRightBoundary();

		void createCenterLine();

```

Then, set the size, position and color of the boundaries in their respective functions:

`Boundary.cpp`

```cpp
void Boundary::createLeftBoundary()
{
    leftBoundary.setSize(Vector2f(vertical_boundary_width, vertical_boundary_height));
    leftBoundary.setPosition(left_position_x, left_position_y);
    leftBoundary.setFillColor(boundary_color);
}
```



> **TODO** 
> ✅In `Header/Gameplay/Boundary/` implement `Boundary.h`.
> ✅In `Source/Gameplay/Boundary/Boundary.cpp` implement the `createLeftBoundary()` and `createTopBoundary()` functions.
> ✅Implement `createCenterLine()` for that classic Pong look



Click here to see the solution.

`Boundary.h`

```cpp
#pragma once
#include <SFML/Graphics.hpp>
using namespace sf;

namespace Gameplay
{
	class Boundary
	{
	private:
		RectangleShape topBoundary;
		RectangleShape bottomBoundary;
		RectangleShape leftBoundary;
		RectangleShape rightBoundary;
		RectangleShape centerLine;

		const float horizontal_boundary_width = 1280.0f;
		const float horizontal_boundary_height = 20.0f;

		const float top_position_x = 0.0f;
		const float top_position_y = 0.0f;

		const float bottom_position_x = 0.0f;
		const float bottom_position_y = 700.0f;

		const float vertical_boundary_width = 20.0f;
		const float vertical_boundary_height = 720.0f;

		const float left_position_x = 0.0f;
		const float left_position_y = 0.0f;

		const float right_position_x = 1260.0f;
		const float right_position_y = 0.0f;

		const float center_line_width = 10.0f;
		const float center_line_height = 680.0f;

		const float center_line_position_x = 640.0f;
		const float center_line_position_y = 20.0f;

		const Color boundary_color = Color::Blue;
		const Color center_line_color = Color::White;

		void createTopBoundary();
		void createBottomBoundary();
		void createLeftBoundary();
		void createRightBoundary();

		void createCenterLine();

	public:
		Boundary();

		void update();
		void render(RenderWindow* game_window);
	};
}
```

`Boundary.cpp`

```cpp
	void Boundary::createTopBoundary()
	{
		topBoundary.setSize(Vector2f(horizontal_boundary_width, horizontal_boundary_height));
		topBoundary.setPosition(top_position_x, top_position_y);
		topBoundary.setFillColor(boundary_color);
	}

	void Boundary::createLeftBoundary()
	{
		leftBoundary.setSize(Vector2f(vertical_boundary_width, vertical_boundary_height));
		leftBoundary.setPosition(left_position_x, left_position_y);
		leftBoundary.setFillColor(boundary_color);
	}

	void Boundary::createCenterLine()
	{
		centerLine.setSize(Vector2f(center_line_width, center_line_height));
		centerLine.setPosition(center_line_position_x, center_line_position_y);
		centerLine.setFillColor(center_line_color);
	}

```





You have successfully added the logic to create boundaries and a center line!

Now what?

You need to call these functions to actually create the boundaries and then render them on the game window.

You have done this before with paddles, so you need to the same for boundaries as well!



> **TODO** 
> ✅In `Boundary()` constructor call the `createLeftBoundary()` and `createTopBoundary()` functions. 
> ✅In the `Boundary::render()` draw all the boundaries and the center line.



Click here to see the solution.

`Boundary.cpp`

```cpp
Boundary::Boundary()
{
	createTopBoundary();
	createLeftBoundary();
	createCenterLine();
}

void Boundary::render(RenderWindow* game_window)
{
	game_window->draw(topBoundary);
	game_window->draw(leftBoundary);
	game_window->draw(centerLine);
}

```





Finally, you just need the `GameplayManager` to render the boundaries.



## Bringing It All Together


---

In `GameplayManager`:

- You need and object of the boundary class
- And then render the boundaries



`GameplayManager.cpp`

```cpp
GameplayManager::GameplayManager()
{
    boundary = new Boundary();
}

void GameplayManager::render(RenderWindow* game_window)
{
    boundary->render(game_window);
    ball->render(game_window);
    player1->render(game_window);
    player2->render(game_window);
}
```

*Notice the rendering order:*

1. Boundaries first (background)
2. Then, game elements (foreground)



> **TODO** 
> ✅In `GameplayManager.h` create pointer object of the `Boundary` class. 
> ✅In `GameplayManager.cpp` initialize the `boundary` object. 
> ✅In the `GameplayManager::render(RenderWindow* game_window)` call `boundary→render(game_window)`.



You have successfully created the top and the left boundaries, and a center line!

It’s your turn to create the right and the bottom boundaries!

You might have noticed something while testing the boundaries:

The ball and paddles still go right through them!

In the next lesson, you’ll add collision detection to your game!!
