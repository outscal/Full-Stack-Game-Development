# **Solutions Memory Leaks and Smart Pointers**

<details>

**<summary>Chapter 8 - Assignment 1 - Smart Pointer</summary>**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

**[Tasks]**

1. Redo the chapter 5 assignment 5 - Constructors by using a **smart pointer.**    
2. Find the order in which objects will be destroyed by printing a message in the destructor of each class.
3. Understand the difference between normal pointer and smart pointer.

Code-

```cpp
#include <bits/stdc++.h>
using namespace std ;

class Player
{
    private:

        int health, lives;

    public:
        
        Player(int _health, int _lives)
        {
            health = _health;
            lives = _lives;
            cout << "\nI am a player, I just got spawned!.\nMy health is " << health << " and I have " << lives << " lives.\n";
        }

        ~Player()       
        {   
            cout << "\nI am a player and I'm dead.\nMy health was " << health << ".\n";      
        }
};

class FastPlayer : public Player
{
    private:

        int speed;
    
    public:

        FastPlayer(int _speed, int _lives) : Player(100, _lives)        
        {   
            speed = _speed;
            cout << "\nI am a fast player, I just got spawned!.\n";
        }

        ~FastPlayer()   
        {   
            cout << "\nI am a fast player and I'm dead.\n";    
            }
};

void LocalObjects()
{
    unique_ptr<Player> P4;
    
    FastPlayer flash(200, 5);
}

int main()
{
    unique_ptr<Player> P1(new Player(50, 7));
    unique_ptr<Player> P2(new Player(100, 3));
    unique_ptr<Player> P3(new Player(80, 5));

    FastPlayer tez(100, 7);

    LocalObjects();
    return 0;
}
```

</details>

<details>

**<summary>Chapter 8 - Assignment 2 - Memory Leak</summary>**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

**[Task]**

1. Create a class of name Player*.*
2. Create a default constructor and print the following message in it:- 
    1. "I am a player, I just not spawned"
3. Create a destructor and print the following message in it:- 
    1. "Ops, that enemy killed me, I just died!".
4. Inside *main(),* create one object of a class Player.
5. Create a second object of class Player using a pointer and a *new* keyword.
6. Run the above code and observe the output.
7. Now add one more line in *main(),* using *delete* keyword free the memory allocated to object made using pointer.
8. Now again run the whole code and notice the difference in outputs with that of step 6.

Code-

```cpp
#include <iostream>
using namespace std;

class Player
{
    public:
    
        Player()
        {
            cout << "I am a player, I just got spawned" << endl;
        }
        ~Player()
        {
            cout << "Ops, that enemy killed me, I just died!" << endl;
        }
};

int main() 
{
  Player player1;
  cout << "Object created without new Keyword" << endl;
  Player *player2 = new Player();
  delete player2;
  cout << "Object deleted, created with new Keyword" << endl;
}
```

</details>