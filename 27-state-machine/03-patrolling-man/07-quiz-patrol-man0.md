# Quiz - Patrol Man

Quiz - Patrol Man


## Questions


### Q1. What is the primary purpose of the PatrolManStateMachine class in this context?
- To define the behavior of the Patrol Man enemy. **(correct)**
- To manage state transitions for the Patrol Man enemy. **(correct)**
- To create and configure the Patrol Man's patrol points.
- To handle player input for the Patrol Man character.

### Q2. It seems like using the State Pattern always increases the number of classes in your designs. Look how many more classes your Enemy Controller has than the original design! So why should we use the State Pattern instead of implementing the whole logic in EnemyController itself?
- The State Pattern allows us to create separate classes for each state of an object, promoting modularity. This modular approach makes it easier to manage complex behaviors, update them, and add new states without affecting existing code.
- If we implement the whole logic in EnemyController instead, we will end up with very large, monolithic conditional statements. This makes our code hard to maintain and understand.
- By using separate classes for states, we make states explicit and reduce the effort needed to understand and maintain our code.
- All of the Above. **(correct)**
