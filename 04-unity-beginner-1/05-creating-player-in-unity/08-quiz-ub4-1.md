# ⏳Quiz

ub4


## Questions


### Q1. Which MonoBehaviour method in Unity is called only once when the script instance is loaded and is commonly used for initializing variables or setting up references before the game starts?
- Awake() **(correct)**
- Start()
- Update()
- OnEnable()

### Q2. What is the key difference between the Awake() and Start() methods in Unity's script lifecycle?
- Start() is called before Awake().
- Awake() is called once per frame. Start() is called just before the first frame update.
- Awake() is called when the script instance is loaded, Start() is called just before the first frame update. **(correct)**
- There is no difference between them.

### Q3. Why should you use FixedUpdate() instead of Update() for physics-related code?
- FixedUpdate() is called more frequently than Update().
- Update() doesn't work with physics components.
- FixedUpdate() is called at fixed intervals, ensuring consistent physics calculations regardless of frame rate. **(correct)**
- Using FixedUpdate() improves graphical performance.

### Q4. In Unity's Input system, what is the purpose of the Input.GetKeyDown() method, and how does it differ from Input.GetKey() when detecting user input?
- Input.GetKeyDown() returns true as long as the key is held down, while Input.GetKey() returns true only once when the key is pressed.
- Input.GetKeyDown() returns true only on the frame the key is pressed, whereas Input.GetKey() returns true every frame the key is held down. **(correct)**
- Input.GetKeyDown() is used for detecting key releases, while Input.GetKey() detects key presses.
- There is no functional difference between Input.GetKeyDown() and Input.GetKey().

### Q5. How does defining custom Input Axes in Unity's Input Manager enhance your game's input system?
- It automatically optimizes input latency.
- It allows you to map multiple inputs to the same action. **(correct)**
- It generates default controls for your game.
- It restricts the game to use only standardized input devices.

### Q6. What does the method Input.GetButtonDown("Jump") return?
- True every frame the jump button is held down.
- True only on the frame when the jump button is pressed. **(correct)**
- True when the jump button is released.
- True if the jump button has not been pressed.

### Q7. Why are the OnEnable() and OnDisable() methods useful in MonoBehaviour scripts?
- They are required for scripts to compile.
- They handle user input events automatically.
- They allow you to initialize or clean up resources. **(correct)**
- They control the rendering order of GameObjects.
