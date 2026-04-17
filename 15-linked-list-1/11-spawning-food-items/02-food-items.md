You have eight types of food items, but you'll only need one class to handle all of them. How great is that!!

A food item is quite similar to an obstacle, with the key difference being what happens when the snake collides with it. 

So, let's get started on creating your `FoodItem` class!



## **Food Item**


---

Think of the `FoodItem` class as the chef's kitchen, where all the ingredients combine to create something delicious. 

Here's what each food item needs:

- An `ImageView` for displaying the food.
- A grid position to know where it is on the grid.
- Width and height to determine its size.
- The food type.



> **TODO: FoodItem**
> ✅ Create file for `class FoodItem` in `Food` folder 
> ✅ Create empty lifecycle methods other than `initialize()`
> ✅ Create the following properties:

> private:
> `UI::UIElement::ImageView* food_image`
> `sf::Vector2i grid_position`
> `float cell_width`
> `float cell_height`
> `FoodType food_type`
> 
> public:
> `static const int number_of_foods = 8`



## **Setting Food Texture 🎨**


---



Now, let’s talk about textures. Each food type needs a specific texture to make it look distinct. 

You can achieve this using a `switch-case` statement in the`FoodItem` class returning the texture path of food type. (You can use `Config` for texture path)



> **TODO: FoodItem** 
> ✅ Create `sf::String FoodItem::getFoodTexturePath()` 
> ✅ `getFoodTexturePath()` should return the texture path based on `food_type`. Refer the `Config` for texture path.





Click here to see `getFoodTexturePath()````cpp
sf::String FoodItem::getFoodTexturePath()
{
	switch (food_type)
	{
	case Food::FoodType::APPLE:
		return Config::apple_texture_path;

	case Food::FoodType::MANGO:
		return Config::mango_texture_path;

	case Food::FoodType::ORANGE:
		return Config::orange_texture_path;

	case Food::FoodType::PIZZA:
		return Config::pizza_texture_path;

	case Food::FoodType::BURGER:
		return Config::burger_texture_path;

	case Food::FoodType::CHEESE:
		return Config::cheese_texture_path;

	case Food::FoodType::POISION:
		return Config::poision_texture_path;

	case Food::FoodType::ALCOHOL:
		return Config::alcohol_texture_path;
	}
}
```



## **Calculating Food’s Position 📍**


---



The position of the food item is as crucial as its appearance. It needs to be placed accurately on the grid. 

You need to create a method that calculates and returns screen position based on `grid_position`, cell’s dimensions and the Level’s border offsets. 

You have already implemented the same logic to find the obstacle’s image position or body part's screen position. You can do it here as well.



> **TODO: FoodItem** 
> ✅ Create `sf::Vector2f FoodItem::getFoodImagePosition()`



Click here to see `getFoodImagePosition()````cpp
sf::Vector2f FoodItem::getFoodImagePosition()
{
	float screen_position_x = LevelView::border_offset_left + (cell_width * grid_position.x);
	float screen_position_y = LevelView::border_offset_top + (cell_height * grid_position.y);

	return sf::Vector2f(screen_position_x, screen_position_y);
}
```



## **Initializing the Food Image 🖼️**


---



With the texture and position ready, it's time to initialize the `food_image`.



> **TODO: FoodItem** 
> ✅ Create `void FoodItem::initializeFoodImage()`
> ✅ It should use `getFoodImagePosition()` and `getFoodTexturePath()` to initialize `food_image`
> ✅ Call `food_image->initialize(food_texture_path, cell_width, cell_height, screen_position)`
> ✅ Call `food_image->show()`





Click here to see `initializeFoodImage()````cpp
void FoodItem::initializeFoodImage()
{
	sf::Vector2f screen_position = getFoodImagePosition();
	sf::String food_texture_path = getFoodTexturePath();

	food_image->initialize(food_texture_path, cell_width, cell_height, screen_position);
	food_image->show();
}
```



Alright, it's time to implement `**initialize()**` function based on the parameter.

With this function, your `FoodItem` class will be ready for action!



