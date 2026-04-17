**No space for an Array in Snake's life?? **

**Why So?? Lets Discuss.**



Now you've got a good grip on your snake's functionality.. 

But here's the thing I keep wondering (and I'm sure you've thought about it too).

Why didn't we call upon our old buddy of Array Jumper (**Array**) for the snake? Let's discuss it.



## Using Array to create snake


---

You used a 2D array earlier as well, as you did in Minesweeper, to create a 2D grid.

Additionally, your snake is nothing but a connected chain of body parts.

You can create a structure to store the position and direction of a body part.

Then, create an array of objects of that structure, with each element holding the data of each body part.

That way, an array could be represented as a snake. Sounds good so far, right?


![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__06_27_17.png)

***This is how the array looks like***


![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_20_2024__06_58_42.png)

***Not your Snake but kind of your Snake***



**Both look similar!!! Isn't it??**



> Why isn't an Array the ideal choice for your snake game?



To get a hunch about this question, we have to first brainstorm on the things that make any two data structures different.

It's none other than **Time and Space. **

They play a big role in decision-making to choose which data structure on which operation.



Let's talk about **time** first. You've already learned what time is required in array for insertion and deletion during array Jumper, so let's test it.



Let's play a quiz? 

I will give you a few cases for insertion and deletion and you have to answer how much time this case would take. Alright?



![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__06_36_54.gif)



What would be the time complexity for **Insertion at the Beginning**?

Click here to check the answer

In Arrays, it takes **O(N)** time because we've got to shift everything back to make room at the front. It's like rearranging furniture to fit in a new couch!

> **Hint: Linked Lists do this way quicker, but we'll talk about that magic in the next chapter! 🤭**





Let's move to the next question: what would be the time complexity for **Insertion at the End**?

Click here to check the answer

It's quick and easy in Arrays (**O(1)**) if we know the size (size = last element index of snake + 1). 



Few more to come, what would be the time complexity for **Insertion at Middle,** and What would be the time complexity for **Deletions** of these cases?

Click here to check the answer (Don't worry you will not get Rick Rolled)

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__06_37_27.gif)



Click here to check the answer

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_31_2024__06_23_00.png)





We have covered the time, so what do we have next?

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/05_14_2024__06_38_31.gif)



**MEMORY!!**

Memory is very important when you are dealing with something that changes frequently. 

Your snake isn't just a static bunch of body parts; it's a dynamic entity that grows and shrinks whenever the snake eats delicious food items. 🐍🍎



This means you're constantly adding new body parts (insertion) and sometimes removing them (deletion) as the snake moves and grows. However, arrays **like to know their size upfront. **



*It's like asking to pick up the T-shirt before we even know the size! 🤷‍♂️*

*But that doesn't work with our parents—they always go for the bigger sizes! 😄*



Similarly, if you use an Array for your snake game, you have to be like your parents i.e. you'd have to make its size as big as possible upfront.



When it comes to dynamic space allocation, arrays fall short; it's like trying to fit a growing snake into a fixed-size box.

Now that you've seen why Arrays aren't ideal for a snake game's changing size.



To overcome the **limitations** of arrays, you'll dive into **Linked Lists** in the next chapter—an ideal, flexible, and efficient data structure for your game. Stay tuned!

 

**See you in the next chapter 👋**
