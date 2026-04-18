**Obstacles to Life!!**



Alright, get ready to introduce obstacles into your game! 🚧

Before directly jumping to `ElementService` , first, complete the properties required for `Obstacle`.



To create obstacles in your game, you'll need to define a few key properties:

- **Image**: What the obstacle looks like (use `ImageView`).
- **Grid Position**: Where it sits on the board (e.g., `sf::Vector2i`).
- **Dimensions**: Width & height to fit within a single cell.



> **TODO: **`**Obstacle**`

> ✅ Create `Obstacle.h` and `Obstacle.cpp` inside the `Element` folder and create a namespace `Element` inside it.

> ✅ Create empty lifecycle functions, apart from `initialize()`.

> ✅ Add the following properties:

> `UI::UIElement::ImageView* obstacle_image;`

> `sf::Vector2i grid_position;`

> `float cell_width;`

> `float cell_height;`

> ✅ Call `obstacle_image->update()` in `update()`.

> ✅ Call `obstacle_image->render()` in `render()`




**Done?**

Let's do more!



## INITIALIZING THE OBstacle


---

To initialize the obstacle, you need its width, height and you also need its grid position.

You can take all the values inside the `initialize()` function



> **TODO: **`**Obstacle**`
> ✅ Create `void initialize(sf::Vector2i grid_pos, float width, float height)`
> ✅ Set the values of the related properties inside the method based on the values taken in parameters



You have taken the information, but the image is not initialized. 

For that, you need `initializeObstacleImage()`:

```cpp
void Obstacle::initializeObstacleImage()
    {
        sf::Vector2f screen_position = getObstacleImagePosition();
        obstacle_image->initialize(Config::obstacle_texture_path, cell_width, cell_height, screen_position);
        obstacle_image->show();
    }
```



You can find the sprite for obstacles in `Config`.


Are you confused about what is `getObstacleImagePosition()`?

This helper function calculates the exact screen coordinates for the obstacle's image based on grid position and cell size.



```cpp
sf::Vector2f Obstacle::getObstacleImagePosition()
    {
        float screen_position_x = LevelView::border_offset_left + (cell_width * grid_position.x);
        float screen_position_y = LevelView::border_offset_top + (cell_height * grid_position.y);
        return sf::Vector2f(screen_position_x, screen_position_y);
    }
```



Here's how it works:

During the initialization of the obstacle, you are setting the position of the obstacle with respect to the grid (), 

Let's assume you need an obstacle at grid position **(1,1)**

To calculate the left screen position (**X** coordinate) of the obstacle,

- Multiply the obstacle's grid position by the cell width to get its distance from the grid's left edge.
- Then, add the left border offset to position the obstacle within the entire screen view.

Similarly, you can also calculate the obstacle's top screen position (**Y** coordinate).



![Image](/Full-Stack-Game-Development/images/0b572ac058ad2064.png)

***Screen Position***



> **TODO: **`**Obstacle**`
> ✅ Create and implement `initializeObstacleImage()` 
> ✅ Create and implement`getObstacleImagePosition()` 
> ✅ Call `initializeObstacleImage()` inside the `initialize()`



**Click here to see **`**Obstacle.h**`** **```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "UI/UIElement/ImageView.h"

namespace Element
{
    class Obstacle
    {
    private:
        UI::UIElement::ImageView* obstacle_image;

        sf::Vector2i grid_position;

        float cell_width;
        float cell_height;

        void initializeObstacleImage();
        sf::Vector2f getObstacleImagePosition();

    public:
        Obstacle();
        ~Obstacle();

        void initialize(sf::Vector2i grid_pos, float width, float height);
        void update();
        void render();
    };
}
```

**Click here to see **`**Obstacle.cpp**````cpp
#include "Element/Obstacle.h"
#include "Global/ServiceLocator.h"
#include "Level/LevelView.h"
#include "Global/Config.h"

namespace Element
{
	using namespace Global;
	using namespace Level;
	using namespace UI::UIElement;

	Obstacle::Obstacle()
	{
		obstacle_image = new ImageView();
	}

	Obstacle::~Obstacle()
	{
		delete (obstacle_image);
	}

	void Obstacle::initialize(sf::Vector2i grid_pos, float width, float height)
	{
		grid_position = grid_pos;
		cell_width = width;
		cell_height = height;

		initializeObstacleImage();
	}

	void Obstacle::initializeObstacleImage()
	{
		sf::Vector2f screen_position = getObstacleImagePosition();
		obstacle_image->initialize(Config::obstacle_texture_path, cell_width, cell_height, screen_position);

		obstacle_image->show();
	}

	void Obstacle::update()
	{
		obstacle_image->update();
	}

	void Obstacle::render()
	{
		obstacle_image->render();
	}

	sf::Vector2f Obstacle::getObstacleImagePosition()
	{
		float screen_position_x = LevelView::border_offset_left + (cell_width * grid_position.x);
		float screen_position_y = LevelView::border_offset_top + (cell_height * grid_position.y);

		return sf::Vector2f(screen_position_x, screen_position_y);
	}
}
```



And there you go! 

You've just added obstacles to your game. 

This is an important step forward, and you're doing great! 🎉



Next up, into the `ElementService`, which will handle all the logic related to these elements. And this time, for sure 🤭

**See you in the next section! 👋🏼**
