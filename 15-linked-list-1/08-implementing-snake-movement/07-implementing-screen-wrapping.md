![Snake Wrapping](//outscal.github.io/Full-Stack-Game-Development/images/b2b0e62a6e048004.gif)

***OG Snake Wrapping***



You see how the snake enters one wall and comes out of the opposite wall!

You have to implement the same!



Implementing this is very straightforward, you can just check if the snake's position is within the bounds (0 and number of rows and columns), and if not, then change it to the opposite side.

Example:

```text
If LevelModel::number_of_rows (y) = 100 (0 to 99)
If LevelModel::number_of_columns (x)= 100 (0 to 99)

Now, if your x = 90, it is fine
But if your x = 100, you will move the snake to the other side, which is 0

Similarly, if x = -1, you'll change it to 99
```



You can do this with a simple `if` statement, but wouldn't that be boring?!



There is a better way, a cooler way, a mathematical way

Remember: The goal here is to keep a number between 0 and the number of rows and columns



Take your time and think...

🕛... 🕧... 🕐... 🕜... 🕑... 🕝... 🕒...



Did you figure it out?



MODULUS! REMAINDER!

You remember what Remainder is, right?



To calculate the remainder, you can use the *'%'* (modulus)

```text
5%5 = 0 // Because 5 divided by 5 leaves no remainder
6%5 = 1
2%5 = 2
3%5 = 3
```



Now, you can use this approach to restrict the movement between 0 and the number of rows and columns!

**Just Imagine**

`number_of_rows = 28` 

The snake is moving `DOWN`. It is currently at y-index `27`, which is the edge of the play area; in the next frame, the snake's head will move out of the frame.

Before changing the `head`'s y-position to `28`, you decide to do a little math-magic

```cpp
next_position.y = (current_position.y + 1) % number_of_rows
=> (27+1) % 28
=> 28 % 28
=>0
```

And TADDAAAA🪄!

The head's next y-position is `0`, and your snake is bound to appear from the opposite side of the screen!

That is WRAPPING for you!



But how will you handle it when the position is less than 0?

Well, THINK!



It is just basic maths; pick a pen and a paper and solve it yourself!

And don't see the below code before solving this 100% yourself!



> **TODO: **`**BodyPart**` 
> ✅ Update `getNextPositionDown()`, `getNextPositionUp()`, `getNextPositionRight()` and `getNextPositionLeft()` to implement wrapping



Click here to see the updated functions

```cpp
sf::Vector2i BodyPart::getNextPositionDown ()
{
	return sf::Vector2i(grid_position.x, (grid_position.y + 1)%(LevelModel::number_of_rows));
}

sf::Vector2i BodyPart::getNextPositionUp()
{
	return sf::Vector2i(grid_position.x, (grid_position.y - 1 + (LevelModel::number_of_rows)) % (LevelModel::number_of_rows));
}

sf::Vector2i BodyPart::getNextPositionRight()
{
	return sf::Vector2i((grid_position.x + 1) % (LevelModel::number_of_columns), grid_position.y);
}

sf::Vector2i BodyPart::getNextPositionLeft()
{
	return sf::Vector2i((grid_position.x - 1 + LevelModel::number_of_columns) % (LevelModel::number_of_columns), grid_position.y);
}
```





![Doofenshmirtz: Evil Laugh](//outscal.github.io/Full-Stack-Game-Development/images/53b78727bf462612.png)

*It is time!*



Time for the Snake to DIE!
