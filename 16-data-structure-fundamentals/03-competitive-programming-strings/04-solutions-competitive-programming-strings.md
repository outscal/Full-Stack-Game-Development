# **Chapter 8 -String Problems - Solution**



Reverse-Vowels-of-a-String

```cpp
class Outscal {
  public:
    string ReverseVowel(string s)
    {
        int i = 0;
            int j = s.size()-1;
            string vowels = "aeiouAEIOU";
            while(i < j) {
                while(vowels.find(s[i]) == string::npos && i < j) ++i;   //if the letter is not a vowel, move ahead
                while(vowels.find(s[j]) == string::npos && i < j) --j;
                if(i < j) swap(s[i++], s[j--]);
            }
            return s;
    }
};


```



First-Unique-Character-in-a-String

```cpp
class Outscal {
  public:
    int unique(string s)
    {
        int arr[26] = {0};

        for(int i=0;i<s.length();i++)
        {
           arr[s[i]-'a']++;
        }
        for(int i =0 ;i<s.length();i++)
        {
            if(arr[s[i]-'a'] ==1)
                return i;
        }
        return -1;
    }
};


```



Delete-Operation-for-Two-Strings

```cpp
class Outscal {
  public:
    int reverse(string a,string b)
    {
        string common = "";
        for(int j=0; j<b.length(); j++)
        {
            for(int i=0; i<a.length(); i++)
            {
                if(a[i] == b[j])
                {
                    common += a[i];
                    a[i] = '#';
                    b[j] = '#';
                    break;
                }
            }
        }

        int aLength =0, bLength =0;
        int i=0, j=0;
        while(i < a.length())
        {
            aLength += (a[i++]=='#')?0:1;
        }
        while(j<b.length())
        {
            bLength += (b[j++]=='#')?0:1;
        }

        return aLength + bLength;
    }
};


```
