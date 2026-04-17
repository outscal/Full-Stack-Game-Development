# **Chapter 7**

> **Note : Click on arrow to expand**







Chapter 7 - Assignment - 1 - Find duplicates

```cpp
#include <bits/stdc++.h>
using namespace std;

string FindDuplicate(string str)
{
      string ans="";
      vector<int>count(123,0);             //the corresponding indices at 65-90 will store frequency of a-z and 97-122 of A-Z
    for(int i=0;i<str.length();i++)
    {
        count[str[i]]++;
    }
    for(int i=65;i<=90;i++)
    {
        if(count[i]>1)
        ans.push_back(char(i));
    }
     for(int i=97;i<=122;i++)
    {
        if(count[i]>1)
        ans.push_back(char(i));
    }
    return ans;
}

int main()
{
      string str;
      cout<<"Enter String : ";
      cin>>str;
      cout<<"Duplicates : "<<FindDuplicate(str);
}


```



Chapter 7 - Assignment - 2 - Palindrome

```cpp
#include <algorithm>
#include <iostream>
using namespace std;

bool CheckPalindrome(string &s)
{
   int i=0,j=s.length()-1;       // using two pointers, one at the start and one at the end and keep comparing
     while(i<j)
     {
            if(s[i]!=s[j])
            return false;
            i++;
            j--;
   }
    return true;
}

int main()
{
    string str;
    cout << "Enter string : ";
    cin >> str;

    if(CheckPalindrome(str))
                cout << " YES ";
        else
                cout <<" No";
}


```



Chapter 7 - Assignment - 3 - Anagram

```cpp
#include <iostream>
using namespace std;

bool CheckAnagram(string &str1, string &str2)
{
    if(str1.length() != str2.length())
        return false;
                                                                      //both the below arrays will store the frequency of characters in the two strings
    int hashA[26] = {0};
    int hashB[26] = {0};

    for(int i = 0; i < str1.length(); i++)
    {
        hashA[int(str1[i]) - 97]++;
        hashB[int(str2[i]) - 97]++;
    }

    for(int i = 0 ; i < 26; i++)
    {
        if(hashA[i] != hashB[i])
        {
          return false;
        }
    }
    return true;
}

int main()
{
    string str1, str2;
    cout <<"Enter 1st String : ";
    cin >> str1;
    cout <<"Enter 2nd String : ";
    cin >> str2;
    cout << endl;
    CheckAnagram(str1, str2) ? cout <<"True" : cout <<"False";
}


```



Chapter 7 - Assignment - 4 - Character count

```cpp
#include <bits/stdc++.h>
using namespace std;

void CountCharacter(string str)
{
      vector<int>count(123,0);      // using ASCII value, we will store the frequency of letters in array
      int i=0;
      while(i<str.length())
      {
            count[str[i++]]++;
      }
      for(int i=65;i<=90;i++)
    {
        if(count[i]>0)
        cout<<char(i)<<" - "<<count[i]<<endl;
    }
     for(int i=97;i<=122;i++)
    {
        if(count[i]>0)
        cout<<char(i)<<" - "<<count[i]<<endl;
    }

}

int main()
{
      string input;
      cin>>input;
      CountCharacter(input);
}

```
