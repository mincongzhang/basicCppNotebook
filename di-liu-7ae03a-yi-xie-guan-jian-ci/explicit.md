

the`explicit`-keyword in front of the constructor`C(void)`tells the compiler that only explicit call to this constructor is allowed.

```
class String {
public:
    explicit String (int n); //allocate n bytes
    String(const char *p); // initialize object with string p
};

String mystring = 'x';
//the char 'x' will not be implicitly converted to int and then will call the String(int) constructor. 
```

The`explicit`-keyword can also be used in user-defined type cast operators





https://stackoverflow.com/questions/121162/what-does-the-explicit-keyword-mean

