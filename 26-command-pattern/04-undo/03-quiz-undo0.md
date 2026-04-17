# Quiz - Undo

Quiz - Undo


## Questions


### Q1. In turn-based strategy games like Civilization, the Undo feature is implemented by:
- Reverting the entire game state to a previous save point.
- Reversing the last executed command using the Command Pattern. **(correct)**
- Creating a new game instance without the last action.
- Rewinding time to a specific moment in the game.

### Q2. When implementing the Undo feature, why should each command class have an Undo() method that knows how to reverse its action?
- To complicate the codebase and add redundancy.
- To enable players to undo multiple actions simultaneously.
- To ensure that the Undo feature works seamlessly with all unit actions. **(correct)**
- To store a history of commands in a separate registry.
