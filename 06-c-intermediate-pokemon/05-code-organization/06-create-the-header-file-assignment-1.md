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



Here's the updated version of the guided assignment, 

incorporating the additional point about deleting the `header.hpp` file:




---



Let's start by tidying up. 



Make sure you replace `#include "header.hpp"` back with the `}` at the end of your main function,

and delete the `header.hpp` file we created earlier. 



That was just for demonstration.



Now, it's time to organize your code by creating your first proper header file! 

We'll start with the `PokemonType` enum.




---



**Tasks:**

1. **Create a New Header File:**
2. - In the same folder as your source file, create a new file and name it `PokemonType.hpp`.
3. **Move the PokemonType Enum:**
4. - Remove the `PokemonType` enum from your main source file and move it into the new header file.
5. **Include the Header File in main.cpp:**
6. - To use the `PokemonType` enum in your main source file, include the header file using `#include "PokemonType.hpp"`.



Your directory should look like this:



```cpp
Project_Folder/
├── main.cpp
├── PokemonType.hpp

```



Here’s what the content of `PokemonType.hpp` should look like:




---



Follow the same steps you did for `PokemonType`. 

Create another header file for the `PokemonChoice` enum.




---



Keep it up! 

This is a crucial step towards making your code cleaner and easier to manage!



# Submission Instructions


---

> Submit the Pull Request (PR) link after pushing all the changes in the specified branch.
