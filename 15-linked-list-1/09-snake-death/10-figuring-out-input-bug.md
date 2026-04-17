**Alright, do exactly as I say!**

*START THE GAME*

*PRESS MULTIPLE ARROW KEYS VERY QUICKLY. *

*TRY TO ROTATE THE SNAKE VERY FAST *

Did the game break?

Did the snake die before turning at all?



If not, try again!

Keep trying until you break the game!





**⚠️WARNING:** Don't read anything beyond this line unless you have experienced the glitch!


---





# Brainstorming the Cause


---

What can be the reason for this bug?

What must be happening when you give multiple inputs in a short time?



Are your fingers moving faster than the processing time of a CPU?

Is the snake too lazy to turn so quickly?

Can this be caused because of some garbage data?

Is it a VS issue?

What if there is something wrong with the order of operations?



I don't know, I'm not giving you the answer straight away, you need to ***THINK!***



> **💡THINK TODO: Use Your Brain🧠 **
> **✅ **Figure out what is the reason for this bug!





**⚠️WARNING:** Don't read anything beyond this line unless you have thought of all possible reasons for this bug


---





## Real Reason


---

When you press buttons too quickly, the `current_snake_direction` changes faster than the snake is visually updated on screen. So, in the code, the direction is updated but not on screen. So while checking for collision, the code considers the updated state and detects a collision.



# Brainstorming the Solution


---

If the issue is that direction is changing in code faster than the visuals, you can just update the visuals instantaneously too. That'll solve the issue.

But do you want your snake to be so fast?

It'll be too quick to handle.



What about the other way around?

How about you slow down the process of  updating`current_snake_direction`?



Yes, you can do that!

You can register the input once and then register it again only when the snake is visually updated.



## How To implement the solution?


---

You can use Bools or Enum to check if input is taken and applied

And of course, Enum is a better approach because of the readability!

Enums are just so much more readable than bools!



Here is the Enum for you:

```cpp
enum class InputState
{
	WAITING,
	PROCESSING
};
```



> **TODO: **`**SnakeController**` 
> ✅ Create the above Enum in `SnakeController`



The next section is an assignment where you have to fix this bug...

On your own! 



**So buckle up!**
