# **TASKS**


---

1. Create `StickCollectionModel`, `StickCollectionView` and `StickCollectionController` classes with empty lifecycle methods and follow nested `namespace Collection` & `Gameplay`



## CREATING A STICK


---



## [IN GAMEPLAY]

1. Inside the `Gameplay` folder, create another folder named `StickCollection`.
2. Create a file as `stick.h` inside `StickCollection`. 
3. Create `struct Stick` in the file within nested namespace `Gameplay` and `Collection` . 
4. You have to create properties for the struct Stick, which includes `int data `and a pointer to an object of type `RectangleShapeView`.



## [IN STICK.H]

1. Create a default constructor for `Stick`.
2. Create a constructor that initializes the data as `int` and allocates resources for the `stick view` pointer.
3. Create the destructor to delete the resource, which is the `stick view`.





## CREATING A COLLECTION OF STICKS


---



## [IN STickcollectionmodel.h]

1. Add the following properties as public:

`const float max_element_height = 820.f;`

`float elements_spacing = 25.f;`

`const float element_y_position = 1020.f;`

`float space_percentage = 0.50f;`



`const sf::Color element_color = sf::Color::White;`

`const sf::Color search_element_color = sf::Color::Blue;`

`const sf::Color found_element_color = sf::Color::Green;`

`const sf::Color processing_element_color = sf::Color::Red;`



`int linear_search_delay = 120;`

`int number_of_elements = 100;`



1. Create a public method void setElementSpacing(float space) and set elements_spacing as space in it.
2. Create `enum class SearchType{LINEAR_SEARCH, BINARY_SEARCH,}`





## [IN STICKCollectionController.h]

1. Add the following properties as private:

`StickCollectionView* collection_view;`

`StickCollectionModel* collection_model;`

`std::vector<Stick*> sticks;`

`Collection::SearchType search_type;`



1. Take care of the forward declaration of `StickCollectionView`, `StickCollectionModel` , `Stick` & `SearchType`
2. Getter for `search_type` and `number_of_elements`
3. Create the following properties private methods:

`void initializeSticks();`

`float calculateStickWidth();`

`void updateSticksPosition();`

`void resetSticksColor();`

`void initializeSticksArray();`

`float calculateStickHeight(int array_pos);`

1. Create an empty public method `void searchElement(SearchType search_type)`



## [in gameplayservice.h]

1. Integrate `StickCollectionController` into `GameplayService` to manage the collection of sticks within the gameplay.
2. Add the following properties as private:

`GameplayController* gameplay_controller;`

`StickCollectionContoller* collection_controller;`



1. Create a method `void searchElement(Collection::SearchType search_type)` that calls the `searchElement()` of  `StickCollectionController`.
2. Also, create its getter method.





# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-1-Linear-Search**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-1-Linear-Search**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
