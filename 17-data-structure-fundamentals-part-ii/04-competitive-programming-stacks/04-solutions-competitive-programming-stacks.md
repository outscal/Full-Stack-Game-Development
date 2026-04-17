# **Competitive programming - Stacks - Solution**



Problem 1

```cpp
vector<int> commonPrefix (vector<int> nums1,vector<int> nums2) {
      int n = nums2.size();
        stack<int> s;
        map<int, int> ans_nums2;

                //iterate from last to first element in the vector nums2
        for(int i = n - 1; i >= 0; i--) {
                        //keep popping elements out from stack until stack is
                        //empty or the top element of stack has value greater
                        //than nums2[i]
            while(s.size() && s.top() < nums2[i]) {
                s.pop();
            }
                        //now the top element of stack will be the next greater
                        //element of nums2[i]
            if(s.empty()) {
                                //No greater element exist for nums2[i]
                ans_nums2[nums2[i]] = -1;
            } else {
                ans_nums2[nums2[i]] = s.top();
            }
            s.push(nums2[i]);
        }
        vector<int> ans(nums1.size());
        for(int i = 0; i < nums1.size(); i++){
            ans[i] = ans_nums2[nums1[i]];
        }
        return ans;
 }
```



Problem 2

```cpp
vector<int> temperatures(vector<int> temperatures) {
    stack<int> s;
    int n = temperatures.size();
    vector<int> ans(n);

        //iterate from last to first element in the vector temperatures
    for (int i = n - 1; i >= 0; i--) {
                //keep popping elements out from stack until stack is
                //empty or the top element of stack has value greater
                //than or equal to temperatures[i]
        while (s.size() && temperatures[i] >= temperatures[s.top()]) {
            s.pop();
        }
        if (s.empty()) {
            ans[i] = 0;
        } else {
            ans[i] = s.top() - i;
        }
        s.push(i);
    }
    return ans;
}


```



Problem 3

```cpp
int game(vector<string> ops) {
    stack<int> s;
    int n = ops.size();
    int ans = 0;
    for (int i = 0; i < n; i++) {
        if (ops[i] == "+") {
                        //Pushing last two elements which are present at the
                        //top of stack into the stack
            int a = s.top();
            s.pop();
            int b = s.top();
            s.push(a);
            ans += a + b;
            s.push(a + b);
        } else if (ops[i] == "D") {
                        //Pushing twice of the value present at the top of the
                        //stack into the stack
            int a = s.top();
            a *= 2;
            ans += a;
            s.push(a);
        } else if (ops[i] == "C") {
                        //Popping the top element of the stack
            int a = s.top();
            s.pop();
            ans -= a;
        } else {
                        //Pushing the element ops[i] into the stack
                        //stoi function converts a string to an integer
            int x = stoi(ops[i]);
            ans += x;
            s.push(x);
        }
    }
    return ans;
}


```
