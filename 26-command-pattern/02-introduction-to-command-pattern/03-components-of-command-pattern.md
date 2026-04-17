The process of creating, storing, handling, executing, commands involves multiple components each with their own set of responsibilities.



These components of command pattern are as follows:

- **Abstract Command:** This is a template for any command which can be used to encapsulate an **Execute()** call.
- **Concrete Command:** These are specific implementations of the Abstract Command. Each Concrete Command class encapsulates a particular action.
- **Client:** The client is responsible for creating and setting up the commands. It initiates requests that are to be executed but is separated from the objects that actually perform these requests.
- **Command Invoker:** The invoker is the object that triggers the execution of commands. It stores and manages a collection of command objects and executes them when needed.
- **Receiver:** The receiver is responsible for carrying out the actual action associated with a command. It's the object that knows how to perform the operation when the command is executed.



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_24_2023__12_49_34.png)



To understand better, lets revisit our restaurant example from before. We will replace all entities in that example with the component that they represent:



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/10_24_2023__13_13_18.png)



1. The **Customer** being the **Client** creates a **Command (Order)** according to his requirement
2. The **Client** then tells the **Command Invoker** to Process this command, **Waiter** being the Command Invoker.
3. The Waiter processes this command and **stores it** somewhere to be used later.
4. After some time the **Command Invoker** calls the **Command** object's **Execute() **method.
5. Calling execute() results in **Receiver** **(Chef) **to invoke Action1() & Action2()



![](https://tenor.com/view/reference-captain-america-avengers-understood-gif-7991943.gif)



In the next section we will understand the current architecture of the project and figure out how can these components be fit in it.
