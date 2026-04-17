# **TASKS**


---



## Drawing BODYPART


---



## [IN Body Part]

1.  Create empty lifecycle functions, apart from `initialize()` and `update()` 
2. Create `createBodyPartImage()` and initialize the `bodypart_image` with the `new` keyword and call this function inside the constructor
3. Set `grid_position` to `(0,0)` inside inside the constructor
4. Call `bodypart_image->render()` inside `render()` 
5. Create `void destroy()` and delete the `bodypart_image` inside it, and call it inside the destructor
6. Create `void BodyPart::initialize(float width, float height, sf::Vector2i pos, Direction dir)`
7. Set the values of the below properties based with the values taken in parameters

> `bodypart_width`
> `bodypart_height`
> `direction`
> `grid_position`

1. Create `initializeBodyPartImage()` and call it inside the `initialize()` 
2. Implement `update()` 

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Linked-List**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Linked-List**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
