# **Chapter 12 - Implementation - LRU cache**

**[ Task ]**

- Design a data structure that follows the constraints of a <a href="https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)" target ="_blank">Least Recently Used (LRU) cache</a>.
- Implement the ***LRUCache*** class:
    1. ***LRUCache(int capacity)*** Initialize the LRU cache with positive size capacity.
    2. ***int get(int key)*** Return the value of the key if the key exists, otherwise return -1.
    3. ***void put(int key, int value)*** Update the value of the key if the key exists. Otherwise, add the key-value pair to the cache. If the number of keys exceeds the capacity from this operation, evict the least recently used key.
- **Note -** The functions get and put must each run in O(1) average time complexity.
- Use the below template as the starter code.

```cpp
class LRUCache {
public:
    LRUCache(int capacity) {   
    }
    int get(int key) {
    }
    void put(int key, int value) {   
    }
};
```

**[Submission]**

- Turn in this assignment with your repl link.