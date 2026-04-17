You’ve got your `Node.h` file in place. 

Time to implement `SingleNode.h` and `DoubleNode.h`.



Do you need to add anything new in `SingleNode` ? Nope!

You already have everything in `Node` for `SingleNode`. 



> **TODO: SingleNode.h**
> ✅ Create a folder `SingleLinked` inside `LinkedListLib` 
> ✅ Create `struct SingleNode` inheriting `Node` inside `SingleLinked` folder. Make sure to add the nested namespace of `LinkedListLib` and `SingleLinked`



**Click here to see **`SingleNode.h````cpp
#pragma once
#include "LinkedListLib/Node.h"

namespace LinkedListLib
{
	namespace SingleLinked
	{
		struct SingleNode : public Node 
		{};
	}
}
```



When you talk about `DoubleNode` , you know you have to add something extra on top of the normal `Node`.

It's the `previous` pointer, which maintains a reference to the previous element in the list. It allows bidirectional traversal.



> **TODO: DoubleNode.h**
> ✅ Create a folder `DoubleLinked` inside `LinkedListLib` 
> ✅ Create `struct DoubleNode` inheriting `Node` inside `DoubleLinked` folder. Make sure to add the nested namespace of `LinkedListLib` and `DoubleLinked`
> ✅ Add extra property `Node* previous = nullptr`



**Click here to see **`DoubleNode.h````cpp
#pragma once
#include "LinkedListLib/Node.h"

namespace LinkedListLib
{
	namespace DoubleLinked
	{
		struct DoubleNode : public Node
		{
			Node* previous = nullptr;
		};
	}
}
```



You’ve just set up your `SingleNode.h` and `DoubleNode.h` files, inheriting from `Node.h`. 



**See you in the next section! 👋**