```cpp
void FoodItem::initialize(sf::Vector2i grid_pos, float width, float height, FoodType type)
{
	grid_position = grid_pos;
	cell_width = width;
	cell_height = height;
	food_type = type;

	initializeFoodImage();
}
```



> **TODO: FoodItem** 
> ✅ Refer to the above code and create `void FoodItem::initialize()`





## **Wrapping Up the Food Class 🎁**


---

Implement all lifecycle functions and a getter function that returns the FoodType.



> **TODO: FoodItem** 
> ✅ Implement all lifecycle functions. `initialize()` is already created 
> ✅ Create `FoodType getFoodType()` that returns `food_type`





Click here to see `FoodItem.h````cpp
#pragma once
#include <SFML/Graphics.hpp>
#include "UI/UIElement/ImageView.h"

namespace Food
{
    enum class FoodType;

    class FoodItem
    {
    private:
        UI::UIElement::ImageView* food_image;

        sf::Vector2i grid_position;

        float cell_width;
        float cell_height;

        FoodType food_type;

        void initializeFoodImage();
        sf::String getFoodTexturePath();
        sf::Vector2f getFoodImagePosition();

    public:
        static const int number_of_foods = 8;

        FoodItem();
        ~FoodItem();

        void initialize(sf::Vector2i grid_pos, float width, float height, FoodType type);
        void update();
        void render();

        FoodType getFoodType();
    };
}
```

Click here to see `FoodItem.cpp````cpp
#include "Food/FoodItem.h"
#include "Global/ServiceLocator.h"
#include "Level/LevelView.h"
#include "Global/Config.h"
#include "Food/FoodType.h"

namespace Food
{
	using namespace Global;
	using namespace Level;
	using namespace UI::UIElement;

	FoodItem::FoodItem()
	{
		food_image = new ImageView();
	}

	FoodItem::~FoodItem()
	{
		delete (food_image);
	}

	void FoodItem::initialize(sf::Vector2i grid_pos, float width, float height, FoodType type)
	{
		grid_position = grid_pos;
		cell_width = width;
		cell_height = height;
		food_type = type;

		initializeFoodImage();
	}

	void FoodItem::initializeFoodImage()
	{
		sf::Vector2f screen_position = getFoodImagePosition();
		sf::String food_texture_path = getFoodTexturePath();

		food_image->initialize(food_texture_path, cell_width, cell_height, screen_position);
		food_image->show();
	}

	sf::String FoodItem::getFoodTexturePath()
	{
		switch (food_type)
		{
		case Food::FoodType::APPLE:
			return Config::apple_texture_path;

		case Food::FoodType::MANGO:
			return Config::mango_texture_path;

		case Food::FoodType::ORANGE:
			return Config::orange_texture_path;

		case Food::FoodType::PIZZA:
			return Config::pizza_texture_path;

		case Food::FoodType::BURGER:
			return Config::burger_texture_path;

		case Food::FoodType::CHEESE:
			return Config::cheese_texture_path;

		case Food::FoodType::POISION:
			return Config::poision_texture_path;

		case Food::FoodType::ALCOHOL:
			return Config::alcohol_texture_path;
		}
	}

	void FoodItem::update()
	{
		food_image->update();
	}

	void FoodItem::render()
	{
		food_image->render();
	}

	FoodType FoodItem::getFoodType()
	{
		return food_type;
	}

	sf::Vector2f FoodItem::getFoodImagePosition()
	{
		float screen_position_x = LevelView::border_offset_left + (cell_width * grid_position.x);
		float screen_position_y = LevelView::border_offset_top + (cell_height * grid_position.y);

		return sf::Vector2f(screen_position_x, screen_position_y);
	}
}
```



Your food items are prepared, but they are still left to be served (**spawn**)!



![Food GIFs - Find & Share on GIPHY](https://media1.giphy.com/media/EDV30lQQ9VW5q/200w.gif?cid=6c09b952zyrslvjo7v5t7gfp8h4rd5vtpyzokwdqyp7p7p01&ep=v1_gifs_search&rid=200w.gif&ct=g)



In the next section, you’ll understand how to spawn these delicious and dangerous food items correctly.

**See you there! 👋🏼**
