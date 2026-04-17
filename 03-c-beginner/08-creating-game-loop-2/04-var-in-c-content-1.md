I hope you have given your best to bring justice to the world of Pizzas!

I hope you did your best to create the ***Midnight Pizza Fight***!



This content will expand your knowledge of a concept that can almost seem like magic!



## Let the magic begin!


---

```csharp
int age = 30;
float weight = 60.45f;
double height = 1.75;
char grade = 'A';
bool isStudent = true;
string name = "John Doe";
```



What if I tell you can write this code without ever mentioning any specific Data Type and the code will still work exactly as it is?

Here I introduce to `***var***`!

```csharp
 var age = 30;
 var weight = 60.45f;
 var height = 1.75;
 var grade = 'A';
 var isStudent = true;
 var name = "John Doe";
```



> **💡PRO TIP:** `***var***` 
> The `***var***` keyword tells the compiler to decide the type of variable based on the right side of the initialization statement.
> `***var***` can be used for multiple types: built-in data types, user-defined types like classes, etc. etc.



Now isn't it beautiful...

Whenever you need a variable, call your friendly neighbourhood friend...🕷️ `***var***`



## How does `var` work?


---

**SAMPLE CODE for an Addition Function:**

```csharp
int add(int a, int b)
{
	return a+b;
}
```



**SAMPLE CODE to use **`**var**`** with the above Function:** 

```csharp
int total1 = add(2,3); 			//No var
var total2 = add(5,7);			//var
var total3;												//var
```



**Statement 1:** This is pretty simple, compiler will look at `int` and it'll know that the data type is `int`. Easy Life.

**Statement 2:** Since `var` is used, compiler will look at the right side, it'll know that return type of `add()` is `int`, so it'll know `total2` is an `int`. Again, Easy Life.

**Statement 3:** Now, this gets a little messy. Since there is nothing on the right of `var`, compiler won't be able to decide the data type of `total3`. This doesn't work!



That's it!

That's how simply `var` works

> *"Look at the right and decide the type"*
> -`*var*`



## WHen "**NOT"** to use `var`!


---

I get it, using `var` looks very enticing.

You never have to worry about the data type.

Well, it comes with its drawbacks.



**1. Can compromise readability and clarity**



Code with `var` 

```csharp
var birthdate = new DateTime(1990, 5, 15);
var today = DateTime.Today;
var age = today.Year - birthdate.Year;
if (birthdate > today.AddYears(-age)) age--;
var dayOfWeek = birthdate.DayOfWeek;
var formattedDate = birthdate.ToString("dddd, MMMM dd, yyyy");

Console.WriteLine("Born on: " + formattedDate);
Console.WriteLine("Day of the week: " + dayOfWeek);
Console.WriteLine("Age: " + age);

```





Code with Explicit Data Types

```csharp
DateTime birthdate = new DateTime(1990, 5, 15);
DateTime today = DateTime.Today;
int age = today.Year - birthdate.Year;
if (birthdate > today.AddYears(-age)) age--;
DayOfWeek dayOfWeek = birthdate.DayOfWeek;
string formattedDate = birthdate.ToString("dddd, MMMM dd, yyyy");

Console.WriteLine("Born on: " + formattedDate);
Console.WriteLine("Day of the week: " + dayOfWeek);
Console.WriteLine("Age: " + age);

```





Which of these codes is easy to understand?

Well, of course, the second one.

Because you clearly know which variable is of which type. So you know which operations can be performed on which variable.

Imagine trying to perform multiplication on a `char` and then blaming God for making you a bad programmer...that'll just be too sad😞 



This can get even worse when you use `var` everywhere in a big project with hundreds of files and hundreds of people working on the same code base.

**2. Self-Describing Code**

When you use Explicit Data Types and properly name variables and functions, your code becomes self-explanatory.

This gives a huge advantage, especially when you are working in a team or you are creating libraries (code) that will be used by other developers.

**3. Type Specific Operation** 

Same example that I gave above:
Imagine trying to perform multiplication on a `char` and then blaming God for making you a bad programmer

This can easily happen if you use `var`, especially when data types get complicated.

**4. Can lead to Unexpected Errors** 

When right-side expressions get complicated, using `var` can assume a different data type than expected. This can lead to subtle bugs that are hard to track down.

**5. Code Standards and Consistency** 

Many teams establish coding standards that require you to use explicit types to maintain consistency and clarity. 



## WHen to use `var`!


---

**1. Clear Type from the Right-Hand Side**

When the data type is too obvious by looking at the right side. 

Example: `var num = 47f;` 

`f` at the end makes it too obvious that this is a float.

**2. Anonymous Types** 

Sometimes the data type is not known at the time of coding. This can happen while working on external Databases and APIs. (don't get worried by the big words, you'll understand everything as you keep going through his course and keep growing as a programmer🙌🏻)

**3. Iterating through Collections** 

> **💡PRO TIP: Collections in C#**
> As the name suggests, collections are collections of data types. These can be collections of integers or strings or objects of a class or even a collection of collections. You'll use collections in upcoming Unity projects!



If, while handling a collection, you don't know its data type, then using `var` can make your life super easy!

```cpp
foreach (var item in listOfComplexObjects) 
{
    // Process item
}
```



Here, the type of `item` will automatically be decided based on the type of `listOfComplexObjects` 

And you can work with this list carefree!

**4. Handling Local Variables**

Clarity can become an issue when using `var` for a large code base, but it can be used for local variables (variables declared in a function's scope, or in any other scope).

Example: `for (var x = 1; x < 10; x++)`
