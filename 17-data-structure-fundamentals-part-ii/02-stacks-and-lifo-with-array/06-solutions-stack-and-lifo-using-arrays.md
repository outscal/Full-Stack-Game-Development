# Implementation - Stack using Array 


<details>
<summary>Assignment - 1 - Two stacks using an Array</summary>
<p>


**[Task] - Implement two stacks using a single array.**

- Create the following functions:-
    1. push1(int x) - pushes x to first stack
    2. push2(int x) - pushes x to second stack
    3. pop1() - pops an element from the first stack and return the popped element
    4. pop2() - pops an element from the second stack and return the popped element
    5. getTop1() - return the topmost element of stack1
    6. getTop2() - return the topmost element of stack2
- **Note:-**
    1. Implementation should be space-efficient.
    2. Also, check the conditions of overflow and underflow while push & pop.
    3. Elements of one stack should not be inserted by removing elements of other stack.

**[Submission]**

- Turn in this assignment with your repl link.

Solution

```cpp
#include <iostream>
using namespace std;

#define size 10

class Stack
{
  private:
    int* arr;
    int top1, top2;

  public:   
   
    Stack()
    {
      arr = new int[size];
      top1 = -1;        
      top2 = size;
    }

    void push1(int _data)
    {
      if(top1 + 1 == top2 )
      {
        cout << "Stack OverFlow ";
        return;
      } 
      else 
      {        
        arr[++top1] = _data;
      }
    }

    void push2(int _data)
    {
      if(top1 + 1 == top2 )
      {
        cout << "Stack OverFlow ";
        return;
      } 
      else 
      {        
        arr[--top2] = _data;        
      }
    }
    

    int pop1()
    {
      if(!isEmpty1())
      {
        int x = arr[top1];
        top1--;
        return x;      
      } 
      else 
      {
        cout << "Stack Is Empty";
      }
    }

    int pop2()
    {
      if(!isEmpty2())
      {
        int x = arr[top2];
        top2++;
        return x;      
      } 
      else 
      {
        cout << "Stack Is Empty ";
      }
    }

    bool isEmpty1()
    {
      return top1 == -1;
    }

    bool isEmpty2()
    {
      return top2 == size;
    }

    int getTop1()
    {
      return arr[top1];
    }

    int getTop2()
    {
      return arr[top2];
    }

    void print1()
    {
      int i = top1;
      cout << endl << "Stack 1 Elements : " << endl;
      while(i >= 0)
      {
        cout << arr[i] << endl;
        i--;
      }
      cout << endl;
    }

    void print2()
    {
      int i = top2;
      cout << endl << "Stack 2 Elements : " << endl;
      while(i < size)
      {
        cout << arr[i] <<endl;
        i++;
      }
      cout << endl;
    }

};

int main() {
  Stack *st = new Stack();

  cout <<"==========Stack 1 Operations============" << endl;
  st->push1(10);
  st->push1(20);
  st->push1(30);
  st->push1(40);
  st->push1(50); 

  st->print1();

  cout <<  "Top Element of Stack 1: " << st->getTop1() << endl;

  cout << st->pop1() << " Removed from Stack 1" << endl << endl;
  st->print1();

  cout<<endl <<"==========Stack 2 Operations===========" << endl;

  st->push2(10);
  st->push2(20);
  st->push2(30);
  st->push2(40);
  st->push2(50); 

  st->print2();

  cout <<  "Top Element of Stack 2: " << st->getTop2() << endl;

  cout << st->pop2() << " Removed from Stack 2" << endl;
  st->print2();
  
}
```

</p>
</details>
<br>
<details>
<summary>Assignment - 2 - Prefix to infix (Bonus)</summary>
<p>


**[Task] - Given a Prefix expression, convert it into an Infix expression.**

- Example -
    1. Input - "*+AB-CD" <br>
    Output - "((A+B)*(C-D))"
    2. Input - "-A/BC-/AKL" <br>
    Output - "((A-(B/C))*((A/K)-L))"

**[Submission]**

- Turn in this assignment with your repl link.

Solution

