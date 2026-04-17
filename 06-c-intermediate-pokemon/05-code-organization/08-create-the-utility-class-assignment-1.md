# Initial Instructions


---

> **Make sure you have checked out the **`Feature_4_Code_Organization` **branch in your git repo.**
> 
> **Make changes for this assignment (Add new commits) on this branch.**
> 
> **Create a **`Pull Request`**, from this feature branch **`Feature_4_Code_Organization` **to previous branch **`Feature_3_Main_Quest` **if not already created previously.**
> 
> **If you had created a PR previously, no need to create again, simply commit your changes and that PR will be updated.**



> 💡**PROTIP:**
> You can spoil yourself by looking at the solution before trying out the assignments, but we don't recommend learning that way.

> If you feel stuck somewhere, don't worry 😌

> It's a part of the learning process!

> Clear your doubts [here](https://discord.com/channels/536834108077113364/680360808936767496). It's a very helpful and inviting place!



You’ve been doing great with organizing your code! 



Now it’s time to take another step and group some frequently used functions into a Utility class. 



This will help keep your main file neat,

and make your functions easier to find and update.




---



**Tasks:**



1. **Create a Utility Header File:**
2. - Create a new file in the same folder as your source files and name it `Utility.hpp`.
  - In `Utility.hpp`, declare the functions `clearConsole()`, `waitForEnter()`, and `clearInputBuffer()`. Don’t forget to use the `static` keyword for each function.
3. **Create the Utility Source File:**
4. - Create another file named `Utility.cpp`.
  - In `Utility.cpp`, include the `Utility.hpp` file and define the functions `clearConsole()`, `waitForEnter()`, and `clearInputBuffer()`.
  - Remember to use `Utility::` before the function names to define them properly.
5. **Update Your Main File:**
6. - Include the `Utility.hpp` file at the top of your `main.cpp`.
  - Go through the main code and replace calls to `clearConsole()`, `waitForEnter()`, and any other utility functions with `Utility::clearConsole()`, `Utility::waitForEnter()`, and `Utility::clearInputBuffer()`. This makes sure the main file knows these functions belong to the Utility class.
7. **Clean Up Your Main Code:**
8. - Make sure your main file doesn’t have any leftover code for the functions that are now in the Utility class. Double-check that all function calls use the `Utility::` prefix to avoid any errors.




---



By following these steps, 

you’ll have a cleaner main file, 

and your utility functions will be grouped in a neat, 

organized manner! Keep up the great work!



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
