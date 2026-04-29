![placeholder](//outscal.github.io/Full-Stack-Game-Development/images/280bb6fd05c62af7.png)

<!-- image unavailable: PROJECT ARCHITECTURE -->

PROJECT ARCHITECTURE



> **IMPORTANT:** Similar architecture will be used throughout the C++ based projects. So, it is important to understand it.



Let’s break down this diagram.

### What are Services?


---



A service is responsible for handling a specific set of functions. A *‘service’* refers to a module that provides a set of functionality. A service can consist of multiple classes.

In the `***main***` branch, you have the following services:

<!-- image unavailable: s_Services in Project Setup.png -->

![ ](//outscal.github.io/Full-Stack-Game-Development/images/21e373d6988b0ce0.png)



1. **Game Service:** Manages the main lifecycle of the game. It handles different states like showing the Main Menu, Gameplay or Credits. Game Service triggers the lifecycle methods that are used by multiple classes throughout the game.
2. **Event Service:** Handles events such as Game Quit and Mouse Clicks, which are then utilized by other classes throughout the game.
3. **Graphic Service:** Every visual component on the screen is handled by Graphic Service.
4. **Sound Service:** It is responsible for playing all the sounds in the game.
5. **UI Service:** Manages all UI Controllers and the rendering of the user interface.



### Lifecycle Methods


---



Every entity in a game goes through some critical milestones:



<!-- image unavailable: Birth-Life-Death.png -->

![Birth-Life-Death](//outscal.github.io/Full-Stack-Game-Development/images/a04ec4ccea37df7f.png)



You will handle these milestones with *Lifecycle methods*

<!-- image unavailable: Lifecycle Methods.png -->

![Lifecycle Methods](//outscal.github.io/Full-Stack-Game-Development/images/5bccdb786271b375.png)





`**Constructor**` and `**Destructor**`**:** They play an important role in the lifecycle of an object of any class. They are handled by C++ itself.

`**initialize()**`**:** It’ll be used to assign initial values to properties and make the object ready to use.

`**update()**`**:** It handles the *‘functionalities’* that need to be called every frame.

`**render()**`**:** It displays the visual components of a class on screen. It is called on every frame.

Throughout the C++ based courses, whenever it is mentioned to implement Lifecycle methods, you should implement these methods.

Here is an example:



**Header File** (click here)

```cpp
class SampleClass {
public:
    SampleClass();  // Default constructor
    ~SampleClass(); // Destructor

    void initialize(); // To be called when the object is created
    void update();     // To be called on every frame
    void render();     // To be called on every frame
};
```



Source File (click here)

```cpp
#include "SampleClass.h"

SampleClass::SampleClass() {
    // SampleClass's default constructor
}

SampleClass::~SampleClass() {
    // SampleClass's destructor
}

void SampleClass::initialize() {
    // To be called when the object is created
}

void SampleClass::update() {
    // To be called on every frame
}

void SampleClass::render() {
    // To be called on every frame
}
```





You can leave the methods empty as they’ll be implemented on the go.

It is okay if lifecycle methods are left empty, especially in the early stage of development.

Unused methods can always be deleted while cleaning the code at the end of development.



### How are lifecycle methods called?


---



`Constructors` and `Destructors` are part of C++, so they are automatically called by the compiler.

For the rest of the three functions:

Game Service is responsible for calling these.

`update()` and `render()` are called in `Main.cpp`

`initialize()` is called in Game Service’s `ignite()` which is also called in `Main.cpp`

Game Service in turn triggers the respective functions in `ServiceLocator.cpp` and Service Locator triggers these functions for all services.



### Service Locator


---



Handling all services in `GameService.cpp` would create a messy code and violate SRP. So we have a Service Locator.

It creates the services and triggers their lifecycle functions too.

It also helps different services access each other.



## UI


---



![UI_Overview](//outscal.github.io/Full-Stack-Game-Development/images/e2c22d08f429f3c8.png)



A lot of UI files in the project are not mentioned in the architecture yet.

We'll discuss those UI files in the next section.
