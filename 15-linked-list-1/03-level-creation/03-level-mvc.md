# **Drawing a Level**


---

![Level Lableled](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__08_49_25.png)

**LEVEL**

To draw a level, you need a Background and a border!



## Drawing a background


---

Let's quickly use an image to draw the background, like in previous projects

But wait...

The background in Snake is just a solid colour, right?

Why not use a `RectangleShapeView` to draw the background?!

That'll save the texture budget and give you the freedom to pick any background colour whenever you want. You can also change the background colour from Level to Level.



Here is a quick reminder about using `RectangleShapeView` 

![RectangleShapeView Signature](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__09_26_17.png)

`**RectangleShapeView::initialize()**`** Signature**



To initialize a `RectangleShapeView` you need:

1. **Background Size:** Will be the same as the render window size
2. **Position:** Will be (0,0) since the rectangle is full screen
3. **Outline Thickness:** Will be 0 since there is no outline on the background
4. **Colour:** It'll be similar to the classic Snake with RGB values being: `(180, 200, 160)` 
5. **Outline Colour:** It will be transparent since there is no outline



> **TODO: LevelView** 
> ✅ Create below properties:
> `const sf::Color background_color = sf::Color(180, 200, 160)`
> `RectangleShapeView* background_rectangle`
> 
> ✅ Create `void initializeBackground()`, call it in `initialize()`, and inside it:
> ✅ Calculate background size by using the game window from `GraphicService` 
> ✅ Call `background_rectangle->initialize()` and pass all the arguments as discussed above
> ✅ Call `background_rectangle->show()` 
> 
> ✅ Implement `background_rectangle` by initializing using the `new` keyword in the constructor, initializing using `initializeBackground()`, calling all its lifecycle functions and finally deleting it



Click here to see `initializeBackground()` 

```cpp
void LevelView::initializeBackground()
{
    sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

    sf::Vector2f background_size = sf::Vector2f(game_window->getSize().x, game_window->getSize().y);

    background_rectangle->initialize(background_size, sf::Vector2f(0, 0), 0, background_color);
    background_rectangle->show();
}
```





## Drawing A border


---

Here comes the interesting part, 

You can either draw 4 different rectangles, 1 for each borderline

OR

You can create  a transparent rectangle with thick black outlines

To draw this rectangle, you need to know the size of the playable area.

Do you remember we discussed that the level in Snake is like a grid?

Well, you need the grid's width and height

![Border Width and Offsets](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_14_2024__10_25_50.png)

**Border Width and Offsets**

In the image, you can see offsets from all the sides. These offsets can be used to calculate the playable area.

Here are the offsets you need and the border thickness

`**LevelView.h**` 

```cpp
	namespace
	{
		class LevelView
		{
		private:
		//... some other code
			Color border_color = sf::Color::Black;
		//... some other code
		public:
			static const int border_thickness = 10
			static const int border_offset_left = 40;
			static const int border_offset_top = 40;
		//... some other code
		}
	}
```



You can use these values to calculate the grid's width and height

**Remember:** These offset values only consider the offset of only 1 side



> **TODO: LevelView**
> ✅ Create properties offsets and thickness for border, refer to above code
> ✅ Create properties:
> `private:`
> `    float grid_width`
> `    float grid_height`
> ✅ Create getter functions for `grid_width` and `grid_height` 
> ✅ Create `void calculateGridExtents()` that uses the offsets to calculate `grid_width` and `grid_height` 
> ✅ Call `calculateGridExtents()` in `initialize()`



To finally draw the border rectangle, you need:

1. **Size:** This will be the same as `grid_width` and `grid_height` combined: `border_size = Vector2f(grid_width, grid_height)` 
2. **Position:** The origin of the border is exactly the offsets, i.e. `(border_offset_left, border_offset_top)` 
3. **Outline Thickness:** You can use `border_thickness` 
4. **Colour:** Since you just need the border, this will be transparent
5. **Outline Colour:** As in the image that'll be black, you can use `border_color` 



