# Quiz - Processing Commands

Quiz - Processing Commands


## Questions


### Q1. How does the PlayerService process a command passed by the GameService?
- By directly executing the command within the PlayerService.
- By storing the command in a registry for future use.
- By setting the input state to EXECUTING_INPUT.
- By delegating command processing to the corresponding player and setting unit references for the command. **(correct)**

### Q2. How does the communication flow between classes occur when processing a command in game development?
- GameService -> PlayerService -> PlayerController -> UnitController -> CommandInvoker **(correct)**
- UnitController -> PlayerController -> GameService -> PlayerService
- PlayerController -> UnitController -> CommandInvoker -> GameService
- CommandInvoker -> GameService -> PlayerService -> PlayerController
