# Creating Random Values in C++


---



Hey there, aspiring game dev! Picture this: you're crafting an epic game with diverse elements. To add unpredictability, you'll need random values! Random numbers add unpredictability, influencing various aspects like enemy behavior, loot drops, or map generation. 

In C++, you can create random numbers within a specific range using the `rand()` function. But wait, there's more to it than just `rand()`!

To understand it, lets have a look at how computers generate random numbers:



True randomness, found in natural phenomena like radioactive decay or atmospheric noise, embodies genuine unpredictability beyond human comprehension.

However, in the digital realm, achieving true randomness remains an impossible task. Instead, what computers offer is **pseudo-randomness **— numbers that appear to be random but originate from **deterministic algorithms**. This deterministic nature means that computer-generated randomness follows **specific sequences**, starting from an initial state or **seed value**.



Despite their appearance of unpredictability, these sequences are deterministic and can be reproduced given the same initial conditions (**Seed Value**). So whenever you call `rand()` function in C++, your computer will return you a number from a sequence of numbers that has been generated using a seed value. You can use `srand()` method to generate a new sequence of pseudo-random numbers by giving a seed value manually to the compiler. It initializes the random number generator with a seed value:

```cpp
srand(time(0)); // Seeds the random number generator
```

Providing `time(0)` as an argument to `srand()` ensures a unique seed value based on the current time. This uniqueness generates different sequences of random values. If the same seed value is provided, the sequence of numbers generated will be same always.



Example Code:

```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>

int main() {
    srand(time(0)); // Seeds the random number generator with current time

    // Generating random numbers within a specific range (1 to 10)
    int min = 1, max = 10;
    int randomNumber = min + (rand() % (max - min + 1));

    std::cout << "Random Number: " << randomNumber << std::endl;
    return 0;
}
```
