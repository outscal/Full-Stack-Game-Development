In this lesson, you’ll learn about some important properties of the `RectTransform` component: Anchors, Pivot, and Anchor Presets.



## Anchors


---



Anchors define how UI elements stick to their parent container.



They have four values:

- Min X, Min Y: Bottom-left anchor point
- Max X, Max Y: Top-right anchor point



Values range from 0 to 1, representing percentage of parent's width/height.



Here's what those values mean:

- **0**: Represents the starting point of the parent's width or height (e.g., left side or bottom).
- **1**: Represents the ending point of the parent's width or height (e.g., right side or top).



So, an anchor of **Min(0.5, 0.5) Max(0.5, 0.5)** would place the UI element in the center of its parent, while **Min(0, 0)** **Max(0, 0)** would place it in the bottom-left corner, and **Min(1, 1)** **Max(1, 1)** in the top-right corner.



Here’s another example:

- Min X = 0, Max X = 1: Element stretches full width
- Min Y = 0, Max Y = 0: Element sticks to bottom



## Pivot: The Rotation and Scaling Center


---



Pivot is the point around which UI elements rotate and scale.

- (0, 0) is bottom-left
- (1, 1) is top-right
- (0.5, 0.5) is center

You can choose your pivot based on how you want your element to transform.



## Anchor Presets: Quick UI Positioning


---



Anchor Presets are pre-defined anchor and pivot combinations.

They're great for quickly positioning UI elements.

You can use the presets to position the level number correctly!



## Moving the Level Number UI


---



Where do you think the level number can be placed?🤔 Top-Left?

Let's move our Level Number to the top-left:

1. Select `Level_Text` in `Hierarchy`
2. In `RectTransform`, click the square `Anchor Presets` icon.
3. Hold the `Alt` key and choose `Top-Left` preset.
4. Adjust position if needed using `Pos X` and `Pos Y`




[Watch video](https://www.loom.com/embed/897636fe4bcf449fb3777771857e5bac?sid=342d02a2-15f3-482a-969f-a606c843e976)





> TODO: 
> ✅ Position the `Level_Text` to the top-left of the `Level_Panel`



You have successfully created a complete UI!

I know, it’s just a text.

But, don’t worry 😌

In the next lesson, you’ll also add an Image and Buttons!
