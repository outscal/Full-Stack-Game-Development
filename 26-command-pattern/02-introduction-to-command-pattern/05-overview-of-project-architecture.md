Before you start implementing command pattern in your project let us understand the current architecture of the project first:

![](/Full-Stack-Game-Development/images/141dc5be3d45b763.png)



The above block diagram gives you an overview of all the major components in the current project. Below is a more detailed explanation:

- The current project implements the Service Locator Patter where the class **GameService** acts as the Service Locator
- **Input Service** is responsible for detecting player inputs like choosing a Unit Action to execute or a choosing a Target and accordingly call relevant methods.
- **Battle Service** is responsible for creating a creating and loading a battle according to customized Scriptable Objects that contain all Level Configurations
- **Player Service** is where the Turn-Based mechanism is implemented and all the players and their respective Units are created, initialized and maintained.
- **Action Service** contains objects of various Action classes which holds the execution logic of any specific action like "Attack" and "Heal". When Units need to execute an action, they request the Action Service to `Perform()` that Action.
- ** UI Service **creates UI Controllers which are responsible for all UI related logic in the game like Action Selection UI and Battle Selection UI.



Go and take a good look at each of these Services in your project and try to understand their straight forward implementation. 

In the next section you will study in deep about Action Service and how Unit Controller interacts with it to execute an Action.
