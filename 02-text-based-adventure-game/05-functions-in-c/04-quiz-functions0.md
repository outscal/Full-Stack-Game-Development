# Quiz - Functions

Quiz - Functions


## Questions


### Q1. Which of the following is the correct way of defining a function in C++?

1. void fun() {}
2. void function(int a, int b) {}
3. int func() { return -1; }
4. int func(double x) { return 0.0; }
- 1, 2, 4
- 1, 2, 3, 4
- 2, 3
- 1, 2, 3 **(correct)**

### Q2. In which return type, no value is returned from function?
- int
- void **(correct)**
- char
- double

### Q3. Which keyword is used to terminate the execution of function and return the control to the calling function?
- main
- continue
- break
- return **(correct)**

### Q4. Given the code:

void func() {
    int x = 5;
    if (x > 0) {
        int y = 10;
        cout << y << endl;
    }
    cout << y << endl;
}


What will happen when func() is executed?
- Compilation error due to conflicting variable names **(correct)**
- 10 followed by a compilation error
- 10 followed by a value printed as garbage
- 10 followed by a runtime error

### Q5. int z = 50;
void func() {
    int z = 20;
    cout << z << endl;
}



What will be printed when func() is called?
- 20 **(correct)**
- 50
- Compilation error due to conflicting variable names
- Runtime error due to a conflict in variable types
