> 💡 **PRO TIP: Input in C#**

> In C#, you can capture user input from the console using various methods. The two most commonly used methods for this purpose are `Console.ReadLine()` and `Console.Read()`.



# ReadLine


---

Implementation of the `Console.ReadLine()` function:

- **Reads** an entire line of text from the input stream.
- **Returns** the input as a `string`.
- **Useful for** capturing multi-character input, such as words, sentences, or any text input, until the user presses the `Enter` key.



> 💡 **PRO TIP: Input Stream**

> Refers to the flow of data from the user.





Example of `Console.ReadLine()`

```csharp
using System; 
class Program 
{ 
		static void Main() 
		{ 
				Console.WriteLine("Enter your gamer name:");
				// Reading from the input stream and returning to name
				string name = Console.ReadLine(); 
				Console.WriteLine("Hello," + name + " !"); 
		}
}
```





# Read


---

Implementation of the `Console.Read()` function:

- **Reads** a single character from the input stream.
- **Returns** the ASCII value of the character as an `int`.
- **Useful for** scenarios where you need to capture just one character, such as when processing character-by-character input.



Example of `Console.Read()`

```csharp
using System; 
class Program 
{ 
		static void Main() 
		{ 
				Console.WriteLine("Press any key to start the game..."); 
				int charCode = Console.Read();
				char character = (char)charCode; // Cast the int to char
				
				//Start game
		}
}
```
