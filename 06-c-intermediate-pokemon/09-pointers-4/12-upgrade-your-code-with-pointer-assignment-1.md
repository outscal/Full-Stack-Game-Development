# Initial Instructions


---

> **Make sure you have checked out the **`Feature_8_Pointers` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_8_Pointers` **to previous branch **`Feature_7_Inheritance `**if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!





In the previous lessons, you learned about pointers, 

how to create objects using the `new` keyword, 

and how to properly manage memory using `delete`. 



Now, it's time to apply these concepts directly to your game code.



In your main game file (`main.cpp`), 

you’ve created several objects directly without using pointers. 



To gain better control over memory management, 

you'll need to update these object creations.




---



### Tasks:



- **Identify Object Creation in **`**main.cpp**`**:**



- - Locate the objects created directly: `ProfessorOak professor`, `Player player`, and `Game game`.



- **Convert Object Creation Using Pointers:**



- - Replace each object creation using `new` to create these objects dynamically.
  - Example: Change `ProfessorOak professor("Professor Oak");` to `ProfessorOak* professor = new ProfessorOak("Professor Oak");`.



- **Access Methods Using Pointer Notation:**



- - Since you are now using pointers, update method calls to use the `>` notation.
  - Example: Change `professor.greetPlayer(player);` to `professor->greetPlayer(player);`.



- **Free Memory After Use:**



- - After you’re done using the objects, free up the memory by using the `delete` keyword.
  - Example: `delete professor;`.



### Steps to Implement:



-  Replace direct object creation with pointer-based creation using `new`.
-  Update method calls to use the `>` notation.
-  Ensure to delete the objects at the end of your program to free up memory.



Updating your code this way will help you manage object lifetimes more effectively and avoid potential memory management issues!





# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