> **TODO: LevelView** 
> 
> ✅ Create property `RectangleShapeView* border_rectangle` 
> 
> ✅ Create `void initializeBorder()`, call it in `initialize()`, and inside it:
> ✅ Calculate size by using `grid_width` and `grid_height` to create a `Vector2f` 
> ✅ Call `border_rectangle->initialize()` and pass all the arguments as discussed above
> ✅ Call `border_rectangle->show()` 
> 
> ✅ Implement `background_rectangle`by initializing using the `new` keyword in the constructor, initializing using `initializeBorder()`, calling all its lifecycle functions and finally deleting it



Click here to see `initializeBorder()` 

```cpp
void LevelView::initializeBorder()
{
    sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

    sf::Vector2f border_size = sf::Vector2f(grid_width, grid_height);
    sf::Vector2f border_position = sf::Vector2f(border_offset_left, border_offset_top);

    border_rectangle->initialize(border_size, border_position, border_thickness, sf::Color::Transparent, border_color);
    border_rectangle->show();
}
```





and done👍🏼



Click here to see `LevelView.h` 

```cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "UI/UIElement/RectangleShapeView.h"

namespace Level
{
    class LevelView
    {
    private:
        const sf::Color background_color = sf::Color(180, 200, 160);
        const sf::Color border_color = sf::Color::Black;

        UI::UIElement::RectangleShapeView* background_rectangle;
        UI::UIElement::RectangleShapeView* border_rectangle;

        float grid_width;
        float grid_height;

        void createViews();
        void initializeBackground();
        void initializeBorder();
        void calculateGridExtents();
        void destroy();

    public:
        static const int border_thickness = 10;
        static const int border_offset_left = 40;
        static const int border_offset_top = 40;

        LevelView();
        ~LevelView();

        void initialize();
        void update();
        void render();

        float getGridWidth();
        float getGridHeight();
    };
}
```



Click here to see `LevelView.cpp`

```cpp
#include "Level/LevelView.h"
#include "Global/ServiceLocator.h"
#include "Graphics/GraphicService.h"
#include "UI/UIElement/RectangleShapeView.h"

namespace Level
{
    using namespace UI::UIElement;
    using namespace Global;

    LevelView::LevelView()
    {
        createViews();
    }

    LevelView::~LevelView()
    {
        destroy();
    }

    void LevelView::createViews()
    {
        background_rectangle = new RectangleShapeView();
        border_rectangle = new RectangleShapeView();
    }

    void LevelView::initialize()
    {
        initializeBackground();
        calculateGridExtents();
        initializeBorder();
    }

    void LevelView::initializeBackground()
    {
        sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

        sf::Vector2f background_size = sf::Vector2f(game_window->getSize().x, game_window->getSize().y);

        background_rectangle->initialize(background_size, sf::Vector2f(0, 0), 0, background_color);
        background_rectangle->show();
    }

    void LevelView::initializeBorder()
    {
        sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

        sf::Vector2f border_size = sf::Vector2f(grid_width, grid_height);
        sf::Vector2f border_position = sf::Vector2f(border_offset_left, border_offset_top);

        border_rectangle->initialize(border_size, border_position, border_thickness, sf::Color::Transparent, border_color);
        border_rectangle->show();
    }

    void LevelView::calculateGridExtents()
    {
        sf::RenderWindow* game_window = ServiceLocator::getInstance()->getGraphicService()->getGameWindow();

        grid_width = game_window->getSize().x - 2 * border_offset_left;
        grid_height = game_window->getSize().y - 2 * border_offset_top;
    }

    void LevelView::destroy()
    {
        delete (background_rectangle);
        delete (border_rectangle);
    }

    void LevelView::update()
    {
        background_rectangle->update();
        border_rectangle->update();
    }

    void LevelView::render()
    {
        background_rectangle->render();
        border_rectangle->render();
    }

    float LevelView::getGridWidth()
    {
        return grid_width;
    }

    float LevelView::getGridHeight()
    {
        return grid_height;
    }
}
```





You have completed the `LevelView`
Go have a cup of coffee!☕ 



In the next chapter, you'll quickly implement the `LevelModel` and `LevelController` 

**See you there!👋🏼**
