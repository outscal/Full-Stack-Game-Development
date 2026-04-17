# **Types of Queues - Priority Queue - Solution**



Implementation - 1 - Priority queue using Array

```cpp
#include <iostream>
using namespace std;

struct item 
{
    int data;
    int priority;
};

 class Queue 
{
  private:  
    int front, rear, count;
    item *arr;

  public:
    Queue(int c)
    {
      front = 0;
      rear = 0;
      count = c;
      arr = new item[count];
    }
    
    void push(int data, int priority)
    {
      if(count == rear)
      {
        cout <<"Queue is Full" << endl;
      } 
      else 
      {
        arr[rear].data = data;
        arr[rear].priority = priority;
        rear++;
      }
      sortArrayByPriority(arr);            
    }

    void sortArrayByPriority(item *arr)
    {
      for(int i = 0; i < rear-1; i++)
      {
        for(int j = i+1; j <rear; j++)
        {
          if(arr[i].priority < arr[j].priority)
          {
            item temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;               
          }
        }
      }
    }

    item pop()
    {
      if(isEmpty())
      {
        cout <<"Queue is Empty"<< endl;
      } 
      else 
      {
        item temp = arr[front];        
        for(int i = 0; i < rear - 1; i++)
        {
          arr[i] = arr[i+1];
        }  
        rear--; 
        return temp;
      }      
    }

    item getFront()
    {
      return arr[front];
    }

    bool isEmpty()
    {
      return front == rear;
    }

    void display()
    {
      for(int i = front; i < rear; i++)
        cout << arr[i].priority << "->"<< arr[i].data << endl;
    }    
};

int main() 
{
  Queue *q = new Queue(10);

  q->push(10,2);
  q->push(20,5);
  q->push(30,1);
  q->push(40,5);
  q->push(50,3);

  q->display();

  item temp = q->pop();
  cout << "Removed From Queque " << temp.data << " " << temp.priority << endl;

 temp = q->getFront();
 cout << "Front Of Queque " << temp.data << " " << temp.priority << endl;
  
  cout << endl;
  q->display(); 
}
```
