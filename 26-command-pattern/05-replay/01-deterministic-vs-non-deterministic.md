> It’s time to create a new feature branch for the upcoming game features.

> 

> Make a new feature branch out of your main branch called → [ `**Feature-4-Replay**` ]

> Let’s start working on the new feature now!



In the world of game development, there are two fundamental types of game engines: **Deterministic** and **Non-Deterministic**. Let's explore what these terms mean and how they relate to game mechanics like undo and replay when using the Command Pattern.



## Deterministic game engines:

A deterministic game engine ensures that the outcome of the game is entirely predictable and consistent. In a deterministic game engine, given the same initial conditions and player inputs, the game will produce the exact same results every time it is played. 

This reliability and consistency make deterministic game engines suitable for turn-based games, puzzles, and strategy games, where precision and predictability are essential for gameplay. Imagine a chess game where every piece's move is predetermined. This predictability makes it suitable for turn-based strategy games or puzzles. 



## non-deterministic game engines:

These engines bring unpredictability to your gaming experience. In a non-deterministic engine, the same input may yield slightly different results each time you play. sometimes these differences can be negligible but can also hinder the gameplay experience if consistency matters for you.



## **Discrete and Continuous Gameplay:**



**Discrete Gameplay:**

Discrete gameplay involves actions in the game occurring in distinct, separate steps or turns. Players typically take individual turns, making decisions or performing actions one at a time. Turn-based strategy games like **Civilization**, board games like **Chess**, and classic role-playing games (RPGs) like **Fire Emblem** often employ discrete gameplay.




<iframe src="https://www.youtube.com/embed/IaO70dFKlc4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





**Continuous Gameplay:**

Continuous gameplay, also known as real-time gameplay, involves actions happening in a fluid and uninterrupted manner. Players can perform actions in real-time, and the game world keeps evolving without distinct turns. Action and Racing games like **Fortnite** and **Forza** are typical examples of continuous gameplay.



In many cases, games can combine elements of both discrete and continuous gameplay. For example, in an RPG, you might have discrete turn-based combat, but when exploring the game world, it's continuous.



## **The Role of Command Pattern:**

In deterministic and discrete games like chess, the Command Pattern neatly encapsulates each player's move as a command object. When a player chooses to undo a move, the command pattern plays back these objects in reverse order, essentially rewinding the game turn by turn. Similarly, you can re-execute these commands to produce the same result as below.



But if you are implementing continuous gameplay in a non-deterministic game engine, re-executing the same set of commands in the same order and in the same time frame as before might produce different results. Although its not impossible but this makes it difficult to implement these kind of features in your game.



Understanding the nature of your game engine, whether deterministic or non-deterministic, and the style of gameplay, whether discrete or continuous, is crucial when implementing undo and redo mechanics using the Command Pattern.
