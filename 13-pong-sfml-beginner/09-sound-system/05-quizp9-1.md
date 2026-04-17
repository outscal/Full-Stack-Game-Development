# ⏳Quiz

quiz


## Questions


### Q1. The sf::Sound class is suitable for short sound effects, while sf::Music is better for longer audio tracks like background music.
- True **(correct)**
- False

### Q2. What is the main difference between sf::Sound and sf::Music in SFML?
- sf::Sound is used for streaming audio, while sf::Music is for preloaded audio.
- sf::Sound can only play .wav files, while sf::Music can only play .ogg files.
- sf::Sound loads the audio entirely into memory, while sf::Music streams the audio directly from the file. **(correct)**
- sf::Sound and sf::Music serve the same purpose but have different APIs.

### Q3. Why is sf::Music more suitable for background music than sf::Sound?
- It supports higher-quality audio formats like .flac.
- It can play multiple audio tracks simultaneously.
- It streams audio from a file, using less memory compared to loading the entire audio into memory. **(correct)**
- It automatically loops the music when it reaches the end.

### Q4. You want to play a sound effect when a button is clicked. Which sequence of actions is correct?
- Create an sf::Music object, load the sound file, and call play().
- Create an sf::SoundBuffer object, load the sound file, and pass it to an sf::Sound object. Then call play() on the sf::Sound object.
- Create an sf::SoundBuffer object, load the sound file, set it to an sf::Sound object, and call play() on the sf::Sound object. **(correct)**
- Create an sf::SoundBuffer object, load the sound file, and call play() directly on the buffer.
