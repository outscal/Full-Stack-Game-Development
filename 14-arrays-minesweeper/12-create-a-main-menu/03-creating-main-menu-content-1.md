Now that we have our `MainMenuManager` class defined, let's bring it to life! 🎨



## Creating the Background


---

First, let's think about what makes a good menu background 🤔

- Visible but not distracting
- It covers the whole window
- Slightly transparent to look professional

Here's how we'll set it up:

First, you need to initialize the variables required to draw the background and buttons:

`MainMenuManager.cpp`

```cpp
    MainMenuManager::MainMenuManager(sf::RenderWindow* window)
    {
        game_window = window;
        initialize();
    }

    void MainMenuManager::initialize()
    {
        initializeBackground();
        initializeButtons();
    }
```

Then, you can start by initializing the background:

`MainMenuManager.cpp`

```cpp
void MainMenuManager::initializeBackground() {
    if (!background_texture.loadFromFile(background_texture_path)) {
        std::cerr << "Failed to load background texture" << std::endl;
        return;
    }
    background_sprite.setTexture(background_texture);
    background_sprite.setColor(sf::Color(255, 255, 255, background_alpha));
}
```



Now that you have initialized the background, let's initialize the play and quit buttons.

 

## Adding Menu Buttons


---

Firstly, you need to initialize the play and quit buttons with a certain dimension and at a certain position.

Then register the callbacks for both the buttons.

You also need to implement the `getButtonPosition` function.



`MainMenuManager.cpp`

```cpp
void MainMenuManager::initializeButtons() {
    play_button = new Button(play_button_texture_path,
                           getButtonPosition(0.f, play_button_y_position),
                           button_width, button_height);

    quit_button = new Button(quit_button_texture_path,
                           getButtonPosition(0.f, quit_button_y_position),
                           button_width, button_height);

    registerButtonCallbacks();
}

sf::Vector2f MainMenuManager::getButtonPosition(float offsetX, float offsetY) {
    float x_position = (game_window->getSize().x - button_width) / 2.0f + offsetX;
    float y_position = offsetY;
    return sf::Vector2f(x_position, y_position);
}
```



> **TODO**: 
> ✅ Implement background and buttons initialization in `MainMenuManager.cpp`.
> ✅ Run the code to make sure that there are no errors



Next is the registration and the implementation of the callback functions.



## Making the Buttons Work


---

Now, what should happen when buttons are clicked? 🤔

- Play button starts the game
- Quit button closes the game
- Both should play a sound for feedback

First, let's connect buttons to their actions:

`MainMenuManager.cpp`

```cpp
void MainMenuManager::registerButtonCallbacks() {
		play_button->registerCallbackFunction([this](UIElements::MouseButtonType buttonType)
		    {
		        playButtonCallback(buttonType);
		    }
		);
		quit_button->registerCallbackFunction([this](UIElements::MouseButtonType buttonType)
		    {
		        quitButtonCallback(buttonType);
		    }
		);
}
```



Then let's implement the callback functions:

You just need to play the button click sound and switch the game state to Gameplay or Exit:

You can do this on your own 💪🏼



> **TODO**: 
> ✅ Implement `playButtonCallback` and `quitButtonCallback` functions in `MainMenuManager.cpp`.
> ✅ Run the code to make sure that there are no errors in the code.



Solution.

`MainMenuManager.cpp`

```cpp
void MainMenuManager::playButtonCallback(MouseButtonType mouse_button_type) {
    if (mouse_button_type == MouseButtonType::LEFT_MOUSE_BUTTON) {
        Sound::SoundManager::PlaySound(Sound::SoundType::BUTTON_CLICK);
        GameLoop::setGameState(GameState::GAMEPLAY);  // Start the game
    }
}

void MainMenuManager::quitButtonCallback(MouseButtonType mouse_button_type) {
    if (mouse_button_type == MouseButtonType::LEFT_MOUSE_BUTTON) {
        Sound::SoundManager::PlaySound(Sound::SoundType::BUTTON_CLICK);
        GameLoop::setGameState(GameState::EXIT);  // Quit the game
    }
}
```





