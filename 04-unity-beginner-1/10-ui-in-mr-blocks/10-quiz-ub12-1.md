# ⏳Quiz

ub12


## Questions


### Q1. In Unity's UI system, what is the primary role of the Event System component?
-  It renders UI elements on the screen.
- It manages input events and dispatches them to UI elements. **(correct)**
- It controls the layout and positioning of UI elements within the Canvas.
- It handles animations for UI elements, such as transitions and fades

### Q2. When working with a Button in Unity, what is the purpose of the OnClick() event, and how can you assign functions to it?
-  OnClick() triggers animations; functions are assigned via animation controllers.
- OnClick() is used for debugging; functions are added through code.
- OnClick() defines what happens when the button is clicked; functions can be assigned in the Inspector or added via scripts using listeners. **(correct)**
- OnClick() is irrelevant for buttons; input is handled elsewhere.

### Q3. Which of the following is a correct method to programmatically add a listener to a Button's OnClick event in Unity?
- button.OnClick += MyFunction;
- button.onClick.AddListener(MyFunction); **(correct)**
- button.RegisterListener(MyFunction);
- button.AddEvent(MyFunction);

### Q4. What is the role of the Canvas Renderer component in Unity's UI system?
- It manages the hierarchy and organization of UI elements.
- It renders UI graphics to the screen, handling the visual appearance of UI elements. **(correct)**
-  It processes input events and dispatches them to UI elements.
- It controls the scaling and resolution of the Canvas.

### Q5. When might you choose to add a listener to a Button's OnClick event via script rather than assigning it in the Inspector, and what are the implications for game design?
- Assigning in the Inspector is faster; adding via script slows down performance.
-  Using scripts avoids typos in function names; Inspector assignments are error-prone.
- There is no difference; both methods are identical in functionality and use cases.
- Adding via script allows for dynamic assignment at runtime, enabling more flexible and modular game design. **(correct)**
