> [Click here](https://outscal.com/compiler/the_mysterious_potions_of_the_wizards) to this assignment.

> Go to this link and start writing your code.

> **NOTE:** This assignment is independent of your game code.





You've stumbled upon a wizard’s tower, 

filled with mysterious potions and magical items. 



As an apprentice wizard, 

you have the chance to brew potions that can either permanently or temporarily boost your magical power.



There are two potions you can brew:



1. **Elixir of Wisdom:** A permanent boost potion that increases your magic level by 10 points.
2. **Potion of Swiftness:** A temporary boost potion that increases your magic level by 50 points, but only for one spell cast.



Your task is to brew these potions and see how they affect your magic level!



### **Tasks:**



1. **Set Up Your Magic Level:**
2. - Create an integer variable `magicLevel` in the main function and set it to 30.
3. **Create a **`**castSpell()**`** Function:**
4. - Write a function `castSpell()` outside the main function that takes `magicLevel` as an argument and prints `"Casting spell with magic level: X"` where X is the current level of magic.
5. **Brew the Elixir of Wisdom (Call by Reference):**
6. - Create a function `brewElixir()` outside the main function that takes `magicLevel` as an argument by reference (`&`).
  - Inside the function, increase the magic level by 10 points permanently.
  - Call `castSpell()` to show the effect of the potion.
7. **Brew the Potion of Swiftness (Call by Value):**
8. - Create a function `brewPotion()` outside the main function that takes `magicLevel` as an argument by value.
  - Inside the function, increase the magic level by 50 points temporarily.
  - Call `castSpell()` to show the effect of the potion.
9. **Test the Potions:**
10. - In the main function, call `brewElixir()` and then `brewPotion()` to see how each potion affects your magic level.



Expected Output:

```cpp
Initial magic level: 30

Casting spell with magic level: 40  // After drinking the Elixir of Wisdom (Call by Reference)

Casting spell with magic level: 80  // After drinking the Potion of Swiftness (Call by Value)

Final magic level: 40
```



### **Key Takeaways:**



- The Elixir of Wisdom boosts your magic level permanently by reference, making it last beyond one spell.



- The Potion of Swiftness boosts your magic level temporarily, as it’s passed by value, not affecting the actual magic level beyond the spell cast.





# Submission Instructions


---

> Submit your personal generated link below after completing your code.
