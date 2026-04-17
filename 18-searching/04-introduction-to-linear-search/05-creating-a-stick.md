Your visualizer is nothing but an algorithm that is being performed on the collection of sticks with some extra logic.

In this lesson, the focus is on creating the Stick. This is an important step because it will form the base for what you will build.



## The role of stick and its collection


---



A Stick in your visualizer is a rectangle shape that holds data related to its height.

The larger the data, the taller the stick.



This data is also related to the target element, which represents a value you are searching for in the algorithm.

In the context of your visualizer, each stick is a static object with a value that you use to represent data visually.

What do you think a static object with a value is? It's nothing but a **structure**.



So, to visualise the stick you need `struct Stick`.

- `struct Stick` represents a single stick.
- It will include a rectangle shape UI element and an integer to store the stick's number.



But only one stick is not enough for the visualization. 

You need a collection of sticks, and for that, you need a Stick MVC that handles all the data, view, and logic.



> ✅**TODO:**

> 

> 1. Inside the `Gameplay` folder, create another folder named `StickCollection`.

> 2. Now, create a file as `stick.h` inside `StickCollection`.

> 3. Create `struct Stick` in the file within nested namespace `Gameplay` and `Collection`.

> 4. Add the following properties in it:
>          `int data;`
>          `UI::UIElement::RectangleShapeView* stick_view;`



Now, a constructor that allows setting up the data for the stick during initialization.



> ✅**TODO**: **In stick.h**

> 

> 1. Create a default constructor for Stick.

> 2. Create a constructor that takes `int data` as a parameter which initializes the `data` as `int` and allocates resources for the `stick_view` pointer.

> 3. Create the destructor to delete the resource, which is the stick view.



Click here to see for struct stick (`stick.h`)```cpp
#pragma once
#include "UI/UIElement/RectangleShapeView.h"

namespace Gameplay
{
    namespace Collection
    {
        struct Stick
        {
            int data;
            UI::UIElement::RectangleShapeView* stick_view;

            Stick() { }

            Stick(int data)
            {
                this->data = data;
                stick_view = new UI::UIElement::RectangleShapeView();
            }

            ~Stick() { delete(stick_view); }
        };
    }
}
```



In the next lesson, you will create a Controller, Model and View for a collection of sticks.

See you there!
