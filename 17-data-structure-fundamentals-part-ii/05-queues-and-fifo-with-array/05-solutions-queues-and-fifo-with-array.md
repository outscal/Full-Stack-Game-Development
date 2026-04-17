# **Queues with FIFO and Array - Solution**



Implementation - 1 - Queue using Array

```cpp
#include <iostream>
using namespace std;

template <typename  T>
class Queue
{
  private :
    int front;
    int rear;
    int size;
    T arr1[6];
    
  public :

   Queue()
   {  
      size = 0;
      front = -1; 
      rear = -1;
   }

   bool isEmpty()
   {
     if((rear == front && rear==-1) || front > rear)
     {
        return true;
     }
     return false;
   }

   bool isFull()
   {
     if(rear == 5)
     {
        return true;
     }
     return false;
   }

   void enqueue(T value)
   {
      if(isFull())
      { 
        cout<<"Queue is Full";
      }
      else
      {
        if(front == -1)
        {
          front = 0 ;
        }
        rear ++;
        size++;
        arr1[rear] = value;
      }
   }

   T dequeue()
   {
      T v  = -1;
      if(isEmpty())
      { 
        cout<<"Queue is Empty";
      }
      else
      {
        v = arr1[front];
        front ++;
        size --;
      }
      return v;
   }

    T getFront()
    {
      return arr1[front];
    }

    int getSize()
    {
      return size;
    }

    void displayQueue()
    {
      for(int i = front; i<=rear; i++)
      {
        cout<<arr1[i]<<"-";
      }
    }

};

int main() 
{
   Queue<int>* queue = new Queue<int>();

   queue->enqueue(1);
   queue->enqueue(2);
   queue->enqueue(3);
   queue->enqueue(4);
   queue->enqueue(5);
   queue->enqueue(6);
  

  queue->displayQueue(); 
  
  cout<<endl;   
  cout<<"Dequeuing element : "<<queue->dequeue()<<endl;
  cout<<"Dequeuing element : "<<queue->dequeue()<<endl;
  cout<<"Dequeuing element : "<<queue->dequeue()<<endl;
  cout<<"Dequeuing element : "<<queue->dequeue()<<endl;

  cout<<endl;
  queue->displayQueue(); 

 cout<<"\nSize of  queue is "<<queue->getSize();
}
```



Assignment - 1 - Queue traversal

```cpp
#include <iostream>
#include <queue>
using namespace std;

void showQueue(queue<int> *q)
{
    while(!q->empty())
    {
      cout<<q->front()<<"-";
      q->pop();
    }
    cout<<endl;
}

int main() 
{
  queue<int> q;
  q.push(10);
  q.push(20);
  q.push(30);
  q.push(40);
  q.push(50);

  showQueue(&q);
}
```



Assignment - 2 - Stack using Queue (Bonus)

```cpp
#include <iostream>
#include <queue>
using namespace std;

class Stack
{
    queue<int>q;
public:
    void push(int val);
    void pop();
    int top();
    bool empty();
};
 
// Push operation
void Stack::push(int val)
{
    //  Get previous size of queue
    int s = q.size();
 
    // Push current element
    q.push(val);
 
    // Pop (or Dequeue) all previous
    // elements and put them after current
    // element
    for (int i=0; i<s; i++)
    {
        // this will add front element into
        // rear of queue
        q.push(q.front());
 
        // this will delete front element
        q.pop();
    }
}
 
// Removes the top element
void Stack::pop()
{
    if (q.empty())
        cout << "No elements\n";
    else
        q.pop();
}
 
// Returns top of stack
int  Stack::top()
{
    return (q.empty())? -1 : q.front();
}
 
// Returns true if Stack is empty else false
bool Stack::empty()
{
    return (q.empty());
}
 
// Driver code
int main()
{
    Stack s;
    s.push(10);
    s.push(20);
    cout << s.top() << endl;
    s.pop();
    s.push(30);
    s.pop();
    cout << s.top() << endl;
    return 0;
}
```
