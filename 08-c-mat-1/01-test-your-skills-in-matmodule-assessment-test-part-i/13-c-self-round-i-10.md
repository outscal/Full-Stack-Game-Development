<div style="margin: auto 5%">
<div style = "text-align: center">
<h1><strong>IP(Interview Preparation)-Self-Round- I - Assignment 10</strong></h1>
</div>
<p><strong>[Instructions]</strong></p>
<ul>
<li>Attach a single video answering all questions. Use any preferred software to record.</li>
<li>It is mandatory for you to turn on your camera while answering the questions.</li>
<li>Time Limit of the video: 5 Min.</li>
<li>Submit the link to that recorded video.</li>
<li>Any link containing the video, eg. Youtube, loom, drive, etc, is fine.</li>
</ul>
<br><br>
<p><strong>[Questions]</strong></p>
<ol>
<li>Explain what will the output of the program and why?</li>

```cpp
#include <iostream>
using namespace std;

class Calculator
{
public:
   Calculator()
   {
     cout<<"Calculator Class Default Constructor"<<endl;
   }
   Calculator(int x)
   {
     cout<<"Calculator Class custom/paramaterized Constructor"<<endl;
   }

   ~Calculator()
   {
     cout<<"Calculator Class Default Destructor"<<endl;
   }
	 ~Calculator(int x)
   {
     cout<<"Calculator Class custom/paramaterized Destructor"<<endl;
   }

};

class Add : Calculator
{
public:
   Add()
   {
     cout<<"Add Class Default Constructor"<<endl;
   }

    Add(int x) : Calculator(x)
   {
     cout<<"Add Class custom/paramaterized Constructor"<<endl;
   }

	 ~Add()
   {
     cout<<"Add Class Default Destructor"<<endl;
   }

   ~Add(int x)
   {
     cout<<"Add Class custom/paramaterized Destructor"<<endl;
   }
};
int main()
{
  Add objAdd(10);
  return 0;
}
```

</li>
</ol>

<p><strong>[Submission Instructions]</strong></p>
<ul>
<li>Submit the link to that recorded video.</li>
<li>Any link containing the video, eg. Youtube, loom, drive, etc, is fine.</li>
</ul>

</div>
