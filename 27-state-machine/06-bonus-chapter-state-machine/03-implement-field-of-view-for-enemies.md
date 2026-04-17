> Create a Bonus-Solution branch and complete the following tasks, commit all these changes and submit the link of your branch for this assignment.



**Tasks:**

- Currently there is a radius for the range of each enemy.
- Which means each enemy has a radial detection range, inside which if a player enters, the enemy will detect that player.
- You need to update this into a field of view for each enemy to be conical like below:

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/11_15_2023__10_25_09.png)



- Each enemy will have a field-of-view and vision-distance property in its scriptable object which will be determine the line of sight for each enemy.
- By implementing this feature, your enemies will not be able to detect the player behind their back.

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/11_15_2023__10_30_25.png)
