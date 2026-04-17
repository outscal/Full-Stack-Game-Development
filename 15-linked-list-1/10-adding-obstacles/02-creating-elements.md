Before starting with obstacles, it's important to understand what elements are and how obstacles fit into this category.

Think of elements as anything that appears in the snake game besides your snake and food.

Like a speed boost powerup, killer time bomb or a wall created by obstacles.



Obstacles are like challenges that make the game trickier. Let's get into the details.



## Obstacles


---

Obstacles are just one of the types of elements you'll introduce, but oh boy, they'll make things interesting.

**Obstacles** are things in a game that make it harder to play.

They can be things that block your way, like **walls** or **rocks**. You have to avoid obstacles to keep yourself alive in the game.



In your game, each obstacle will appear as a black square. 

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_04_2024__10_27_11.png)

***Obstacle in Snake Game***



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_18_2024__09_21_35.png)

***Obstacles in Level 2***



Look at the above image, which shows the obstacles in Level 2 of the Snake game. 



To keep your code clean and organized, you'll manage all element logic separately from the level logic. 

This is where the `ElementService` comes in.



The `ElementService` will handle the creation, management, and interaction of all elements in your game. 

To spawn an element, you'll need two key pieces of information: its type and its position.

 

Currently, the only element type available is '**Obstacle**.' However, more types will be introduced in the bonus assignments.

But what would the architecture of the Element Service look like?



## Element Service architecture


---



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_24_2024__10_47_49.png)

***Element Service Architecture***



The `ElementService` manages elements and their lifecycle. These elements are represented and manipulated using data structures like `ElementData`. 


Take a look at the script to create `ElementData`, where `ElementType` is defined as `OBSTACLE`:

```cpp
#pragma once
#include <SFML/System/Vector2.hpp>

namespace Element
{
    enum class ElementType
    {
        OBSTACLE,
    };

    struct ElementData
    {
        ElementData(ElementType type, sf::Vector2i pos)
        {
            element_type = type;
            position = pos;
        }

        ElementType element_type;
        sf::Vector2i position;
    };
}
```



In the above script:

- You define an enum `ElementType`, where `OBSTACLE` represents an obstacle element.
- You create a `struct ElementData` to manage each element's data. It contains two members: one representing the element's type and another representing its position on the game board.



> **TODO:**`**ElementData**`

> ✅ Create the `ElementData` struct using above script inside the `Element` folder and follow namespace `Element`.



Here's how to create an obstacle in your game:

```cpp
Element::ElementData obstacle(Element::ElementType::OBSTACLE, sf::Vector2i(5, 5));
```

This example creates an obstacle element on the game board at position (5, 5).





**See you in the next section, where we'll discuss more about **`**ElementService**`**.👋🏼**
