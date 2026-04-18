> It’s time to create a new feature branch for the upcoming game features.

> Make a new feature branch out of your current branch called → ***Feature_6_Battle_Loop***

> Let’s start working on the new feature now!




Try to imagine yourself as the player as I explain how the game will proceed below:



![Pokemon Noir, Pokemon Art, Indie Game Dev, Indie Games, Pokemon ...](//outscal.github.io/Full-Stack-Game-Development/images/878e21a9e86cfeb0.gif)



You’ve been wandering through the tall grass, 

your heart racing as you encounter wild Pokémon. 

Now, it’s time to prepare for the ultimate challenge—battling these wild creatures!



How did it feel? Exciting right?

That's how the user will feel when they play your game.



It's time to create a working battle loop in your pokemon game where the player's Pokémon can engage in turn-based combat with wild Pokémon.

In this chapter you will be a creating simple battle system in your game with limited features, 

So that you understand the core mechanics of a battle system before diving into more advanced topics that will be taught later on in this module.



## What is a Battle Loop?


---

You might have played chess (I am assuming you have)

How do Players proceed, one player plays there move and then the other until one of the two checkmates the king of the other.

It is a repetitive cycle unless one player is victorious.



![Wizard Chess Gifs Get The Best Gif On Giphy | My XXX Hot Girl](//outscal.github.io/Full-Stack-Game-Development/images/62b3c8c891f400d8.gif)



Similar is the battle loop that you are going to design in your game 



Let's understand this more with the help of a flowchart





![Image](//outscal.github.io/Full-Stack-Game-Development/images/47c530a2b7404f33.png)





Player’s Turn → Attack → Opponent’s Turn → Attack → Repeat until a Pokémon faints.




---



Now, since you have understood the basic flow of a battle, 

What mechanisms do you think you need to implement in your Pokemon game for the battle?



Were you able to think? Below are the mechanics that you will need:



- Each Pokémon has a certain amount of health, and this health decreases when the Pokémon is attacked i.e., when a Pokémon's HP reaches zero, it faints. So, you will need to have a data structure **Health Points (HP)** to keep track of the Pokémons health.
- Pokemon battle is a **turn-based combat**, the Player and the wild pokemon will take turns attacking each other.
- You have declared health points but how will you reduce it in battles so that it reaches zero? We can create a **simple basic attack **method in the `Pokemon` class, which will reduce opponent's HP by a fixed amount.




---



In this chapter you will only be creating the basic attack methods that all the pokemons will share,

and there will be no differentiation between different Pokémon types in terms of their attack or defense abilities. 



(If you think this is intentional then yes, it is) Because I want you to first understand the core battle loop mechanics and making things simple can only do that.



But don't worry even though this chapter is limited regarding attacks and defense abilities in the pokemons of your game once you get your fundamentals strong, you will be adding unique moves and abilities to your Pokémon.



Adding unique moves and abilities to your Pokémon will require a more advanced approach that is not covered in this chapter but will be discussed in the lessons ahead.



And sooner you will be creating more complex and realistic battle system in your full fledge pokemon game for which this chapter is the stepping stone!!.



![Image](//outscal.github.io/Full-Stack-Game-Development/images/d068785739ea771e.png)
