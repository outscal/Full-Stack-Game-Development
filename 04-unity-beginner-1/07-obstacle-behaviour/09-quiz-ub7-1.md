# ⏳Quiz

ub7


## Questions


### Q1. You want to move a sprite smoothly from point A to point B over a period of time. Using Vector3.Lerp in the Update() method, you notice the sprite starts moving quickly and slows down as it approaches point B. Why does this happen, and how can understanding the mathematical function behind Lerp help you achieve a constant movement speed?
- Lerp uses linear interpolation, so the speed should be constant; the issue must be elsewhere.
- Lerp needs a consistent interpolation parameter over time; using Time.deltaTime incorrectly causes deceleration. **(correct)**
- The sprite slows down due to floating-point precision loss near point B; increasing precision fixes it.
-  Lerp inherently creates easing effects; using MoveTowards ensures constant speed.

### Q2. While scaling a sprite uniformly over time to double its size, you observe that the sprite becomes pixelated and loses quality. Why might this occur, and how does understanding the concept of texture filtering and sprite import settings help in preserving visual quality during scaling?
- Scaling doesn't affect sprite quality; the issue is with the camera settings.
- Sprites are raster images; scaling enlarges pixels. Adjusting texture filtering can help. **(correct)**
- The sprite's mesh becomes distorted when scaled; using higher-quality meshes prevents pixelation.
- Unity doesn't support scaling sprites; using vector graphics is necessary.

### Q3. You need to move a sprite from point A to point B in a straight line at a constant speed, ensuring it stops exactly at point B. Why might using Vector3.MoveTowards in the Update() method be more appropriate than using transform.Translate, and how does understanding MoveTowards help achieve precise movement?
- MoveTowards ignores frame rate; the sprite moves instantly to point B.
- MoveTowards moves the sprite incrementally toward the target each frame, stopping precisely at point B regardless of frame rate. **(correct)**
- transform.Translate automatically adjusts for frame rate, making it better for precise movement.
- Using transform.position directly ensures constant speed and precise stopping.

### Q4. When scaling a sprite non-uniformly (e.g., scaling only on the X-axis), the sprite appears stretched and distorted. Why does non-uniform scaling cause this distortion, and how can you mitigate the issue?
- Unity doesn't support non-uniform scaling; only uniform scaling works.
- Pivot point shifts during scaling; fixing it prevents distortion.
- Non-uniform scaling changes aspect ratio; adjust artwork or maintain aspect ratio to avoid stretching. **(correct)**
- Camera's field of view affects scaling; adjusting camera fixes it.
