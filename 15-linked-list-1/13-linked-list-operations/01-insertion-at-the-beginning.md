This chapter is pretty interesting and it sets the foundation of inserting in a linked list.

What you learn in this chapter will be applied to all insertions that you make in a linked list.

How you can insert nodes at different positions or how you can delete them. 

So, follow this chapter diligently!



In this section, you will insert a node at the Head of the Linked List.



## How to insert a node at the head


---

You already have a reference of the current head node (`head_node`) in `SingleLinkedList`

1.  Now you have to create a new node
2. Make the new node point at the current head node
3. Replace the current head node with the new node in `head_node` 



![Inserting at Head](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/65a8c70a6348a80a870c1fa7/05_31_2024__09_39_54.gif)

***Inserting at Head***



The pseudo-code will be like this:

```text
Create a new_node
new_node→next = head node
head node = new_node
```



Okay, this doesn't look like a lot

In just 3 lines you added a new node to the Linked List.



So, if you do this in the game, there will be a new `BodyPart` attached to the head. But at what location will it be spawned? In which direction will it move?

The above 3 lines don't consider this. They just add a new node. But the node in Snake has all the data for the `BodyPart`! So you need to calculate and set that data for every new node you add!



Alright, so before you start adding a new node to the snake, let's first solve the problem of initializing the new `BodyPart` that'll be created inside the node!
