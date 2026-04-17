# **Solutions - Generics And Templates**

<details>

**<summary>Chapter 7 - Assignment 1 - Generic Functions</summary>**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

**[Tasks]**

1. Create a generic function to add a score where you are passing two arguments/parameters, one is the current score and another is a score that needs to be added to the current score.
2. Return the sum of the two values in the same type as the type of data passed into the function.
3. Print out gamified console message when the score is getting added. 
4. Inside main(), call this function 2 times to do the following tasks :
    1. Take two integers from the user and print their sum.
    2. Take two float value inputs from the user and print their sum.

Code-

```cpp
#include <iostream>

template <typename T>
T AddScore(T currentScore, T scoreToBeAdded)
{
	return currentScore + scoreToBeAdded;
}


int main() 
{
  int currentScore, scoreToBeAdded;
  float score, scoreAdded;
  std::cout << "Please enter 2 values of integer type:";
  std::cin >> currentScore >> scoreToBeAdded;
  std::cout << "\nAfter adding integer type:" << AddScore(currentScore, scoreToBeAdded);
  std::cout << "\nPlease enter 2 values of float type:";
  std::cin >> score >> scoreAdded;
  std::cout << "\nAfter adding float type:" << AddScore(score, scoreAdded);
}
```

</details>

<details>

**<summary>Chapter 7 - Assignment 2 - Generic Class</summary>**

**[Note]** 

- This solution is to push you towards the best solution and to improve your overall code quality.
- Do not help your lagging friend with this solution if you are a true friend of him/her.

**[Tasks]**

1. Create a generic class ***SpecialAbility*** with one generic private member variable **attackStrength**.
2. Define a member function *performSpecialAbility*() to return the attackStrength. 
3. Create two objects of ***SpecialAbility*** class with the int and float data types and take user input to set the variable of **attackStrength**
4. Call *performSpecialAbility*() in each case to print the damage delivered.
5. Add a cool gamified message to make the assignment exciting.

Code-

```cpp
#include <iostream>
using namespace std;

template < class T >
class SpecialAbility
{
  T attackStrength;

  public:

    SpecialAbility(T arg1 ) 
    {
      attackStrength = arg1;
    }
    T performSpecialAbility()
    {
      return attackStrength;
    }
};

int main() 
{
  int a;
  float x;
  SpecialAbility<int> *sA1;
  SpecialAbility<float> *sA2;

  cout << "Enter Attack strength value of int type: ";
  cin>>a;
  sA1 = new SpecialAbility<int>(a);
  cout <<" Damage Done by 1st Enemy: " <<sA1->performSpecialAbility()<<endl;
  delete sA1;

  cout << "Enter Attack strength value of float type: ";
  cin>>x;
  sA2 = new SpecialAbility<float>(x);
  cout <<" Damage Done by 2st Enemy: " <<sA2->performSpecialAbility()<<endl;
  delete sA2;
 
}
```

</details>