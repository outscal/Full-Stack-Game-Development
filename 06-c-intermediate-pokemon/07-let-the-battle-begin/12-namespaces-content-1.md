By this lesson, you have organised your code really well.

But a small step is still left, which you will do in this lesson.



You will add namespaces to your code now.

You have used the standard namespace multiple times,

that is "`using namespace std;`" but I guess,

you don't understand it well.



You can understand namespace as,

binding a few functions and variables together under some **term**.





Suppose you and your friend live in a hostel.

You both have separate rooms.



You went to the playground to play cricket,

but you forgot to bring a cricket ball.



When you guys realised this,

your friend said, "I saw it in the room, go get it".



Now, you will get confused about whose room your friend is referring to.

But there would have been no confusion if your friend would say "*your* room" or "*my* room".



![ ](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/09_16_2024__10_52_08.png)





The use of "your" and "my" in the above example is called namespace in the programming world.

Programmers use namespaces, so that compiler won't get confused.





Let's see how you can implement namespaces in your code.

Let me show an example of Utility files.



Utility.hpp```cpp
// Utility.hpp

namespace N_Utility{

    class Utility {
    public:
        static void clearConsole();
        static void waitForEnter();
        static void clearInputBuffer(); // New helper function
    };

}
```



Utility.cpp```cpp
// Utility.cpp
#include "../../include/Utility/Utility.hpp"
#include <iostream>
#include <limits>
using namespace std;

namespace N_Utility{

  void Utility::clearConsole() {
  #ifdef _WIN32
    system("cls");
  #else
    (void)system("clear");
  #endif
  }

  void Utility::waitForEnter() { cin.get(); }

  void Utility::clearInputBuffer() {
    cin.ignore(numeric_limits<streamsize>::max(), '\n');
  }

}
```



Now, wherever you want to use Utility file content,

just add the below code in the top of that file.



```cpp
.....
using namespace N_Utility;
.....
```



In place of the above code,

you can also use the scope resolution operator

```cpp
N_Utility::
```



But, what's the difference between them?🤔

- `using namespace N_Utility` imports all the names from the `N_Utility` namespace into the current scope, allowing you to access its contents without prefixing them with `N_Utility::`.
- `N_Utility::` explicitly specifies the namespace for each use, avoiding any ambiguity about where the identifier is defined. It doesn't import all the names in the namespace

When to use them?🤔

Here are some key differences:



Aspect

`using namespace N_Utility;``N_Utility::`**Readability**Less explicit, especially in large codebases.

More explicit and clear.

**Risk of Name Clashes**Higher risk if other namespaces or global names overlap.

No risk of clashes as names are scoped.

**Convenience**More convenient for repeated use of many namespace members.

Less convenient but safer.

**Best Practice**Suitable for small, self-contained code.

Recommended for larger or shared codebases.



Now, it's your task to implement namespace in all the files of your code.



> **NOTE:** You should follow a standard rule to implement namespace. Keep the name of the namespace as N_folderName
