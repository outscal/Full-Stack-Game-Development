# ⏳Quiz

 ub13


## Questions


### Q1. What is the primary purpose of the DontDestroyOnLoad method in Unity?
- It prevents a GameObject from being destroyed when the application quits.
- It locks a GameObject's position and rotation, preventing accidental changes during gameplay.
- It keeps a GameObject and its children intact when loading a new scene, allowing persistent data or behaviors. **(correct)**
- It duplicates a GameObject across all scenes, creating copies in each loaded scene.

### Q2. When using DontDestroyOnLoad, which potential issue must you consider to prevent unintended behavior in your game?
- It disables the GameObject's ability to interact with new scene elements, isolating it.
- It can cause memory leaks if overused; freeing up memory manually is necessary.
- Multiple instances of the same GameObject may persist across scenes, leading to duplicates and conflicts. **(correct)**
- It resets all component values to default, causing loss of game state information.

### Q3. Which of the following correctly describes how the AudioSource component works in Unity?
- It plays back audio clips attached to it, allowing control over volume, pitch, and spatial settings. **(correct)**
- It processes audio effects like reverb and echo, applied globally to all sounds.
- It records audio input from the user's microphone for in-game communication.
-  It manages the game's audio settings, such as master volume and audio device selection.

### Q4. How can you play an audio clip attached to an AudioSource component exactly once, ensuring it doesn't loop?
- Set the loop property to true and call Play().
- Set the loop property to false and call Play(). **(correct)**
- Use PlayOneShot(audioClip) with the loop property enabled.
- Adjust the priority to prevent looping and call Play().

### Q5. You use FindObjectOfType<MyComponent>() to locate a component in your scene, but it returns null even though the component exists. What could be a possible reason for this, and how does understanding Unity's object hierarchy help you resolve the issue?
- The component script has syntax errors; FindObjectOfType cannot locate faulty scripts.
- The GameObject containing the component is inactive; FindObjectOfType does not find components on inactive GameObjects. **(correct)**
- The component is attached to a prefab; FindObjectOfType cannot find components on prefabs.
- There are multiple components of the same type; FindObjectOfType cannot determine which one to return.
