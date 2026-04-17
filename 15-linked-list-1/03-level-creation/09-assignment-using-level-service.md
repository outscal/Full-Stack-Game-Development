So, now it should work when you hit `play`, yes? 

No, it will not work. Because you have not integrated the `LevelService` with `ServiceLocator`.

For that, do this small task.

**All the best.**



# **TASKS**


---



## USING LEVEL SERVICE


---

## [IN ServiceLocator]

1. Create a reference of `LevelService` as `level_service` and set it `nullptr` in `constructor`.
2. Create a `getLevelService()` getter function that returns the reference of `LevelService`.
3. Create an object of `level_service` in `createServices()` 
4. Call lifecycle functions of `level_service` just take care that `update()` & `render()` should only be called if the `GameState` is `GAMEPLAY`.
5. Don't forget to delete the object of `LevelService`.

# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Level**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Level**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
