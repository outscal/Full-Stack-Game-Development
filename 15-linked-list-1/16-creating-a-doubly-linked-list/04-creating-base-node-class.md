**Ready to code? 🐍💻**

Go open your Visual Studio! 
Opened? Good! 👍



As discussed in the previous section, the architecture we lectured you about is now ready for action. 

It’s time to move forward with it...



Check this out! ASAP! 📸

![Image](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_01_2024__18_57_02.png)



I know, I know—you've seen them before. 

But let’s refresh: Singly linked list nodes have **one** pointer, and doubly linked list nodes have **two** pointers. This is where their structures differ. That means having two different node classes is a necessity.



But How Does This Look in the Code for your Snake Game? 

Take a look:

![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/6635d6da56724faeff889a65/06_06_2024__06_05_59.png)



Any comments?? 💬

Do you see any similarities between these two?  

Both have data `body_part` and at least one pointer, `next`, in common.



So, what does this mean? 

We can have a base `Node` class that these two can inherit from. For `DoubleNode`, just add one more pointer. 

And in the future, if you wish to add more similar functionalities, you can add them to `Node` rather than to both classes. 

**Reusability for the win! 🏆**

 

Lesss go!!



> **✅TODO: Node.h**
> Add your `Node.h` in the `LinkedListLib` folder and within the namespace `LinkedListLib`.



**Click here to see **`Node.h````cpp
#pragma once
#include "Player/BodyPart.h"

namespace LinkedListLib
{
	using namespace Player;

	struct Node
	{
		BodyPart body_part;
		Node* next = nullptr;
	};
}
```



That was short and simple because you’re a pro now! 💪 

Head on to create more classes in the upcoming sections.



**See you there! 👋**
