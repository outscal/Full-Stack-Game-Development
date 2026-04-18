You've developed some projects by now, and you have taken your first steps towards developing awesome games!

Let's try to solve a game dev problem using that knowledge.



![Plague Tale Rats](/Full-Stack-Game-Development/images/655e0e8def30bba1.png)

**Plague Tale Rats**



Plague Tale is a great game and it won multiple awards in 2022 Game Awards.

Plague Tale has huge hordes of rats. These rats chase you, and if they catch you, they eat you. 

Sounds scary!

But if you throw fire on them, all the rats caught in the fire die.

Now...

How do you think these rats are managed in the game?



```cpp
class RatCrowd
{
	Rat rat1;
	Rat rat2;
	Rat rat3;
	Rat rat4;
	...
}
```



You can create separate variables, but how many?

Do you know how many rats there are in Plague Tale?

![placeholder](/Full-Stack-Game-Development/images/2bfb1268d0a9f96b.png)



Yup, you read it correctly,

THREE HUNDRED THOUSANDS rats!



Imagine writing 300,00 variables for just declaring the rats.

I don't know about you, but if it were me, I'd immediately hand my resignation.



But don't worry, we developers are too lazy to do this. So, we use Data Structures



## data structures


---



Data structures are a way of organizing and storing data so that it can be accessed and modified efficiently. They are essential to easily manage and use the data. 



> **Data structure is simply a tool used to organize, process, retrieve, and store data.**



## Solving Rat Problem


---

In the case of Plague Tale's rats, imagine data structures as a list.

Here is a pseudocode for the solution



```cpp
class RatCrowd
{
	int TotalRats = 300000;
	Rat ListOfRats[TotalRats];
}
```

 

Yup!

It's that easy, you don't have to `copy-paste` 300,000 lines. 

1 line will do the trick



## Understanding Data Structures


---

You needed to create 300,00 rats, and you created a list of rats. 

Now, you can do whatever you want in this list.

You can move all rats in any direction, you can increase or decrease the damage all rats do, and you can even kill all rats at once.



Basically, you have a lot of data, and you put it in a structure, that is what data structures do.



A suitcase filled with your clothes is like a data structure

A library filled with books is like a data structure

Your YouTube playlists also use data structures



Every collection of anything you see on a computer is made up of data structures.

In the next chapter, we'll discuss the different types of Data Structures

**See you there👋🏼**
