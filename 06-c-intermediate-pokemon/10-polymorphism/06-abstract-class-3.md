In the last lesson,

you override `attack()` function in all the classes,

of different types of Pokemon.

But, your code started giving errors after that.

Can you guess why is it so?



Okay, let me give you a hint.

*You can not create an object of an ****Abstract Class****.*

*Because ****Abstract Class**** is created to be used as a base class only.*



You have learnt about the **Abstract Functions**,

but what is this **Abstract Class**?



*Any class that consists an abstract function in it,*

*is known as ****Abstract Class****.*



Now, can you identify why your code is giving errors?

Yes, because of Abstract Class.



In the previous lesson,

you created `attack()` abstract function in `Pokemon` class,

that means now your `Pokemon` Class is an **Abstract Class**.



So, you can not create any object of `Pokemon` Class type.

You can just use `Pokemon` Class-type pointers,

to handle child classes (different types of Pokemon)





# Coding Time


---

So, you have to change your code a little bit.



You have to remove all `Pokemon` class type objects,

instead, you can directly create different types of `Pokemon` class objects.



But remember, you will still use `Pokemon` class type *pointer*.



Let me show you an example.



Suppose, you want to create a Charmander Pokemon,

currently, your code looks like

```cpp
chosenPokemon = new Pokemon("Charmander", PokemonType::FIRE, 100, 10);
```



But now, you need to change it to the one given below.

```cpp
chosenPokemon = new Charmander();
```



Now, it's your job to do so for the rest of the code.





Apart from this, there are still some lines in the code,

which are using Pokemon Class objects.



```cpp
Player::Player() {
    name = "Trainer";
    chosenPokemon = new Pokemon(); // Using the default Pokemon constructor
}
```



In the player class constructor,

there is no need to assign default `Pokemon` class object in `chosenPokemon`.

So, you can remove this line from the code.



Also, in the parameterized Player class constructor,

there is no need to pass a `Pokemon` type of pointer.



Currently:

```cpp
Player::Player(string p_name, Pokemon* p_chosenPokemon) {
  name = p_name;
  chosenPokemon = p_chosenPokemon;
}
```



But it should be like:

```cpp
Player::Player(string p_name) {
  name = p_name;
}
```





Now, it's time to update the `Game.cpp` and `Game.hpp` file.



Declare a `wildPokemon` pointer of Pokemon type in the header file,

and also declare the destructor for the class so that,

you will be able to delete the above pointer manually.



Game.hpp```cpp
........
class Game {
  private:
    Grass forestGrass;
    Pokemon* wildPokemon;

  public:
    Game();
    ~Game();
    void gameLoop(Player* player);
    void visitPokeCenter(Player* player); 
};
```



In `Game.cpp`, remove these line of code.

```cpp
N_Pokemon::Pokemon* wildPokemon = new N_Pokemon::Pokemon();
.....
delete(wildPokemon);
.......
```



And define the destructor as follows.

```cpp
Game::~Game(){
    delete(wildPokemon);
}
```





Once you are done with all the changes,

try to run your code.



This time, your code should run properly.
