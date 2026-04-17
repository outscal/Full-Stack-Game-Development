*How do you measure time in your game?*

Let's think about different kinds of clocks:

- Your wall clock → Can be changed manually
- Your system clock → Changes with time zones
- A stopwatch → Just keeps ticking forward

In C++, we have something similar to that stopwatch: `std::chrono::steady_clock`



> 📖 🎮 **GAME DEV DICTIONARY **
> ***steady_clock***: "`**std::chrono::steady_clock**` is one of the clock types provided by the C++ `**<chrono>**` library. 
> It is designed to represent a clock that guarantees that time will only move forward(like the stopwatch) and will not jump backward(like a regular system clock)." 
> The units of time (e.g., nanoseconds, microseconds) are system-dependent but can be retrieved using `std::chrono::duration`.



Now, using the `steady_clock`, you can store the point at which a frame starts and also when the frame ends.



Click here to see the folder structure.

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6675375f717323b2671e88fc/12_20_2024__13_11_11.png)

**Folder Strtucture**





`TimeService.h`

```cpp
#pragma once
#include <chrono>

namespace Utility
{
    class TimeService
    {
	    private:
        std::chrono::steady_clock::time_point previous_time;
        float delta_time;
		}
}

```

`**std::chrono::steady_clock::time_point**` represents a point in time from a `steady_clock`.

Then, you need the functions for calculating and updating delta time and lifecycle functions.

`TimeService.h`

```cpp
		private:
		void updateDeltaTime();
		float calculateDeltaTime();
		void updatePreviousTime(); // Update previous_time to the current time

	public:

		void initialize();
		void update();
		float getDeltaTime();
```



> **TODO** 
> ✅In `Header/Utility` create `TimeService.h` 
> ✅Create all the function and variable declarations.



It’s time to implement these functions!



## Initializing Time Service


---



Before measuring time differences, you need a starting point:

`TimeService.cpp`

```cpp
void TimeService::initialize()
{
    previous_time = std::chrono::steady_clock::now();
    delta_time = 0;
}
```

Now, you need to calculate the delta time.



## Calculating Delta Time


---

Now, you can not just store the time difference in delta time. You need to convert it into time units(microseconds).

You can use `**std::chrono::duration_cast**` for this. `**duration**`** **is the time difference between time points and `**duration_cast**`** **is used to convert the difference to microseconds, seconds, or other time units.

Then `**count()**` extracts the raw numerical value of the duration, in this case, the number of microseconds.



`TimeService.cpp`

```cpp
float TimeService::calculateDeltaTime()
{
    // Get time difference in microseconds
    int delta = std::chrono::duration_cast<std::chrono::microseconds>(
        std::chrono::steady_clock::now() - previous_time).count();

    // Convert to seconds
    return static_cast<float>(delta) / 1000000.0f;
}


```



- Time is measured in microseconds.
- Convert it to seconds for easier use.



## Updating Time


---

Now, when the delta time between two frames is calculated, 
you finally need to update the previous time 
and then again calculate the delta time between the next two frames.

.

`TimeService.cpp`

```cpp
void TimeService::updateDeltaTime()
{
    delta_time = calculateDeltaTime();
    updatePreviousTime();
}

void TimeService::updatePreviousTime()
{
    previous_time = std::chrono::steady_clock::now();
}

void TimeService::update()
{
		updateDeltaTime();
}
```

Lastly, you need a getter function for other classes to access delta time.

Other parts of our game need to know about time:

`TimeService.cpp`

```cpp
float TimeService::getDeltaTime()
{
    return delta_time;
}
```



> **TODO** 
> ✅Create `TimeService.cpp` 
> ✅Implement all the functions



Finally, `delta_time`(time difference between two frames) is ready!💪🏼

In the next lesson, you’ll use it to make the paddle and ball movement frame rate independent!
