> It’s time to create a new feature branch for the upcoming game features.

> 

> Make a new feature branch out of your main branch called → **[ **`**Feature-1-Command-Pattern**`** ]**

> Let’s start working on the new feature now!



You must already be knowing by now what encapsulation is. Here is a reminder:

**"Encapsulation **is a *process of wrapping code and data together into a single unit****"***



**Command Pattern** takes encapsulation to a whole new level:  **It encapsulates a method invocation.**



In simpler terms, it allows us to solidify specific tasks or actions as individual commands.

This way, the object requesting the action doesn't have to concern itself with how the task is executed, it simply uses the predefined command to accomplish it.

We can also do some wickedly smart things with these encapsulated method invocations, like save them away for logging or reuse them to implement undo in our code.


---



Sounds confusing? It is a little hard to understand the Command Pattern by just hearing its description.

Let's understand how this works through an example:



Imagine you go to a restaurant as a customer and give the waiter your order.

The waiter takes your order and goes to the counter to convey the same to the chef.

The Chef prepares your meal according to the order received.



Lets see the above process in a more object oriented way now:

![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_24_2023__11_28_02.png)



If you look at the above diagram closely, you will notice that "**Order Slip**" encapsulates a method invocation to prepare a meal.

The order slip here is an object that acts as a request to prepare a meal. Since it is an object, it can even be passed around from one waiter to another. It can even be reused if the same customer wants to repeat their order.

The waiter doesn't need to know who prepares the order and how, He just needs to tell at the counter to **Execute() **this encapsulated request whenever necessary.



You might be thinking that's all great but how is it helpful in making video games!

Think of the game that we are going to create. There are some units in it, Wizards, Sword Masters, Mages, etc. They all have some specific Actions that they can perform. Now using the above example, what if we in the same way make a clear distinction between the Units making a request and the objects that receive and carry out those requests. The request in this example would be an encapsulated call to perform an action like "**Attack()**", "**Heal()**", etc.



If we do so, we can even store these encapsulated method invocations as objects in a **Command Registry**. We may use them in the future if we want to. This allows us to do all sorts of wicked things like making replay and undo game mechanics.



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_24_2023__12_03_44.jpg)



In the next section we will learn the components that are involved in implementing command pattern.
