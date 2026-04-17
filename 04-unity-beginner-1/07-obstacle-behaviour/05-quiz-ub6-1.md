# ⏳Quiz

ub6


## Questions


### Q1. When you rotate a sprite by adjusting its Transform.rotation each frame, inconsistent rotation speeds may occur on different devices. What causes this inconsistency, and how does it relate to frame rate dependency?
- Unity's physics engine processes rotations differently across devices.
- Floating-point calculations vary on different CPUs.
- Higher frame rates lead to more updates per second, causing faster rotation—illustrating frame rate-dependent logic. **(correct)**
- Time.deltaTime is inaccurate on some devices.

### Q2. You want a sprite to rotate smoothly at a rate of 120 degrees per second. If your game runs at a constant frame rate of 60 frames per second, how many degrees should the sprite rotate each frame to achieve the desired rotation speed?
- 0.5 degrees per frame
- 2 degrees per frame **(correct)**
- 3 degrees per frame
- 6 degrees per frame

### Q3. When rotating a sprite around a point other than its center, why is it necessary to adjust the sprite's pivot point, and how does this affect the rotation?
- The pivot point doesn't affect rotation; the sprite always rotates around its center.
- Adjusting the pivot point changes the center of rotation, allowing rotation around a different point like an edge. **(correct)**
- Changing the pivot point affects the sprite's scale but not its rotation.
- Pivot points are only relevant for UI elements, not sprites.

### Q4. Why is it important to multiply movement or rotation amounts by Time.deltaTime when applying them in the Update() method?
- To make the movement or rotation faster.
- To make the movement or rotation frame rate independent, ensuring consistency across devices. **(correct)**
- To synchronize physics calculations.
- It's not important; Time.deltaTime has no effect.

### Q5. You want a sprite to rotate exactly 360 degrees over 2 seconds, regardless of frame rate. Why might adding a fixed rotation each frame not achieve this, and how does understanding time-based calculations help implement accurate rotation?
- Fixed increments ignore elapsed time; using rotation speed multiplied by Time.deltaTime ensures consistent rotation over time. **(correct)**
- High frame rates cause over-rotation; using a modulo operation resets rotation.
- Fixed values are too small on high-res displays; adjusting for screen DPI solves the issue.
- Incrementing per frame doesn't consider the sprite's initial rotation; resetting rotation each frame fixes it.
