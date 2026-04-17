> [Click here](https://outscal.com/compiler/the_hidden_core_network) to this assignment.
> 
> Go to this link and start writing your code.
> 
> **NOTE:** This assignment is independent of your game code.




You are now part of a highly secretive organization, 

known as the Code Network, 

which manages advanced systems for critical global operations. 



The Network is facing a complex problem: 

it manages a vast array of specialized agents (functions), 

within a common framework (base class), 

but not all agents are performing optimally. 



Your mission is to streamline their operation.



The Network’s control system has a base layer called the “Operations Core.” 

This Core oversees all agent operations, 

but not every agent behaves as expected under its guidance. 



Some agents are unique, with distinct protocols that must be acknowledged by the Core.



**Your Tasks:**



- **Establish the Operations Core:**



- - Create a class named `OperationsCore` with a virtual function `executeTask()`.
  - The `executeTask()` function should print: "Executing general task protocol."



- **Design Specialized Agents:**



- - Create three agent classes that inherit from the `OperationsCore` class:
  - - `CyberAgent`: This agent handles cybersecurity protocols and overrides `executeTask()` to print "CyberAgent executing cybersecurity protocol."
    - `DataMiner`: This agent deals with data extraction and overrides `executeTask()` to print "DataMiner extracting data sets."
    - `LogisticsBot`: A basic agent that doesn’t override `executeTask()`.



- **Deploy the Agents:**



- - Create pointers of the `OperationsCore` type, each pointing to one of the specialized agents (`CyberAgent`, `DataMiner`, and `LogisticsBot`).
  - Use the pointers to execute each agent’s task protocol and observe the results.



- **Analyze the Network Behavior:**



- - Verify which agents run their unique protocols and which default to the general task protocol.
  - Reflect on why some agents run specialized tasks while others do not, using the concept of virtual functions.





# Submission Instructions


---

> Submit your personal generated link below after completing your code.
