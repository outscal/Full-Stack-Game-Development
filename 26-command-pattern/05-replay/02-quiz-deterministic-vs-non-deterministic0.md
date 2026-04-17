# Quiz - Deterministic vs Non-Deterministic

Quiz - Deterministic vs Non-Deterministic


## Questions


### Q1. Can the Command Pattern be used for implementing undo and replay features in non-deterministic game engines?
- Yes, by recording and replaying individual player actions just like in deterministic engines.
- Yes, by periodically taking snapshots of the game state to provide some level of consistency.
- No, the Command Pattern is not suitable for non-deterministic game engines. **(correct)**
- Yes, by creating branching timelines to account for the multiple possible outcomes.

### Q2. Can the Command Pattern be used for implementing undo and replay features in games with continuous gameplay?
- Yes, by storing player actions as command objects and replaying them in the same order as they were originally executed.
- No, the Command Pattern is only suitable for games with discrete gameplay, and it cannot handle continuous gameplay.
- Yes, by employing a time-stamped command queue to maintain the sequence of actions for replay. **(correct)**
- Yes, as long as you have a Time-Traveling Unicorn
