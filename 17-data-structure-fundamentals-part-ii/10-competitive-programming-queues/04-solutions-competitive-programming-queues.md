# **Competitive programming - Queues - Solution**



Problem 1

```cpp
#include <bits/stdc++.h> 
using namespace std; 

int remainingCard(int n) 
{ 
  // creating a queue named as queCards which will
  // store the cards
    queue<int> queCards;
 
    // Inserting all the numbers from 1 to n
    for (int i = 1; i <= n; i++)
        queCards.push(i);
 
    // While there are at least two
        //elements in the queue
    while (((int)queCards.size()) >= 2) {
        // Push the front element at the back
        queCards.push(queCards.front());
        // Remove the front element
        queCards.pop();
        // Remove another element
        queCards.pop();
    }
    // Return the only element left in the queue
    return queCards.front();
} 

int main() 
{ 
    int n; 
  cin >> n;
    cout << remainingCard(n); 

    return 0; 
}
```



Problem 2

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
  int n;
  cin>>n;
  // Declaring the queue
  queue<int>KiraQ;
  // running loop for multiple testcases
    while(n--){
    // taking our choice
      char ch;
    cin>>ch;
    if(ch == 'E') {
      // taking the element
      int x;
      cin>>x;
      KiraQ.push(x);
      cout<<KiraQ.size()<<"\n";
    }
    else if(ch == 'D') {
      // printing the elemernt
        if(KiraQ.size() == 0) {
          cout<<"-1 0\n";
        }
        else {
        cout<<KiraQ.front()<<" "<<KiraQ.size()-1<<"\n";
        KiraQ.pop();
      }
    }
    else {
      // if something aside from E and D is placed
      cout<<"Wrong choice\n";
    }
  }
  return 0;
}
```



Problem 3

```cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long
int main()
{
  ll n,x,product=1;
  cin>>n ;
  priority_queue<ll,vector<ll>,greater<ll>> pq;
  for(int i=0;i<n;i++) {
    cin>>x;
    if(pq.size()==3) {
      if(x>pq.top()) {
        product=(product/pq.top())*x;
        cout<< product <<endl;
        pq.push(x);
        pq.pop();
      }
      else 
        cout<<product<<endl;
    }
    else {
      pq.push(x);
      product*= x;
      if(pq.size()!=3) 
        cout<<-1<<endl;
      if(pq.size()==3 )         
        cout<<product<<endl;
    }
  }
  return 0;
}
```
