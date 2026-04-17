Remember our fullscreen window trap from the last lesson? 😅

How to quit the game? 🤔

Well, closing the game or quitting the game is an Event. But before implementing it, you need to understand what events are and how they work.



## Understanding Events


---



Think about your favorite game for a moment:

- How does it know when you press a button?
- How does it respond to your mouse clicks?
- How does it detect when you resize the window?

These are all events! But what exactly are they?

Events are like messages that tell your game:

- "Hey, the player pressed a key!"
- "Someone clicked the mouse!"
- "The window is being resized!"



> 📖 🎮 **GAME DEV DICTIONARY** 
> ***Events***: "Actions or occurrences triggered by player actions (like pressing keys or clicking buttons) that your game needs to handle."



## How Do Events Work?


---



Before you code, let's understand the event system:

Imagine a line of people waiting at a game store:

- Each person (event) waits their turn
- They enter one by one (queue)
- First come, first served (order)

The store manager (your game) has two important jobs:

**Event Queue** (The Line Outside):

- Players line up to buy games (events waiting to be processed)
- New customers join the back of the line (new events occur)
- Everyone stays in order (event sequence maintained)

**Event Polling** (The Manager's Actions):

- Manager opens the door and checks the line (polls for events)
- Helps one customer at a time (processes each event)
- Keeps checking until everyone is served (event loop)



This is exactly how SFML handles events!

Let’s create an `EventManager` for Pong!



## Creating Event Manager


---



> **TODO**: Project Structure 
> ✅Create new folder: `Header/Event` and `Source/Event` 
> ✅Create `EventManager.h` in `Header/Event` 
> ✅Create `EventManager.cpp` in `Source/Event`



Let’s start with the header file.

Think about what does an Event Manager needs🤔

- A function to handle all incoming events: `pollEvents`
- A function to check if a key(like: Esc) is pressed: `isKeyPressed`



`EventManager.h`

```cpp
// EventManager.h
#pragma once
#include <SFML/Graphics.hpp>
using namespace sf;

namespace Event {
    class EventManager {
    public:
        void pollEvents(RenderWindow* game_window); // Process all events
        bool isKeyPressed(sf::Keyboard::Key key);   // Check specific key
    };
}
```



> 💡**ProTip**: 
> `**sf::Keyboard**` is a class in SFML that provides real-time access to the keyboard's state. It has a `key` enum and functions like `isKeyPressed` to track the state of different keys in the keyboard.



Now, you need to implement these functions to manage events!



## Implementing Event Manager


---



Let's start with our poll events function:

Think about what `pollEvents()` function needs to do:

- Create an `Event` object to store the current event,
- Check the queue(`game_window->pollEvent()`) until all events are processed

`EventManager.cpp`

```cpp
void EventManager::pollEvents(RenderWindow* game_window) {
        sf::Event event;
        while (game_window->pollEvent(event)) {

        }
    }
```

Now, what events should you handle first? 🤔

- Window closing (X button)
- Keyboard input (Escape key)
- Other window events

Let's add window close handling first:

- Detects when X button is clicked
- Closes the game window



`EventManager.cpp`

```cpp
void EventManager::pollEvents(RenderWindow* game_window) {
        sf::Event event;
        while (game_window->pollEvent(event)) {
						// Handle window close event
            if (event.type == sf::Event::Closed) {
                game_window->close();
            }
        }
    }
```



> 💡**ProTip**: 
> `**sf::Event**` is a class in SFML that encapsulates details about system events such as key presses, mouse movements, or window actions.



Now, you need to check for the Escape key press.

But, for that you need to implement the `isKeyPressed()` method.

`EventManager.cpp`

```cpp
    bool EventManager::isKeyPressed(sf::Keyboard::Key key) {
		// Detect if a specific key is pressed
        return sf::Keyboard::isKeyPressed(key);
    }
```

Finally, add escape key handling:

`EventManager.cpp`

```cpp
void EventManager::pollEvents(RenderWindow* game_window) {
        sf::Event event;
        while (game_window->pollEvent(event)) {
						// Previous Code

						// Check for Escape key
            if (isKeyPressed(sf::Keyboard::Escape)) {
                game_window->close();
            }
        }
    }
}
```



> **TODO**: `EventManager.cpp` 
> ✅ Implement `pollEvents(RenderWindow* game_window)` function. 
> ✅ Implement `isKeyPressed(sf::Keyboard::Key key)` function.



Your event manager is ready!

Lastly, you need to check for the events in the `main()` function.



## Bringing It All Together


---



Let's update our main function:



> 💡 **PROTIP**: 
> Always process events before rendering! This ensures your game responds immediately to player input.



`main.cpp`

```cpp
#include "Core/GameWindowManager.h"
//Add event manager's header file
#include "Event/EventManager.h"

int main() {
    //previous code
    //Create an object of event manager
    Event::EventManager eventManager;

    //previous code

    while (gameWindowManager.isGameRunning()) {
		    //Check and Process Events
        eventManager.pollEvents(gameWindowManager.getGameWindow());
        gameWindowManager.render();
    }

    return 0;
}
```



> **TODO**:  Main Program Update 
> ✅Include EventManager in main.cpp 
> ✅Add event polling to main() function. 
> ✅Test escape functionality



Great, your game is not frustrating now!😌

In the next lesson, you'll explore how to handle mouse input.
