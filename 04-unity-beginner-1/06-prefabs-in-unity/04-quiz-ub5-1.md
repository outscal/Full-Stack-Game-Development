# ⏳Quiz

ub5


## Questions


### Q1. In Unity, what is the primary advantage of using Prefabs when you have multiple instances of the same GameObject in your scene?
- Changes to one instance automatically update all other instances.
- Modifying the prefab asset updates all instances. **(correct)**
- Each instance remains unique, preventing accidental changes.
- Prefabs increase memory usage but improve performance.

### Q2. When you unpack a prefab instance in Unity, what happens to that GameObject's connection to the original prefab asset?
- It is deleted from both the scene and the prefab asset.
- It disconnects from the prefab, becoming a regular GameObject. **(correct)**
- It remains linked but ignores future prefab updates.
- It becomes a new prefab asset on its own.

### Q3. What is the difference between Unpack Prefab and Unpack Completely in Unity?
- They perform the same action; there is no difference.
- Unpack Prefab unpacks the root and all nested prefabs; Unpack Completely  unpacks the root prefab.
- Unpack Prefab unpacks the root prefab only; Unpack Completely unpacks the root and all nested prefabs. **(correct)**
- Unpack Prefab creates a variant; Unpack Completely deletes the prefab asset.

### Q4. How do Prefab Variants in Unity help with asset management?
- They duplicate all properties, increasing memory usage.
- They inherit properties from a base prefab but allow overrides, reducing duplication. **(correct)**
- They synchronize changes in both directions between variants and base prefabs.
- They eliminate the need for version control systems.

### Q5. If you want to modify one specific instance of a prefab without affecting others, which approach should you take?
- Modify the prefab asset directly.
- Override properties on the instance without unpacking it. **(correct)**
- Unpack the instance completely to disconnect it.
- Create a new prefab variant from the instance.
