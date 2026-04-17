# **TASKS**


---



## LEVEL CREATION


---



## [IN LevelModel]

1. Create the following properties:
2. - `private:`
  - 1. `std::vector<LevelData> level_configurations`
    2. `float cell_width`
    3. `float cell_height`
  - `public:`
  - 1. `static const int number_of_rows = 28`
    2. `static const int number_of_columns = 50`
3. Create void initialize(int width, int height), inside it:
4. 1. Calculate and initialize `cell_width`. (cell width will be equal to total screen width per number of columns)
  2. Calculate and initialize `cell_height`. (cell height will be equal to total screen height per number of rows)
5. Create getter functions for cell width and height



## [IN LevelController]

1. Create reference of  `LevelModel` & `LevelView` and initialize them in `constructor`.
2. 1. `LevelModel* level_model`
  2. `LevelView* level_view`
3. Call lifecycle functions of `level_view`
4. Call `level_model`'s `initialize()` and pass `grid_width` and `grid_height` using `level_view`
5. Create getter functions for `cell_width` and `cell_height` and return `level_model`'s dimensions in it
6. Delete the references in `destroy()`





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Level**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Level**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
