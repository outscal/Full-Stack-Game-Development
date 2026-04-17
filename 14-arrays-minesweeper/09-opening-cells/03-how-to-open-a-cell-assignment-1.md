# Initial Instructions


---

- Make sure you are in the  `Feature-6_Gameplay` branch in your git repo.
- Make changes mentioned in the assignment (Add new commits) on this branch.
- Create a `Pull Request`, from this feature branch `Feature-6_Gameplay` to the previous branch `main` if not already created.
- If you had created a PR previously, no need to create again, simply commit your changes, and that PR will be updated.
- Since this is a guided assignment, code reviews will not happen, instead, the solution code will be present at the end of the next chapter.
- But, before checking the solution code, try your best to solve it independently.



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



## Detect a Mouse Click


---

## [tasks]


In the `Button.h` file 

1. Add `bool isMouseOnSprite(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` method.
2. Add a `void handleButtonInteractions(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` function.


In the `Button.cpp` file 

1. Implement the `bool isMouseOnSprite(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` method.
2. Implement the `void handleButtonInteractions(Event::EventPollingManager& event_manager, const sf::RenderWindow& window)` function.



In the `Cell.cpp`, `Board.cpp`, `GameplayManager.cpp`, and `GameLoop.cpp` files 

1. Implement the `update()` methods for respective classes. 



## Callback Function


---

## [tasks]



1. Add the `registerCallbackFunction` method in the `Button` class. 
2. Update the `handleButtonInteractions` implementation in the `Button` class.
3. Call `registerCellButtonCallback()` in `Cell::intialize()`
4. Add the `onCellButtonClicked` method in the `Board` class.



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
