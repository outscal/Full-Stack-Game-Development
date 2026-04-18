
# **Instructions for Submissions**

<figure class="video_container">
  
<iframe src="https://www.loom.com/embed/b32fc0b46d2d4f3fab949e3a19457f70" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</figure>

<br>
<details>
<summary>
Important steps to keep in mind while creating and merging the branches while submission.
</summary>

1. Always create a new branch **before starting** a new feature implementation.
2. Consider you have a branch named feature-1 and your implementation is done but code reviews are pending which means your **merging is pending for feature-1 into master**. That's why to start a new feature you should create a branch named feature-2 **from feature-1 and not from the master** to bring in an exact copy of your latest changes.
3. **Once code review is done for feature-1**, and if you are on a different branch than feature-1 then **checkout at the feature-1 branch**(means just come to feature-1) then do required changes as per mentor code review. After the changes are over **merge the feature-1 branch into master.**
4. **If feature-1 branch changes are critical** for the feature-2 branch **then only merge feature-1 into feature-2 as well.**
5. After merging is done of feature-1, you can checkout at the feature-2(or any other latest branch that you were working on) and **continue your work.**
</details>
<details>
<summary>
Important steps to keep in mind while submitting your pull requests
</summary>

1. If you have created a branch named feature-1 **from a master** then submit the pull request by comparing feature-1 **with a master.**
2. **Generalization**: If you have created an X branch **from a Y branch** then submit a pull request by comparing the X branch **with a Y branch**. 
</details>

<img src="/Full-Stack-Game-Development/images/6f3dd1991e346e42.jpg" width ="700">


