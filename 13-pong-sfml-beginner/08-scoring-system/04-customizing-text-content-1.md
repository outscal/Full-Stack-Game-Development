*Look at these scores:*

```text
Player 1: 3        Player 2: 12
Player 1: 03      Player 2: 12
```

Which looks better?

The second one, right? Why?

- Even spacing
- Professional look
- Easy to read quickly



> 💡**PROTIP**: 
> Small details like score formatting make games feel polished and professional!



## Formatting the Score


---



Let's create a function that always shows two digits:

`UIService.cpp`

```cpp
string UIService::formatScore(int score)
{
    return (score < 10 ? "0" : "") + to_string(score);
}
```

*What's happening here?*

- Score less than 10? Add a "0" in front
- Score 10 or more? Show it as is
- Result: "00", "01", "02"... "10", "11"

Then, you need to keep track of the points.



## Keeping Track of Points


---



When a player scores, we need to:

1. Increase their score
2. Update the display
3. Make it look good!

Here's how:

`UIService.cpp`

```cpp
void UIService::incrementPlayer1Score()
{
    player1_score++;
}

void UIService::incrementPlayer2Score()
{
    player2_score++;
}
```

Updating the score:

`UIService.cpp`

```cpp
void UIService::update()
{
    left_score_text.setString(formatScore(player1_score));
    right_score_text.setString(formatScore(player2_score));
}
```



> **TODO** In `UIService.cpp`: 
> ✅Implement `string formatScore(int score)` 
> ✅Implement `void incrementPlayer1Score()` 
> ✅Implement `void incrementPlayer2Score()` 
> ✅Implement `void update()`



The logic to display the score is ready!

But, when should it update?

Think about:

- When does a player score?
- Which side did the ball go out?
- How do we track this?

All your questions will be answered in the next lesson!
