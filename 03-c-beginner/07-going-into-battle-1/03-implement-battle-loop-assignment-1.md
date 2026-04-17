**ASSIGNMENT LINK:** [https://outscal.com/compiler/c-sharp-beginner](https://outscal.com/compiler/c-sharp-beginner) 



# **Tasks**


---

## Create Battle Loop


---



## [In Game Class]

1. Create empty `public void ProcessBattleLoop()`



## [In Program Class]

1. Call the `ProcessBattleLoop()` function in `Main()` after `game.SpawnCharacters()` 





## Show Battle Options


---



## [In Game class]

1. Implement `private void ShowBattleOptions()` function.
2. Call `ShowBattleOptions()` function in the `ProcessBattleLoop()` function.



## Process Battle Input


---



## [In Game class]

1. Create the empty `private void ProcessBattleInput()` function.
2. Implement the  `private string GetInput()` function.
3. Implement the  `private void PlayerAttack()` and `private void PlayerHeal()` functions.
4. Implement `private void EnemyAttack()` function.
5. In the `ProcessBattleInput()` function:
6. 1. Call `GetInput()` function and store the input in `string playerChoice`
  2. Call `Console.Clear()` after `GetInput()`.
  3. Create `switch` statement for the `playerChoice` after `Console.Clear()`
  4. Call  the `PlayerAttack()` and `PlayerHeal()` functions. in their respective `cases` in the `switch` statement.
  5. Call the `EnemyAttack()`inside `switch-case` after the player attacks and heals.
7. Call the `ProcessBattleInput()` function in `ProcessBattleLoop()` function after the `ShowBattleOptions()` function.



## Display Character stats


---



## [In Game class]

1. Implement the `private void DisplayCharacterStats()` function.
2. Call `DisplayCharacterStats()` function in the  `ProcessBattleInput()` function after `EnemyAttack()` function.



## Check Game Over


---



## [In Game class]

1. Implement the `private void ShowGameWin()`  and `private void ShowGameLose()` functions.
2. Call `ShowGameWin()` and `ShowGameLose()` in the `private bool CheckGameOver()` function when their respective conditions are met.
3. Call the `CheckGameOver()` function in the `ProcessBattleInput()` function after the player and enemy's attacks and break out of switch statements if true is returned.



## Invalid Input


---



## [In Game class]

1. Implement the `private void InvalidInput()` function.
2. Call the `InvalidInput()` in the `ProcessBattleInput()` function in the default case in the `switch` statement.



## Are Characters Alive


---

## [In Game class]

1. Implement the  `private bool AreCharactersAlive()`  function.
2. Implement the `do-while` loop using `AreCharactersAlive()` as a condition for executing `ShowBattleOptions()` `ProcessBattleInput()` functions.



Expected Output.


[Watch video](https://www.loom.com/embed/8d11bd3b58c24979bc54f8fde875c658)



**Battle Loop**







# Submission Instructions


---

- Save the code in the above compiler link
- Submit the Submission Link from the compiler
