# ⏳Quiz

quiz


## Questions


### Q1. In Unity's **Hierarchy** window, you can organize GameObjects in a parent-child relationship. Suppose you have a parent GameObject with a non-uniform scale (e.g., X: 2, Y: 1, Z: 1) and a child GameObject with a uniform scale (X: 1, Y: 1, Z: 1). If you rotate the parent GameObject by 90 degrees around the Y-axis, how does this transformation affect the scale and orientation of the child GameObject in world space?
- The child's scale remains uniform, but its orientation changes due to the parent's rotation.
- The child inherits the non-uniform scale and rotation, causing distortion in its shape. **(correct)**
- The child's world scale becomes non-uniform, and its orientation remains unchanged.
- The child's local scale and orientation remain the same, with no impact from the parent.

### Q2. In the Inspector, some components have a small "lock" icon in the upper right corner. What is the purpose of this lock, and how can it be used to enhance your workflow when working with multiple GameObjects and components?In the Inspector, some components have a small "lock" icon in the upper right corner. What is the purpose of this lock, and how can it be used to enhance your workflow when working with multiple GameObjects and components?
- Locking the Inspector prevents it from updating when other GameObjects are selected, allowing you to drag and drop references into the locked Inspector. **(correct)**
- It secures the component's properties, making them read-only to prevent accidental changes.
- The lock hides the component from the Inspector to declutter the interface.
- - It locks the GameObject's Transform, preventing any movement, rotation, or scaling.

### Q3. The Rotate Tool in Unity provides different rotation handle orientations. When working with nested GameObjects, how does using the Global rotation handle differ from the Local rotation handle in terms of the resulting transformation, and why might this distinction be important when animating objects?
- Global rotation modifies the GameObject's world rotation, affecting its global transformation, which is important for animations that rely on world coordinates.
- Using Global rotation can cause gimbal lock, while Local rotation prevents it due to quaternion calculations.
-  Local rotation changes the object's rotation relative to its parent, preserving hierarchical animations. **(correct)**
- There is no difference; both handles affect the rotation in the same way.

### Q4. The Scale Tool can uniformly or non-uniformly scale GameObjects. What potential issues might arise when non-uniformly scaling a GameObject that has child objects or is part of a prefab, and how does this relate to concepts of inheritance and transformation hierarchies in Unity?
- Scaling a parent GameObject has no effect on its children due to encapsulation principles.
- Non-uniform scaling can cause child objects to inherit distorted scales, leading to rendering artifacts and complicating prefab instances. **(correct)**
- Prefabs automatically adjust to compensate for parent scaling, maintaining their original appearance.
- Non-uniform scaling only affects the collider components, not the visual representation.

### Q5. When using the View Tool (hand icon) in Unity's Scene view, you can navigate around your scene. However, there's a feature called Flythrough mode activated by holding the right mouse button and using WASD keys. How does Flythrough mode enhance scene navigation, and what advantages does it offer when working with large or complex scenes compared to traditional panning and zooming?
- Flythrough mode allows for intuitive first-person navigation, making it easier to traverse and inspect large scenes quickly. **(correct)**
- It locks the camera to predefined paths, limiting navigation but improving performance.
- Flythrough mode provides an orthographic view, which is better for level design but not for inspecting object details.
- It slows down the navigation speed, offering more precision but taking longer to move across the scene.
