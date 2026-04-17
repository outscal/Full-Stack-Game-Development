# Chapter 6 - Implementation - Reverse a String

<details>
  <summary markdown="span">Chapter 6 - Implementation - Reverse a String</summary>

**[Task]** - 

- Reverse a string without using the inbuilt function.

 **[Submission]** 

- Turn in this assignment with your repl link.

### Solution

```cpp
#include <iostream>
using namespace std;

void reverseStr(string& str)
{
    int n = str.length();
     
    for (int i = 0; i < n / 2; i++)
        swap(str[i], str[n - i - 1]);
    
    cout <<endl << "String After Reversing : " << str;
}

int main() 
{
    string str;
    string revStr;
  
    cout << "\nEnter The String : ";
    cin >> str;
    reverseStr(str);
}
```
</details>

<details>
  <summary markdown="span">Chapter 6 - Assignment - 1 - Operator overloading</summary>

**[Task] -** 

1. Create a *Player* class.
2. Declare a private member variable *name.*
3. Create a custom constructor to assign value to the variable *name*.
4. Overload the '+' operator to concatenate the *name* of two objects.
5. Create two different objects with different names.
6. Take user input for the names of those two objects.
7. Add the value of the *name* of both objects and print it.

 **[Submission]** 

- Turn in this assignment with your repl link.

### Solution

```cpp
#include <iostream>
using namespace std;

class Player
{
    private:
      string name;
  
    public:
      Player(string _name)
      {
          name = _name;
      }
  
      string operator + (Player _p1)
      {
          return this->name + _p1.name;
      }
};

int main() 
{
    string tempName;
    
    cout<<"Enter Player1 Name"<<endl;
    cin >> tempName;
    Player player1(tempName);
    
    cout<<"Enter Player2 Name"<<endl;
    cin >> tempName;
    Player player2(tempName);
  
    cout << player1 + player2;  
}
```
</details>


<details>
  <summary markdown="span">Chapter 6 - Assignment - 2 - Invert Text Case (Bonus)</summary>

**[Task] - Write a program to convert lowercase into uppercase and vice-versa for every character in a string.**

1. Take a string as an input from the user.
2. Perform the above task.
3. Print the converted string.
4. Example:-
    1. Input    :- "abcdef"<br>
    Output :- "ABCDEF"
    2. Input    :- "AbCdEf"<br>
    Output :- "aBcDeF"

 **[Submission]** 

- Turn in this assignment with your repl link.

### Solution

```cpp
#include <iostream>
using namespace std;
const int diffCase = 32;
const int capitalLetterStart = 65;
const int capitalLetterEnd = 90;
const int smallLetterStart = 97;
const int smallLetterEnd = 122;

void InvertTextCase(string &word)
{
    for(int i = 0; i < word.length(); i ++)
    {
        if(int(word[i]) >= capitalLetterStart && int(word[i]) <= capitalLetterEnd)
        {
            word[i] = int(word[i]) + diffCase;
        }
        else if(int(word[i]) >= smallLetterStart && int(word[i]) <= smallLetterEnd)
        {
            word[i] = int(word[i]) - diffCase;
        } 
    }
    cout <<endl << "Invert Text Case of String : "<< word;
}

int main() 
{
    string tempWord; 
    cout << "Enter The String : ";
    getline(cin,tempWord);
  
    InvertTextCase(tempWord);  
}
```
</details>

