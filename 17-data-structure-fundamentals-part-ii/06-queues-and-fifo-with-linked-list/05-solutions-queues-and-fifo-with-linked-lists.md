# **Queues and FIFO Using Linked List - Solution**





Implementation - 1 - Queue using linked list

```cpp
#include <iostream>
using namespace std;

class Node
{
  public:
    int data;
    Node *next;
};

class LinkedList
{
  private:
    Node *head;

  public:
    LinkedList()
    {
      head = NULL;
      last = NULL;
    }

    Node *getHead()
    {
      return head;
    }

    void Add(int _data)
    {
      Node *node = new Node();
      node->data = _data;
      node->next = NULL;

      if(head == NULL)
      {
        head = node;
      } 
      else 
      {
        Node *temp = head;

        while(temp->next != NULL)
        {
          temp = temp->next;
        }
        temp->next = node;
      }      
    }

    void Remove()
    {
      Node *node = head;
      head = node->next;
      
      delete node;
    }

    void Display()
    {
      Node *node = head;

      while( node != NULL)
      {        
        cout << node->data << " ";
        node = node->next;
      }
      cout << endl;
    }
};

class Queue
{
  private:
    LinkedList *ll;
    int front, rear;

  public:
    Queue()
    {
      ll = new LinkedList();
      front = 0;
      rear = 0;
    }

    void push(int x){
      ll->Add(x);
      rear++;
    }

    int pop(){
      if(isEmpty()){
        cout << "Queue Is Empty " << endl;
      } else {
        int temp = ll->getHead()->data;
        ll->Remove();
        rear--;
        return temp;      
      }
    }

    void display(){
      ll->Display();
    }

    int getFront(){
      return ll->getHead()->data;
    }

    int getSize(){
      return rear;
    }

    bool isEmpty(){
      return front == rear;
    }
};

int main() {
  Queue *q = new Queue();

  q->isEmpty() ? cout << "Queue Empty " : cout << "Queue Is Not Empty";
  cout << endl;
  q->push(10);
  q->push(20);
  cout << "Removing : " << q->pop() << endl;
  q->push(30);
  q->push(40);

  q->display();

  q->isEmpty() ? cout << "Queue Empty " : cout << "Queue Is Not Empty";
   cout << endl;

  cout << "Size of Queue : " << q->getSize();
}
```



Assignment - 1 - Queue using stack

```cpp
#include <iostream>
#include <stack>
using namespace std;

class Queue
{
  private:
    stack<int> st1, st2;
    int front, rear;

  public:
    Queue()
    {
      front = 0;
      rear = 0;
    }

    void push(int data)
    {
      while(!st1.empty())
      {
        st2.push(st1.top());
        st1.pop();
      }
      
      st1.push(data);

      while(!st2.empty())
      {
        st1.push(st2.top());
        st2.pop();
      }
      rear++;
    }

    int pop()
    {
      if(isEmpty())
      {
        cout << "Queue is empty" << endl;
      } 
      else 
      {
        int temp = st1.top();
        st1.pop();
        rear--;
        return temp;
      }      
    }

    void display()
    {
      while(!isEmpty())
      {
        cout << st1.top() << " ";
        st1.pop();
        rear--;
      }
    }

    bool isEmpty()
    {
      return rear == front;
    }
};

int main() 
{
  Queue *q = new Queue();

  q->push(10);
  q->push(20);
  q->push(30);
  q->push(40);
  q->push(50);

  cout << q->pop() << " Popped From Queue " << endl;
  q->display();
}
```
