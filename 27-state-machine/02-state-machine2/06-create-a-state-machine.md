> In your ***Project-Setup**** *branch complete the following tasks, commit all these changes and submit the link of your branch for this assignment.



**Tasks:**

- **Create an **`**IState**`** interface with following methods to be implemented:**
- `**OnStateEnter()**`
- `**Update()**`
- `**OnStateExit()**`



- **Create an enum called **`**OnePunchManStates**`** and define various states for One Punch Man**



- **Create a StateMachine class called **`**OnePunchManStateMachine**`** responsible for managing all state transitions.**
- Initialize all states inside `**OnePunchManStateMachine**` and map them to their corresponding enum value.
- Set the Owner of this State Machine as well as all the states that you have created.
- maintain the current state of enemy and update it each frame.
- Create a `**ChangeState(IState newState)**` method which will switch the current state to new state.



- **Implement concrete state classes for different enemy behavior:**
- **Idle State** => Enemy does nothing for a few seconds and then transitions to rotating state
- **Rotating State** => Rotates 180 degrees and goes back into Idl state
- **Shooting State** => If the player enters enemy range, enemy starts shooting towards player. If player goes out of enemy range, enemy transitions back to Idle State.



![](//outscal.github.io/Full-Stack-Game-Development/images/c384479b0168e549.gif)