Then, you need to implement the update and render methods.



## Lifecycle Functions


---

We need to keep our menu updated and visible:



`MainMenuManager.cpp`

```cpp
void MainMenuManager::render() {
    game_window->draw(background_sprite);
    if (play_button) play_button->render(*game_window);
    if (quit_button) quit_button->render(*game_window);
}

void MainMenuManager::update(EventPollingManager eventManager) {
    play_button->handleButtonInteractions(eventManager, *game_window);
    quit_button->handleButtonInteractions(eventManager, *game_window);
}
```



Then, the lifecycle functions of the GameLoop class.



## Connecting to the Game


---

Let's integrate our menu with the game loop:



> **TODO**: 
> ✅ Implement the render and update methods in `MainMenuManager.cpp`. 
> ✅ Include the `MainMenuManager.h` file in the `GameLoop.h` file and create its object.
> ✅ Update the lifecycle functions to manage the `main_menu_manager` object.



Solution.

> **Summary📃**
> Here's what is added in the `GameLoop.cpp` file:
> 🔸 **Initialization:** Created and initialized in `GameLoop::initialize()`.
> 🔸 **Memory Management:** Allocated in `initialize()` and deleted in `~GameLoop()`.
> 🔸 **Updating:** `update()` is called in MAIN_MENU state to handle interactions.
> 🔸 **Rendering:** `render()` is called in MAIN_MENU state to draw the UI.



`GameLoop.cpp`

```cpp
void GameLoop::initialize()
{
    // Create Managers:
    window_manager = new GameWindowManager();
    game_window = window_manager->getGameWindow();
    event_manager = new EventPollingManager(game_window);

    splash_screen_manager = new SplashScreenManager(game_window);
    //initialize the main menu
    main_menu_manager = new MainMenuManager(game_window);
    gameplay_manager = new GameplayManager();
    
    // Initialize Sounds:
    Sound::SoundManager::Initialize();
    Sound::SoundManager::PlayBackgroundMusic();

    // Initialize Time:
    Time::TimeManager::initialize();
}

GameLoop::~GameLoop()
{
    delete window_manager;
    delete event_manager;
    delete splash_screen_manager;
    delete main_menu_manager; //delete main menu manager	
    delete gameplay_manager;
}

void GameLoop::update()
{
    Time::TimeManager::update();
    event_manager->update();
    window_manager->update();

    switch (current_state)
    {
    case GameState::SPLASH_SCREEN:
        splash_screen_manager->update();
        break;
    case GameState::MAIN_MENU:
        main_menu_manager->update(*event_manager); //update the main menu
        break;
    case GameState::GAMEPLAY:
        gameplay_manager->update(event_manager, game_window);
        break;
    case GameState::EXIT:
        game_window->close();
        break;
    }
    
}


void GameLoop::render()
{
    game_window->clear();
    window_manager->render();

    switch (current_state)
    {
    case GameState::SPLASH_SCREEN:
        splash_screen_manager->render();
        break;
    case GameState::MAIN_MENU:
        main_menu_manager->render(); //render the main menu
        break;
    case GameState::GAMEPLAY:
        gameplay_manager->render(*game_window);
        break;
    }
    
    game_window->display();
}
```





Lastly, you need to transition from `SplashScreen` to the `MainMenu` state instead of the Gameplay state

`SplashScreenManager.cpp` 

```cpp
    void SplashScreenManager::drawLogo()
    {
        elapsed_time = elapsed_time + Time::TimeManager::getDeltaTime();
        
        if (elapsed_time < logo_animation_duration)
            game_window->draw(logo_sprite);
        else
        {
            elapsed_time = 0.0f;
            GameLoop::setGameState(GameState::MAIN_MENU); // transition to Main Menu state
        }
    }
```



> **TODO**: 
> ✅ Play the game



Your game is now complete with a proper Main Menu! 🎮

Congratulations!!!🎉🎉

You have created another game while learning a new data structure!💪🏼
