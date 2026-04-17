# **Chapter 12 - Implementation - LFU cache**

**[ Task ]**

- Design and implement a data structure for a <a href="https://en.wikipedia.org/wiki/Least_frequently_used" target ="_blank">Least Frequently Used (LFU) cache</a>.
- Implement the ***LFUCache*** class:
    1. ***LFUCache(int capacity)*** Initializes the object with the capacity of the data structure.
    2. ***int get(int key)*** Gets the value of the key if the key exists in the cache. Otherwise, returns -1.
    3. ***void put(int key, int value)*** Update the value of the key if present or inserts the key if not already present. When the cache reaches its capacity, it should invalidate and remove the least frequently used key before inserting a new item. For this problem, when there is a tie (i.e., two or more keys with the same frequency), the least recently used key would be invalidated.
- To determine the least frequently used key, a use counter is maintained for each key in the cache. The key with the smallest use counter is the least frequently used key.
- When a key is first inserted into the cache, its use counter is set to 1 (due to the put operation). The use counter for a key in the cache is incremented either a get or put operation is called on it.
- The functions get and put must each run in O(1) average time complexity.
- Use the below template as the starter code.

```cpp
class LFUCache {
public:
    LFUCache(int capacity) {   
    }
    int get(int key) {   
    }
    void put(int key, int value) { 
    }
};
```

**[Submission]**

- Turn in this assignment with your repl link.