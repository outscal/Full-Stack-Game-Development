# **TASKS**


---



## creating food type


---

1. Create empty `FoodType.h` and follow `namespace Food` 
2. Create empty `FoodItem` classes with empty lifecycle methods apart from `initialize()` and follow `namespace Food` 



## [IN FoodType.h]

1. Create `enum class FoodType` with enums as:

> `APPLE,`
> `MANGO,`
> `ORANGE,`
> `PIZZA,`
> `BURGER,`
> `CHEESE,`
> `POISION,`
> `ALCOHOL`



## [IN **FoodItem**]

1. Create the following properties:

> `private:`

> `UI::UIElement::ImageView* food_image`

> `sf::Vector2i grid_position`

> `float cell_width`

> `float cell_height`

> `FoodType food_type`
> 
> `public:`
> `static const int number_of_foods = 8`



1. Create `sf::String FoodItem::getFoodTexturePath()` and return the texture path based on `food_type`
2. Create `sf::Vector2f FoodItem::getFoodImagePosition()` and return the screen position of the food.
3. Create `void FoodItem::initializeFoodImage()` and inside it
4. 1. Call `getFoodImagePosition()` & `getFoodTexturePath()` to get `screen_position` and `food_texture_path`
  2. Call `food_image->initialize(food_texture_path, cell_width, cell_height, screen_position)`
  3. Call `food_image->show()`
5. Implement all remaining lifecycle functions
6. Create `FoodType getFoodType()` that returns `food_type`.

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-3-Food-Spawning**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-3-Food-Spawning**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
