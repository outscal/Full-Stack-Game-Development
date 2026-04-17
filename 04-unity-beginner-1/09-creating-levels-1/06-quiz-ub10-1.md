# ⏳Quiz

ub10


## Questions


### Q1. In Unity, what is the Build Index?
- A numerical identifier assigned to each scene in the Build Settings. **(correct)**
- The total number of Scenes in build settings
- A value representing the game's performance metrics
- A level grouping system

### Q2. When transitioning between scenes in Unity, which method is commonly used to load a new scene, and why must the scene be added to the Build Settings?
-  Use EditorSceneManager.OpenScene(); adding the scene to Build Settings enables runtime editing.
- Use Application.LoadLevel(); including the scene in Build Settings optimizes its loading time.
- Use Resources.Load(); placing the scene in Build Settings reduces memory usage.
-  Use SceneManager.LoadScene(); adding the scene to Build Settings allows it to be included in the build and assigned a Build Index. **(correct)**

### Q3. How does the order of scenes in the Build Settings affect the game, and what happens if a scene is not included in the Build Settings?
- The order sets the sequence for scene transitions; scenes not in Build Settings cannot be loaded at runtime, leading to errors. **(correct)**
- The order affects the quality settings; missing scenes default to low-quality graphics.
- The order determines the layering of audio tracks; excluding scenes mutes the audio.
- The order doesn’t matter; Unity automatically determines the order according to the names of the scenes

### Q4. In Unity, what is the primary role of a Level Manager script within a game project?
- To handle player input.
- To handle scene transitions, control game state. **(correct)**
- To only handle scene transitions.
- To only handle game state
