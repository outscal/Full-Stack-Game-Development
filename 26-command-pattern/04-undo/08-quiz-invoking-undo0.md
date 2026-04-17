# Quiz - Invoking Undo

Quiz - Invoking Undo


## Questions


### Q1. What's the problem with the below implementation of undo method in command invoker?

public void Undo() { commandRegistry.Pop().Undo(); }
- It will work as intended.
- No base conditions are present. **(correct)**
- If the command registry is empty we will get a stack underflow exception. **(correct)**
- If the last executed command does not belongs to the current active player it will create weird bugs. **(correct)**

### Q2. In a real-time strategy game like age of empires, a player orders multiple units to move and attack an enemy base simultaneously. 
If you decide to undo this complex action, which strategy should be employed?
- Store each unit's individual actions and reverse them in the exact order they were executed.
- Implement a "group command" that encapsulates all unit commands and can be undone as a single operation. **(correct)**
- Disable the undo feature for complex group actions to avoid issues.
- Record a snapshot of the entire game state before the complex action and revert to it during undo.
