# **TYPES OF SMART POINTERS**


---

Before we jump into explaining types of smart pointers, let’s revisit smart pointers quickly.



> Smart Pointers are C++ objects that act like regular pointers but are “smart” enough to manage memory automatically. 
> They handle memory allocation and deallocation for you, which can save you from common pitfalls.



C++ Provides three main types of smart pointers:


## Unique Pointer:


---

A `**unique_ptr**` represents exclusive ownership of a dynamically allocated object. It ensures that only one `**unique_ptr**` can point to the object at any given time.



![gif](https://github.com/outscal/2D-Platformer-Game/assets/107213542/f0dedc50-7395-45ac-a816-333241e1c9c1)




```cpp
std::unique_ptr<int> uniquePointer = std::make_unique<int>(42);
// Only uniquePointer owns the memory for the integer

std::unique_ptr<int> anotherUniquePointer = std::move(uniquePointer);
// Transfer ownership, now anotherUniquePointer owns the memory

```



Use cases - Managing resources that should have a single owner, such as a game character or a configuration object.



## Shared Pointer


---

A “`**shared_ptr**`” allows multiple pointers to share ownership of the same dynamically allocated object. It keeps track of how many shared pointers are pointing to the object and deallocates the memory when the last one goes out of scope.



![gif](https://github.com/outscal/2D-Platformer-Game/assets/107213542/a7d7153f-a936-4937-8195-ca7e204c581f)




```cpp
std::shared_ptr<int> sharedPointer1 = std::make_shared<int>(42);
std::shared_ptr<int> sharedPointer2 = sharedPointer1;
// Both sharedPointer1 and sharedPointer2 share ownership of the integer

```



Use case: Managing shared resources like textures or sound buffers in a game where multiple objects need access to the same resource.



## Weak Pointer:


---

A **“**`**weak_ptr**`**”** is created as a copy of shared_ptr. 

It provides access to an object that is owned by one or more shared_ptr instances, but it doesn't affect the ownership count of the object it points to. 

The primary use case for weak_ptr is to break **Cyclical Dependencies** that can occur in complex systems when objects refer to each other.



Let's consider a practical example from game development:

Suppose you have a game with two classes: ‘Player’ and ‘`**GameMap**`’. 

Each player can access the game map, and the game map can reference players for various purposes (e.g., tracking player positions).

So, it’s always like Player is pointing to GameMap and GameMap is pointing to Player. Hence, use_count will never reach zero and they never get deleted.



![gif](https://github.com/outscal/2D-Platformer-Game/assets/107213542/3f54d07f-ce89-4921-bce7-106f6cbc77d0)




`weak_ptr` solves this problem by not having ownership of a resource like `shared_ptr` but still being able to access it.



![gif](https://github.com/outscal/2D-Platformer-Game/assets/107213542/9c906ad4-28a9-465a-b9ce-3161c6fe4780)




Use cases:

- Preventing circular references between objects, which can occur in complex game systems.
- Temporary access to a shared resource without prolonging its lifetime.
