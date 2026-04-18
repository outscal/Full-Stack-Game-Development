In this chapter, you'll be setting the groundwork to see a Body Part on screen, meaning that much of the work will revolve around ImageView (`bodypart_image`).



![BodyPart Function Call Tree](/Full-Stack-Game-Development/images/54a547c39d422642.png)

`**BodyPart**`** Function Call Chart**



Let's create the basic functions first, 
We do fast things first!



> **TODO: **`**BodyPart**` 
> ✅ Create empty lifecycle functions, apart from `initialize()` and `update()` 
> ✅ Create `createBodyPartImage()` and initialize the `bodypart_image` with the `new` keyword and call this function inside the constructor
> ✅ Set `grid_position` to `(0,0)` inside inside the constructor
> ✅ Call `bodypart_image->render()` inside `render()` 
> ✅ Create `void destroy()` and delete the `bodypart_image` inside it, and call it inside the destructor



**Done?**

Let's do more!



## Initializing The Body Part


---

To initialize the body part, you need its width, height and you also need its initial position and direction.

You can take all the values inside the `initialize()` function 



> **TODO: **`**BodyPart**` 
> ✅ Create `void BodyPart::initialize(float width, float height, sf::Vector2i pos, Direction dir)`
> ✅ Set the values of the below properties based with the values taken in parameters

> `bodypart_width`
> `bodypart_height`
> `direction`
> `grid_position`



You have taken the information but still, the image is not initialized, you've done it a thousand times so here is the code, enjoy!



```cpp
void BodyPart::initializeBodyPartImage()
{
	bodypart_image->initialize(Config::snake_body_texture_path, bodypart_width, bodypart_height, getBodyPartScreenPosition());
	bodypart_image->setOriginAtCentre();
}
```



Are you confused about what is `setOriginAtCentre()`?

This function just sets the origin of the image to its centre, by default the origin is on the top-left of the image.

Think about why you set the origin to the centre.

And if you don't realise the answer, think again.😊



> **TODO: **`**BodyPart**` 
> ✅ Create `initializeBodyPartImage()` like in the above code and call it inside the `initialize()`



Click here to see `BodyPart`'s `initialize()`

```cpp
void BodyPart::initialize(float width, float height, sf::Vector2i pos, Direction dir)
{
	bodypart_width = width;
	bodypart_height = height;
	direction = dir;
	grid_position = pos;

	initializeBodyPartImage();
}
```





## Updating the Body Part


---

We'll discuss it in later sections.



In this next section, you'll create the logic to position and rotate the body part.

**See you there!👋🏼 **
