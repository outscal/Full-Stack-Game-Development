In the last lesson, you learned that interfaces are like rules that different objects must follow. 

You used projectiles (rocks, arrows, bullets) as an example. 

They behave differently but follow the same rules through an interface. 



Here, before going to create interface for status effect.
Firstly understand, **What is status effect ?**



---


In many games, you’ll notice certain attacks or conditions that apply ongoing effects to characters—things like poison, burn, or sleep. 

These effects don’t just hit once, they last through the battle.



And they continue to affect the Pokémon over several turns.

Changing its ability to move, its health, or other stats



In our Pokémon game, status effects are really important. 

A Pokémon that’s **Poisoned** might lose health every turn.

While a **Burned** Pokémon might have weakened attacks. 



![img](//outscal.github.io/Full-Stack-Game-Development/images/c031692ff69411dd.png)





Status effects like these can completely change how a battle plays out. 

They’re not just about immediate damage—they influence the whole fight.



Now, even though **Poison** and **Burn** are different effects, they share some basic behaviors. 

For example, both effects are applied to the Pokémon over time. 



They change how the Pokémon performs, and eventually, they wear off.

So, instead of writing separate code for each status effect.



*wouldn’t it be easier if all status effects followed the same basic rules? *

This is where you use an **interface**.







# Designing the `IStatusEffect` Interface


---



Each status effect has a different impact, but they share some common behaviors. 

1. They need to be **applied** to the Pokémon.
2. They have a **name** to display in the game.
3. They **affect the Pokémon at the end of each turn**, and some may prevent the Pokémon from moving.
4.  the effect needs to be **cleared** once it wears off.



You’re going to create an interface called `IStatusEffect`. 
This interface will act like a contract for every status effect. 

It will declare some basic methods that all status effects—like `applyEffect`, `getEffectName`,`clearEffect `or `turnEndEffect`—must have. 


Interface might look like:

```cpp
class IStatusEffect {
public:
    // Apply the effect (e.g., poison, burn)
    virtual void applyEffect(Pokemon* target) = 0;

    // Get the name of the effect
    virtual std::string getEffectName() = 0;

    // Apply the changes due to effect after the end of each turn
    // Returns true if the Pokémon can move, else false
    virtual bool turnEndEffect(Pokemon* target) = 0;

    // Remove the effect
    virtual void clearEffect(Pokemon* target) = 0;

    virtual ~IStatusEffect() = default;
}
```



You might be confused**, What Do These Methods Do?**

**1. **`**applyEffect()**`

This method is used to apply the status effect, such as poisoning or burning the target Pokémon.



**2. **`**getEffectName()**`

This method simply returns the name of the effect, such as "Paralyzed" or "Burned." It helps to display the effect during the battle.



**3. **`**turnEndEffect()**`

This method checks if the effect is still ongoing. 
If the Pokémon is still affected by **Poison** or **Burn**, this method will return true.



**4. **`**clearEffect()**`

This method removes the status effect from the Pokémon when the effect wears off.




---



By using this interface, you can create different status effects that all follow the same structure but have unique behaviors. 



**For example :** 

**Paralysis** may stop a Pokémon from moving.
while **Burn** reduces health each turn. 





Think back to the example of projectiles we used earlier. 

A rock, an arrow, and a bullet all behave differently, but they follow the same basic rules.

They all need to move, have a direction, and interact with the world. 



**Status effects work the same way.** 

They each do something unique, but they follow the same contract. 

This makes it easier to add new effects later because they’ll all fit into the same system.





By using an interface, you create a clear, simple system for handling status effects in your game. 

Whether it’s **Poison**, **Burn**, or any other effect.



In the next lesson,
You'll take this interface and start implementing specific status effects like **Poison** and **Burn**. 

You’ll see how each effect uses the same rules but adds its own unique behavior to the game!


**Great Job🎉!**
