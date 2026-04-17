# ⏳Quiz

quiz


## Questions


### Q1. The std::chrono library can measure delta time by taking the difference between two ____.
- std::time_point objects **(correct)**
- std::duration objects
- std::thread objects
- std::timer objects

### Q2. What does the following code do?

#include <chrono>

auto lastTime = std::chrono::high_resolution_clock::now();

while (gameRunning) {
    auto currentTime = std::chrono::high_resolution_clock::now();
    std::chrono::duration<float> deltaTime = currentTime - lastTime;
    lastTime = currentTime;

    std::cout << "Delta Time: " << deltaTime.count() << " seconds" << std::endl;
}
- Prints the elapsed time since the application started.
- Prints the frame rate of the application.
- Prints the time elapsed between the last frame and the current frame (delta time). **(correct)**
- Causes a runtime error because std::chrono::duration is not compatible with std::chrono::high_resolution_clock.

### Q3. Why might using std::chrono::system_clock for delta time cause issues in your game loop?
- It doesn’t support measuring nanoseconds, which are critical for delta time.
- It’s less precise than std::time.
- It requires manual synchronization with the graphics card.
- It can be adjusted by the operating system, causing jumps or inconsistencies in time measurements. **(correct)**

### Q4. What will happen if you calculate delta time like this?

#include <chrono>
auto currentTime = std::chrono::high_resolution_clock::now();
std::chrono::duration<float> deltaTime = currentTime.time_since_epoch();
- Delta time will correctly represent the time elapsed since the last frame and will be updated every loop.
- Delta time will be the total time elapsed since the program started running.
- Delta time will represent the time elapsed since a fixed point in time defined by system, making it unsuitable for frame-to-frame calculations. **(correct)**
- The code will cause a runtime error because time_since_epoch() cannot be used with std::chrono::high_resolution_clock.
