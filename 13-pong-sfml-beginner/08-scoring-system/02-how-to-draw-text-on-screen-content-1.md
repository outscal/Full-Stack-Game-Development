Before you create a scoreboard, let's understand something interesting:

How to display text using SFML?

Think about it:

- Every letter you see is an image
- These images come from something called a *font*
- Fonts tell the computer how to draw each letter



## Setting Up Scoreboard


---



You'll need a separate `UIService` class for displaying the score!

Add the header and source file in a separate `Header/UI` and `Source/UI` folders respectively.



Let's now start setting up the scoreboard!

First, you need a font:

`UIService.h`

```cpp
private:
    Font font;
    Text left_score_text;

    string texture_path = "Assets/Fonts/Aloevera-OVoWO.ttf";
```

*Why do we need both Font and Text?*

- Font → The design blueprint
- Text → The text displayed on the game window

Setting up our text properties:

`UIService.h`

```cpp
    private:
    int font_size = 40;
    Color font_color = Color::White;
    string initial_string = "00";

    float left_score_postion_x = 570.0f;
    float left_score_postion_y = 30.0f;
    
    float right_score_position_x = 670.0f;
    float right_score_position_y = 30.0f;
    
		int player1_score = 0;
```

Now, you need to display the text!



> **TODO** 
> ✅In `Header/UI` create the `UIService.h` file. 
> ✅In `Source/UI` create the `UIService.cpp` file. 
> ✅Setup the properties for `left_score` and `right_score`.



## Creating Scoreboard


---



Let's load our font:

`UIService.cpp`

```cpp
void UIService::loadFontTexture()
{
    font.loadFromFile(texture_path);
}
```

Now that the font is loaded, you need to set the properties of the text.

`UIService.cpp`

```cpp
void UIService::createLeftScoreText()
{
    left_score_text.setFont(font);
    left_score_text.setString(initial_string);
    left_score_text.setCharacterSize(font_size);
    left_score_text.setFillColor(font_color);
    left_score_text.setPosition(left_score_postion_x, left_score_postion_y);
}
```

*Notice how we:*

- Set the font first (text needs a font to exist!)
- Define the initial content
- Make it readable with size and color
- Position it where players can see it



> **TODO** In `UIService.cpp`
> ✅Implement `loadFontTexture()` 
> ✅Implement `void createLeftScoreText()` function.
> ✅Call these functions in the `UIService()` constructor.



Creating the right score will be an assignment!

Let's display the left score in this lesson.



## Showing the Score


---



Finally, you can now render the score on the game window:

`UIService.cpp`

```cpp
void UIService::render(RenderWindow* game_window)
{
    game_window->draw(left_score_text);
}
```

Then, integrate it with the gameplay manager:

`GameplayManager.h`

```cpp
UIService* ui_service = new UIService;
```

`GameplayManager.cpp`

```cpp
void GameplayManager::render(RenderWindow* game_window)
{
    boundary->render(game_window);
    ball->render(game_window);
    player1->render(game_window);
    player2->render(game_window);
    ui_service->render(game_window);
}
```



> **TODO** 
> ✅In `UIService.cpp` implement the functions to render the score. 
> ✅Call `ui_service->render(game_window)` in `GameplayManager::render()`



The scoreboard looks great, but it's static!

*Next up:* You'll make those numbers change when players score! 💯
