# Generic Implementation of Bullet Pool

<b>[Topics covered in the video]</b>

- Modification of BulletPool class by inheriting it from GenericObjectPool class.
- Reducing the number of lines and using generic methods from Generic Object Pool


<b>[NOTE]</b>

- We only defined GetBullet Functionality in the Bullet pool and ReturnBullet() method is removed entirely,
- The reason for this is that ReturnBullet is a public method, and whoever is returning the bullet has no dependency on the BulletPool.
- Hence the definition of ReturnItem() in the GenericObject pool is sufficient and we don't even need to define that in the child class.

<iframe src="https://www.loom.com/embed/4a22bbca7b3f415b84f9b06f1e77cea0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>
<div style="text-align: center">
<img src ="https://github.com/outscal/AGD_ObjectPooling_CosmicCuration/assets/107213542/aa716c3b-35c1-4c9d-8365-118330bc40e6" alt = "img" width=40% >
</div>

<br>
<div style="text-align: center">
<img src ="https://github.com/outscal/AGD_ObjectPooling_CosmicCuration/assets/107213542/e0b59efe-8bbc-4234-a2a7-9e42af08d7cb" alt = "img" width=100% >
</div>