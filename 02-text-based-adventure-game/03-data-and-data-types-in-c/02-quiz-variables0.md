# Quiz - Variables

Quiz - Variables


## Questions


### Q1. What is the correct syntax to write comments in C++?

1. # This is a comment
2. / This is a comment
3. // This is a comment
4. /* This is a
     new comment
   */
- 1
- 2
- 3
- 3, 4 **(correct)**

### Q2. Which of the following statements about variable declaration in C++ is NOT true?
- A variable must be declared before it can be used.
- Variable names can start with an underscore (_).
- The declaration and initialization of a variable must occur in the same statement. **(correct)**
- Variable declarations specify the data type and name of the variable.

### Q3. What is the output of the following code?

#include <iostream>
int main()
{
  int x = 11;
  int y = x*x;
  std::cout<<x<<y<<x+y<<y-x<<'\n';
	return 0;
}
- Compilation Error
- 11121132110 **(correct)**
- 12111     110132
- 11121     132110

### Q4. Consider the following code snippet:

int main() {
    // Single line comment

    /* Multi-line 
       comment */
    
    return 0;
}

Which statement about comments in C++ is inaccurate?
- Multi-line comments cannot be nested within single-line comments.
- Both single-line and multi-line comments can be nested within each other. **(correct)**
- Comments can be used as a substitute for writing proper code documentation.
- Comments have no impact on the compiled code size.