```cpp
#include <iostream>
using namespace std;

#define MAX 100

class Stack
{
  private:
    string *arrStack;
    int top;

  public:
    Stack()
    {
        arrStack = new string[MAX];
        top = -1;
    }

    void push(string _data)
    {
        if(top >= MAX -1)
        {
          cout << "Stack OverFlow ";
        } 
        else 
        {   
          arrStack[++top] = _data;
        }
    }

    string pop()
    {
        if(isEmpty())
        {
          cout << "Stack is Empty ";
        } 
        else 
        {
          string x = arrStack[top];
          top--;
          return x; 
        }          
    }

    bool isEmpty()
    {
        return (top < 0);
    }

    string getTop()
    {
        return arrStack[top];
    }
};

bool isoperator (char c)
{
    switch(c)
    {
      case '+' : 
      case '-' : 
      case '*' : 
      case '/' : 
        return true; 
      default:
        return false;
    }
}

string PrefixToInfix (string exp)
{
    Stack *st = new Stack();
    
    for(int i = exp.length() - 1 ; i >= 0; i--)
    {
      if(isoperator(exp[i]))
      {
          string op1 = st->pop();
          string op2 = st->pop();
          string temp = "(" + op1 + exp[i] + op2 + ")";
          st->push(temp);
      }      
       else 
      {
          string temp;
          temp.append(1,exp[i]);
          st->push(temp);        
      } 
    }
    return st->getTop();     
}

int main() 
{
   string exp = "*-A/BC-/AKL";
   cout << "Prefix To InfiX : " << PrefixToInfix(exp);
}
```

</p>
</details>
<br>
<details>
<summary>Assignment - 3 - Implement Stack functions</summary>
<p>


**[Task] -** 

- Implement a stack that supports the following operations in O(1) time complexity:-
    1. push() - pushes an element to the top of the stack.
    2. pop() - removes an element from the top of the stack and return it.
    3. findMiddle() - return middle element of the stack.
    4. deleteMiddle() - delete the middle element

**[Submission]**

- Turn in this assignment with your repl link.

Solution

```cpp
#include <iostream>
using namespace std;

class Node
{
  public :
    int data;
    Node* next;
    Node* prev;
};

class DoublyLinkedList
{
  private :
    Node* top;
    Node* mid;
    int count;
  
  public :
    
    DoublyLinkedList()
    {
      top = NULL;
      mid = NULL;
      count = 0;
    }

    void push(int value)
    {
      Node* newNode = new Node();
      newNode->data = value;
      newNode->next = NULL;
      newNode->prev = NULL;

      if(newNode == NULL)
      {
        cout<<"Stack Overflow";
        exit(1);
      }
      
      if(top == NULL)
      {
        top = newNode;
        mid = newNode;
        count++;
      }
      else
      {
        newNode -> next = top;
        top -> prev = newNode;
        top = top -> prev;
        count++;
        if(count%2 == 0)
        {
          mid = mid->prev;
        }
      }
    }

    int pop()
    {
      Node* temp = top;
      int value =temp->data;

      if ( top == NULL)
      {
          cout<<"Stack Underflow"<<endl;
          exit(1);
      }      
      else
      {
        top = top -> next;
        count--;
        if(count % 2 != 0)
        {
          mid = mid -> next;
        }
        delete temp;
      }
       return value;
    } 

    int getMid()
    {    
      return mid->data;
    }

    void removeMid()
    {
      Node* tempM = mid;

      if(mid -> next == NULL)
      {
        tempM =NULL;
        top = NULL;
        count = 0 ;

        delete tempM;
      }
      else if (mid -> prev == NULL && top == mid)
      {
        top = top -> next;
        count--;
        mid = mid -> next;
        top -> prev = NULL;
        delete tempM; 
      }
      else
      {
        Node* pre = mid -> prev;
        Node* nex = mid -> next;

        pre -> next = nex;
        nex -> prev = pre;
        count--;
        
        if(count%2 == 0)
        {
          mid = pre;
        }
        else
        {
          mid = nex;
        }
       delete tempM;
      }
    }

    void display()
    {
      if(top == NULL)
      {
        cout<<"Stack Underflow";
        exit(1);
      }

      Node* temp = top;
      while(temp != NULL)
      {
        cout<<temp->data<<"->";
        temp = temp -> next;
      }
    }
};

class Stack
{
  private :
    DoublyLinkedList* dl;

  public :

   Stack()
   {
      dl =  new DoublyLinkedList();
   }

   void push(int value)
   {
     dl->push(value);
   }

   int pop()
   {
      return dl->pop();
   }

   int getMid()
   {
      if ( dl->getMid() == 0)
      {
        cout<<"Error :Stack is Empty"<<endl;
      }
      return dl->getMid();
   } 

   void removeMiddle()
   {
     dl->removeMid();
   }

   void Display()
   {
     dl->display();
   }
};

int main() 
{
  Stack* st = new Stack();

  st->push(1);
  st->push(2);
  st->push(3);
  st->push(4);
  st->push(5);
  st->push(6);
  st->push(7);

  cout<<"Popping the element "<<st->pop();

  cout<<"\nMid is "<<st->getMid();
  cout<<endl;

  st->Display();
  cout<<endl;

  st->removeMiddle();
  cout<<endl;  
  st->Display();

  st->removeMiddle();
  cout<<endl;  
  st->Display();
}
```

</p>
</details>
<br>
