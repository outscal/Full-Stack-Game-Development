# **Types of Queues - Circular Queue - Solution**



Implementation - 1 - Circular queue using Array

```cpp
#include <iostream>
using namespace std;
const int arrSize = 5;

class Queue
{
private:
    int arr[arrSize];
    int front;
    int rear;
public:
    Queue()
    {
        front = rear = -1;
    }

    void enQueue(int _data)
    {
        if (front == rear + 1   || 
        rear == arrSize - 1 && 
        front == 0)
        {
            cout << "Queue is Full" << endl;
            cout << "No Space left in the Array to add " << _data << endl;
        }
        else if (front == -1 && rear == -1)    // for the first the elements
        {
            front = rear = 0;
            arr[rear] = _data;
        }
        else if(rear == arrSize-1) // when the array is full 
        {
            rear = 0;
            arr[rear] = _data;
        }
        else                      // for the other elements other than first
        {
            rear++;
            arr[rear] = _data;
        }
    }

    void deQueue()
    {
        if (front == -1 && rear == -1)
        {
            cout << "Queue is Empty" << endl;
            cout << "Cannot able to DeQueue" << endl;
        }
        else if (front == rear)    // for the first element to remove
        {
            cout << arr[front];
            front = rear = -1;
        }
        else if (front == arrSize - 1)  //for last elements in array
        {
            cout << arr[front];
            front = 0;
        }
        else           // for other elemets 
        {
            cout << arr[front];
            front++;
        }
    }

    void Display()
    {
        if (front == -1 && rear == -1)
        {
            cout << "\nQueue is empty"<<endl;
        }
        else if (rear >= front)
        {
            cout << "\nElements in the queue:" << endl;
            for (int i = front; i <= rear; i++)
            {
                cout << arr[i] << " ";
            }
            cout << endl;
        }
        else
        {
            cout << "\nElements in the queue:" << endl;
            
            for (int k = front; k <= arrSize - 1; k++)
            {
                cout << arr[k] << " ";
            }
      for (int j = 0; j <= rear; j++)
            {
                cout << arr[j] << " ";
            }
            cout << endl;
        }
    }
};

int main()
{
    Queue* Q = new Queue();
    for (int i = 1; i <= arrSize; i++)
    {
        Q->enQueue(i);
    }
  
    Q->Display();
    cout << endl;
    cout << "Dequeue: "; Q->deQueue(); cout << endl;
    cout << "Dequeue: "; Q->deQueue(); cout << endl;
    Q->Display();

  cout << "Dequeue: "; Q->deQueue(); cout << endl;
    Q->enQueue(10);
    Q->enQueue(20);
  Q->enQueue(30);
  Q->Display();	

  cout << "Dequeue: "; Q->deQueue(); cout << endl;
    cout << "Dequeue: "; Q->deQueue(); cout << endl;
  cout << "Dequeue: "; Q->deQueue(); cout << endl;
    cout << "Dequeue: "; Q->deQueue(); cout << endl;
  cout << "Dequeue: "; Q->deQueue(); cout << endl;
  Q->Display();	 
}
```



Implementation - 2 - Circular queue using linked list

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

    int Remove()
    {
      Node *node = head;
      int temp = node->data;      
      head = node->next;
      delete node;
      return temp;
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
      int front;
      int rear;

  public:
      Queue()
      {
      ll = new LinkedList();
          front = rear = -1;
      }

      void enQueue(int _data)
      {
          ll->Add(_data);
      rear++;
      }

      int deQueue()
      {
      rear--;
      int temp = ll->Remove(); 
          return temp;
      }
  
    bool isEmpty()
    {
      return front == rear;
    }
  
      void Display()
      {
          ll->Display();
      }
};

int main()
{
    Queue* Q = new Queue();
    for (int i = 1; i <= 5; i++)
    {
        Q->enQueue(i);
    }
  
    Q->Display();
    cout << endl;
    cout << "Dequeue: " << Q->deQueue(); cout << endl;
    cout << "Dequeue: " << Q->deQueue(); cout << endl;
    Q->Display();

    Q->enQueue(10);
    Q->enQueue(20);
  Q->Display();	

  cout << "Dequeue: " << Q->deQueue(); cout << endl;
    cout << "Dequeue: " << Q->deQueue(); cout << endl;
  cout << "Dequeue: " << Q->deQueue(); cout << endl;
  cout << "Dequeue: " << Q->deQueue(); cout << endl;
  cout << "Dequeue: " << Q->deQueue(); cout << endl;
  Q->Display();	  
}

```
