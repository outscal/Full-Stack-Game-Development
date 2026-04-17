> [Click here](https://outscal.com/compiler/code_conflict) to this assignment.
> 
> Go to this link and start writing your code.
> 
> **NOTE:** This assignment is independent of your game code.





Imagine you are working on a financial application that processes transactions. 



The application has two primary classes:

 `Transaction` (the base class) and `CreditTransaction` (a derived class). 




---



**1. Your task is to identify and understand how method hiding occurs within these classes.**



- **Transaction Class**: This class represents a general financial transaction with a method `process()` that outputs: `"Processing a standard transaction."`
- **CreditTransaction Class**: This class inherits from `Transaction` but redefines the `process()` method to output: `"Processing a credit transaction."`



**2. Simulate the Code Conflict:**



- Implement both classes with the described `process()` methods.
- Create an instance of `CreditTransaction` and call the `process()` method.
- Analyze which version of the method is executed and document why this behavior occurs.



**3. Access Hidden Behavior with the **`**::**`** Operator:**



- Use the `::` operator to explicitly call the `process()` method of the `Transaction` class from the `CreditTransaction` object.
- Reflect on why this might be necessary in real-world applications, particularly in large, evolving codebases like LegacyLine.



# Submission Instructions


---

> Submit your personal generated link below after completing your code.
