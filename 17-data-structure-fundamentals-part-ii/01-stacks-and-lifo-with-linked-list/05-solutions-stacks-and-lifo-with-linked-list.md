# **Stack and LIFO with Linked list - Solution**



**Chapter 16 - Assignment - 2 - Infix to postfix**

```cpp
#include <iostream>
using namespace std;

class Node
{
  public:
    char data;
    Node *next;
};

class StackLL
{
  private:
    Node *Top;
    
  public:
    StackLL()
    {
      Top = NULL;
    }

    Node * getHead()
    {
      return Top;
    }

    void Push(char _data)
    {
      Node *node = new Node();
      node->data = _data;
      node->next = NULL;
  
      if(Top != NULL)
      {
        node->next = Top;
      }
      Top = node;
    }

    char Pop()
    {
      char character = getTop();
      Node *node = Top;
      Top = node->next;
      
      delete node;    
      return character;
    }

    char getTop()
    {
      return Top->data;
    }
  
    bool IsEmpty()
    {
      return (Top == NULL);
    }

    void Display()
    {
      Node *node = new Node();
      node = Top;
      cout <<endl;
      while(node != NULL)
      {
        cout << node->data << endl;
        node = node->next;
      }
    }
};
    
bool IsOperator(char temp)
{
  if(temp == '+' ||
     temp == '-' ||
     temp == '*' ||
     temp == '/' ||
     temp == '^')
     return true;      
  else return false;      
}

int CheckPrecedence(char temp)
{
  switch(temp)
  {
    case '^':            return 3;
    case '*': case '/':  return 2;
    case '+': case '-':  return 1;
    default : return -1;        
  }
}

string InfixToPostfix(string exp)
{
  StackLL *st = new StackLL();
  string postfix; 
      
  for(int i = 0; i < exp.length(); i++)
  {
    if(exp[i] >= 'a' && exp[i] <= 'z' || 
       exp[i] >= 'A' && exp[i] <= 'Z' || 
       exp[i] >= '0' && exp[i] <= '9')
    {
      postfix += exp[i];  
    } 
    else if(exp[i] == '(')
    {
        st->Push(exp[i]);            
    } 
    else if(exp[i] == ')')
    {
      while(st->getTop() != '(' && !st->IsEmpty())
      {
        postfix += st->Pop();
      }
      if(st->getTop() == '(')
      {
        st->Pop();
      }
    } 
    else 
    {
      while(!st->IsEmpty() && CheckPrecedence(exp[i]) <= CheckPrecedence(st->getTop()))
      {
        postfix += st->Pop();
      }
      st->Push(exp[i]);
    }                    
  }  
  
  while(!st->IsEmpty())
  {
    postfix += st->Pop();
  }
  return postfix;
}


int main() 
{
  string expression = "a+b*(c^d-e)^(f+g*h)-i";  
  cout << "Infix To PostFix : " << InfixToPostfix(expression); 
}
```
