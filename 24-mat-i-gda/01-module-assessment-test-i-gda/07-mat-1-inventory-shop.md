# **Inventory and Shop (MAT-1/GDA)**


---

- You have to create an Inventory and Shop Game mechanic as follows:
- The Game Screen will be divided into 2 different UI Panels as shown below, each with a Grid UI:

![](/Full-Stack-Game-Development/images/8344cd0b4ec2abc7.png)



- One Panel represents Shop and the other represents Player Inventory
- Your current **Currency** will displayed on the top corner of the Screen
- Initially, your player inventory will be empty and you will have no money
- There will be many items in the shop that you can buy.
- Each item in the shop or inventory will have the following properties:
- - Type
  - Icon
  - Item description
  - Buying Price
  - Selling Price
  - Weight
  - Rarity
  - Quantity



### Item Types


---

- Items can be of the following types:
- - Materials
  - Weapons
  - Consumables
  - Treasure
- The shop UI will have 4 tabs for each item type
- Selecting a tab will display available items of that type in the shop.



### Selling & Buying Price


---

- When an item is in the shop, selecting that item should show it’s buying price
- When an item is in the inventory, selecting that should show it’s selling price



### Weight


---

- There would be a maximum weight the Player can carry in their inventory.
- Each item will have a certain weight.
- When an item is bought or sold the player’s inventory weight will be updated accordingly.
- The cumulative weight of all the items in the player inventory should always be less than the Maximum Weight.



### Rarity


---

- Each item can be of any of the below Rarity Levels:
- - Very Common
  - Common
  - Rare
  - Epic
  - Legendary
- The Value of the item will accordingly be more or less.



### Icon & Description


---

- Each item will have a unique Icon and Text Description
- Any of the Items in inventory or the shop when selected, its icon, description, value, weight, and any other details will be shown in UI like in the below reference image:

![](/Full-Stack-Game-Development/images/fbad7458d6b551ed.png)



- The layout of your game screen can be designed and tweaked according to your preferences as long as all the features are implemented correctly.



### Gathering Resources


---

- At the bottom, there should be a button to gather resources.
- Initially, the player will have nothing in the inventory and no money as well.
- The player can click the gather resource button and collect some random items.
- The rarity of items gathered will be directly proportional to the cumulative value of the player’s inventory.
- If the inventory’s weight offshoots the maximum weight that can be carried, the gathering resources button will not work and a popup will be shown to indicate the same to the player.



### Buying and Selling Items


---

- Each Item in the shop when selected will show a Buy Button while showing its details.
- If you have enough money you can buy that item and it will shift in your inventory.
- If you don’t have enough money, a popup should be displayed to indicate the same.
- If you select an item in your inventory there should be a sell button along with the details of that item being shown.
- Clicking it should remove that item from the inventory and move it back to the shop.
- Upon selecting “Buy Item” and “Sell Item” button, a popup will be shown to the player where they can select the quantity they want to buy or sell.
- Player can increase or decrease the quantity of the item using ‘+’ and ‘-’ buttons displayed in the popup:



![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8c9f7b97-3438-434a-b8ca-0a53eb7262ea/217e3595-9645-4365-8415-f2d4064906fb/Untitled.png)

![](/Full-Stack-Game-Development/images/4873600420430466.png)



- After selecting the quantity of the item, there should be a popup asking for conformation like shown in the example below:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8c9f7b97-3438-434a-b8ca-0a53eb7262ea/e14294c9-3de0-4d8d-832b-1c389d189001/Untitled.png)

![](/Full-Stack-Game-Development/images/c5a8ba7116eb3191.png)



- When buying an item from the shop: (If conditions are satisfied)
- - A sound will be played
  - Resources will be deducted
  - An overlay text will appear for a few seconds and then disappear for example: “*You bought wxyz”*
  - The bought item will be placed in your inventory UI
  - Current weight of the inventory will be increased accordingly.
- When Selling an item:
- - A sound will be played
  - Resources will be increased
  - Inventory UI will be updated
  - An overlay text will appear for a few seconds and then disappear for example: “*You gained **** gold”*
  - The current Cumulative weight of the inventory will be decreased



## Assets & Resources


---

- **Outscal Asset Library** → [Click Here](https://drive.google.com/drive/folders/1XyofqfzoSdIE5coDiYUnrMW7Tj3Fwq8z?usp=sharing)
- Feel free to use your own assets from the internet and make your game look unique.
- Some of the widely used sites
- 1. [Click Here](https://www.spriters-resource.com/game_boy_advance/pokemonemerald/), [Click Here](https://assetstore.unity.com/packages/2d/free-2d-mega-pack-177430?aid=1101lPGj&utm_source=aff), [Click Here](https://itch.io/game-assets)
  2. Please feel free to use any assets you want.



## Submissions


---

1. Commit your code frequently (every ~30mins with meaningful commits)
2. Push your code to GitHub at the end of every 3hr session
3. At the end of day, record small 2 min video just telling your progress.
4. Submit your final project repository + readme file + small video showing the gameplay working and explaining your code architecture implementation in a 5min loom video



- **Focus of evaluation:**
- Code quality
- Architecture
- System design (make things flexible, modular and scalable)
- Use of Design Patterns



## **Things to note while pushing your code in Github**


---

- Add proper readme file in your GitHub repo.
- 1. Create a video of the gameplay and add it.
  2. Explain what your game is about.
  3. Give an architectural overview of scripts being used in your game (You can create a block diagram on ***miro*** or any similar platform)
  4. Mention all the Design Patterns and Programming Principles you have used in the game and also mention where you have used them.
  5. The hierarchy of your scripts and assets should be properly maintained.
- Make sure to create branches for all the individual features you have implemented.
- Merge all the feature branches to the main/master branch.
