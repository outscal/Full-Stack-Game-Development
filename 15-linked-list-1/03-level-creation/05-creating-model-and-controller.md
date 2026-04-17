To create the level, 2 pieces of the puzzle remain

The Model and the Controller



## Creating Level model


---

What all data do you need?

Since the level is basically a grid, you'll need to know the size of each cell. That size can be used for multiple things like moving the snake or spawning things.

You will also need the number of rows and columns.
You can calculate the cell's width and height by dividing grid's width by number of rows and grid's height by number of columns.

There is one more important thing 



This game has multiple levels, your `LevelModel` will handle all those levels, so it should have a list of all those levels

You can create an Array of `LevelData` but what was the biggest limitation of an array?

Fixed sized, right?



But, you can have as many levels as you want, fixed size shouldn't be a limitation. 

We have ***Vectors*** for that!

If you need a vector revision, you should look at [this](https://outscal.com/course/full-stack-game-development/array/stl-minesweeper/vectors) bonus content from Minesweeper. 



> **TODO: LevelModel** 
> ✅ Create following properties:
> `private:`
>     `std::vector<LevelData> level_configurations`
> 
>     `float cell_width`
>     `float cell_height`
> 
> `public:`
>     `static const int number_of_rows = 28`
>     `static const int number_of_columns = 50`
> 
> ✅ Create `void initialize(int width, int height)`, inside it, calculate 
> `cell_width = width / number_of_columns` 
> `cell_height = height / number_of_rows`
> ✅ Create getter functions for cell width and height



Click here to see `LevelModel.h`

```cpp
#pragma once
#include <SFML/System/Vector2.hpp>
#include "Level/LevelData.h"
#include <vector>

namespace Level
{
    class LevelModel
    {
    private:
        std::vector<LevelData> level_configurations;

        float cell_width;
        float cell_height;

    public:
        static const int number_of_rows = 28;
        static const int number_of_columns = 50;

        LevelModel();
        ~LevelModel();

        void initialize(int width, int height);

        float getCellWidth();
        float getCellHeight();
    };
}
```



Click here to see `LevelModel.cpp`

```cpp
#include "Level/LevelModel.h"

namespace Level
{
	LevelModel::LevelModel() = default;

	LevelModel::~LevelModel() = default;

	void LevelModel::initialize(int width, int height)
	{
		cell_width = width / number_of_columns;
		cell_height = height / number_of_rows;
	}

	float LevelModel::getCellWidth()
	{
		return cell_width;
	}

	float LevelModel::getCellHeight()
	{
		return cell_height;
	}
}
```





## Creating Level Controller


---

Level Controller is a quick quest, all you have to do is handle LevelModel, LevelView and Cell's width and height accessible



> **TODO: LevelController** 
> ✅ Create properties:
> `private:`
>     `LevelModel* level_model`
>     `LevelView* level_view`
> ✅ Initialize `level_model` and `level_view` inside the constructor
> ✅ Call all lifecycle functions of `level_view` 
> ✅ Call `level_model`'s initialize() and pass grid's width and height using `level_view` 
> ✅ Create getters for cell's width and height that return these dimensions using `level_model` 
> ✅ Don't forget to delete both `level_model` and `level_view`





Click here to see `LevelController.h`

```cpp
#pragma once
#include <vector>
#include "LevelModel.h"

namespace Level
{
    class LevelView;

    class LevelController
    {
    private:
        LevelModel* level_model;
        LevelView* level_view;

    public:
        LevelController();
        ~LevelController();

        void initialize();
        void update();
        void render();

        float getCellWidth();
        float getCellHeight();
    };
}
```



Click here to see `LevelController.cpp` 

```cpp
#include "Level/LevelController.h"
#include "Level/LevelModel.h"
#include "Level/LevelView.h"

namespace Level
{
	LevelController::LevelController()
	{
		level_model = new LevelModel();
		level_view = new LevelView();
	}

	LevelController::~LevelController()
	{
		delete level_model;
		delete level_view;
	}

	void LevelController::initialize()
	{
		level_view->initialize();
		level_model->initialize(level_view->getGridWidth(), level_view->getGridHeight());
	}

	void LevelController::update()
	{
		level_view->update();
	}

	void LevelController::render()
	{
		level_view->render();
	}

	float LevelController::getCellWidth()
	{
		return level_model->getCellWidth();
	}

	float LevelController::getCellHeight()
	{
		return level_model->getCellHeight();
	}
}
```





woah! that is everything you need for Level!

You've got then controller, model, view and service!



Everything is ready!



Can you see the level on the screen now?

Well...

No



There is a layer of UI between the Main Menu and the Gameplay area

That UI is for Level Selection



In the next section, you will implement this Level Selection UI and then you will be able to see the level!

**See you in the next section!👋🏼**
