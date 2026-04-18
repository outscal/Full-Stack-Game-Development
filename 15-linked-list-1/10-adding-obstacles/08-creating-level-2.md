**Bringing the OG Snake Experience to Life! 🐍**



It's time to replicate the classic OG snake level 2 in your game. 

Get ready for some fun, some challenges, and a lot of snake nostalgia! 



First, let's take a look at what you're aiming for:

![ ](//outscal.github.io/Full-Stack-Game-Development/images/b572cff86cbc4898.png)

***Level 2 of the Game***

Looks familiar, right? You're going to recreate this!



## placing level 2 obstacles


---

To place obstacles correctly, let's break down the grid:

Imagine your game grid is a beautiful checkerboard. You'll place obstacles based on their positions, using `(x, y)`  = `(col, row)` coordinates. 



![Image](//outscal.github.io/Full-Stack-Game-Development/images/5f75d657216ce4db.png)

***Level Grid***



Let's visualize the screen:

![Image](//outscal.github.io/Full-Stack-Game-Development/images/099870b0eb5c32a9.png)

***Level Divided in Grid***

*(Double-click the image for better view)*



The border part is excluded from the screen for levels, so you'll place obstacles only in the playable area.



Your game screen is divided into a grid of dimensions `**[50, 28]**` excluding the border part. 

So, the part which is required for the level will start at `**(0,0)**` and end at `**(49,27)**` inside the playable area.



**Obstacle Positions:**

Let's break down where each obstacle will be placed:

- **Top-Left Corner**: Obstacles starting at `(1, 1)`
- - You will place obstacles at `(1, 1)`, `(2, 1)`, `(3, 1)`, `(1, 2)`, `(1, 3)`
- **Top-Right Corner**: Obstacles starting at `(48, 1)`
- - You will place obstacles at `(48, 1)`, `(48, 2)`, `(48, 3)`, `(47, 1)`, `(46, 1)`
- **Bottom-Left Corner**: Obstacles starting at `(1, 26)`
- - You will place obstacles at `(1, 26)`, `(1, 25)`, `(1, 24)`, `(2, 26)`, `(3, 26)`
- **Bottom-Right Corner**: Obstacles starting at `(48, 26)`
- - You will place obstacles at `(48, 26)`, `(48, 25)`, `(48, 24)`, `(47, 26)`, `(46, 26)`
- **Center Bars**: Positioned at the top and bottom center parts of the grid
- - Center-Top Bar: Obstacles from `(21, 11)` to `(29, 11)`
  - Center-Bottom Bar: Obstacles from `(21, 15)` to `(29, 15)`



Now, code to draw level 2.



> **TODO: Update **`**LevelModel.h**`

> ✅Set up the `level_two_element_list`



Click here to see Level's Obstacle position in `LevelModel.h````cpp
std::vector<Element::ElementData> level_one_element_list = {};

std::vector<Element::ElementData> level_two_element_list = 
{
    //TOP-LEFT
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(1, 1)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(2, 1)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(3, 1)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(1, 2)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(1, 3)),

    //TOP-RIGHT
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(48, 1)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(48, 2)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(48, 3)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(47, 1)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(46, 1)),

    //BOTTOM-LEFT
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(1, 26)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(1, 25)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(1, 24)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(2, 26)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(3, 26)),

    //BOTTOM-RIGHT
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(48, 26)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(48, 25)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(48, 24)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(47, 26)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(46, 26)),

    //CENTER-TOP-BAR
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(21, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(22, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(23, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(24, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(25, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(26, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(27, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(28, 11)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(29, 11)),

    //CENTER-BOTTOM-BAR
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(21, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(22, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(23, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(24, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(25, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(26, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(27, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(28, 15)),
    Element::ElementData(Element::ElementType::OBSTACLE, sf::Vector2i(29, 15)),
};
```



**Run your Game!!**

***You must see this screen in Level 2***

![ ](//outscal.github.io/Full-Stack-Game-Development/images/b572cff86cbc4898.png)



Voilà! You should see obstacles in your game, even though they won't be interactive just yet. 



Ready to take your game to the next level? 

In the coming chapter, you'll be making these obstacles interactive and spawning food items! 



**See you in the next chapter! 👋🏼**
