In this chapter, You learned about pointers, memory addresses.

Moreover, object creation with `new` keyword and at last memory leak.



But did you notice?

You haven't used a pointer in your game code.😂



Now, it’s time to update the code by applying the pointer concept.



*Can you guess where you can use a pointer in your code?*



> 💡**Brainstorming** :  scroll on the code. and try to find the place where you can change the code using pointer.





Do you remember? 

You have created the player object of the player class, the Pokemon object of the Pokemon class, and other objects of different classes.





Look on the **main.cpp** file :



```cpp
#include "Main/Game.hpp"
#include "Character/Player/Player.hpp"
#include "Pokemon/PokemonChoice.hpp"
#include "Pokemon/PokemonType.hpp"
#include "Character/ProfessorOak.hpp"
#include "Utility/Utility.hpp"
#include <iostream>
#include <limits> // Include this header to use std::numeric_limits
#include <string>

int main() {

    // Continue with the main flow of the game
    N_Character::ProfessorOak professor("Professor Oak");
    N_Character::N_Player::Player player;

    // Greet the player and offer Pokemon choices
    professor.greetPlayer(player);
    professor.offerPokemonChoices(player);

    // Explain the main quest
    professor.explainMainQuest(player);

    // Start the main game loop
    N_Main::Game game;
    game.gameLoop(player);

    return 0;
}
```



You have created 3 objects of different class.

First is, You created professor object of `Professor Oak` class.

Second, You also created player object of `Player` class.

And also created game object of `Game` class.



These are called soft objects. 

These objects are destroyed automatically when their scope ends.



You have to create the object using `new` keyword.

When you create an object  using `new`, it gives you more **control over memory management**. 

You can decide when to allocate and deallocate memory.



> **TODOs :**

> ✅ Replace all soft object and create same object using `new` keyword in main.cpp.

> ✅ Delete all these object using `delete` keyword manually at the end of main function in `main.cpp`.





Main.cpp - Solution```cpp
#include "Main/Game.hpp"
#include "Character/Player/Player.hpp"
#include "Pokemon/PokemonChoice.hpp"
#include "Pokemon/PokemonType.hpp"
#include "Character/ProfessorOak.hpp"
#include "Utility/Utility.hpp"
#include <iostream>
#include <limits> // Include this header to use std::numeric_limits
#include <string>

using namespace N_Character;
using namespace N_Player;

int main() {

    // Continue with the main flow of the game
    ProfessorOak* professor = new ProfessorOak("Professor Oak");
    N_Player::Player* player = new N_Player::Player();

    // Greet the player and offer Pokemon choices
    professor->greetPlayer(player);
    professor->offerPokemonChoices(player);

    // Explain the main quest
    professor->explainMainQuest(player);

    // Start the main game loop
    N_Main::Game* game = new N_Main::Game();
    game->gameLoop(player);

    delete(professor);
    delete(player);
    delete(game);
    
    return 0;
}
```



Now, In your code base.

Find out all soft objects and replace it.

And create objects using `new` keywords.
