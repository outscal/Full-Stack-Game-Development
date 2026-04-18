**WE HAVE OUR BOARD READY!**

It is a big piece in the game and now we'll work on the small pieces, the cells!

**Have a look at this board**



![ ](/Full-Stack-Game-Development/images/b61f9e0ee0c3118a.png)



> We want to create a lot of cells, but what to call this collection of cells? Let's call it a
> 
> **"Grid"**



This grid is not a static image like the board's texture, but an interactive unit that will modify over time, both in gameplay and looks.

A grid with 9 rows and 9 columns is made up of 81 (9x9) cells.



Before drawing the cell, you need to understand

**What happens in a cell?**

1. Cell can either contain a **mine**, a **number** or simply be **empty**. The cell will look different in all three cases.
2. Cell can either be **hidden** (closed) or **revealed** (open).
3. Cell has to interact with other cells around it, so it should know its position
4. Player will be able to flag or unflag a cell.



Now that you understand this, let's start with rendering a single cell on board from the next lesson.

**See you there 👋🏼**
