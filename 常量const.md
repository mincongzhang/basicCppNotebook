## 常量对象、常量成员函数和常引用

### 1.如果不希望某个对象的值被改变，则定义该对象的时候在前面加const

### 2.在类的成员函数说明后面加const，该成员函数成为常量成员函数

\(1\)常量成员函数执行期间不应该修改其所作用的对象  
\(2\)因此，常量成员函数中不能修改成员变量的值\(静态成员除外，不属于对象一部分\)  
\(3\)不能调用同类的非常量成员函数\(非常量成员函数可能修改成员变量，静态成员函数除外\)

### 3.例子

```
class Sample{  
  public:  
    int value;  
    void GetValue() const;  
    void func(){};  
    Sample(){};  
};  
void Sample::GetValue() const {  
   value = 0; //wrong  
   func();//wrong  
}  
int main(){  
const Sample o;  
o.value = 100; //error  
o.func(); //error  
o.GetValue();//OK  
return 0;  
}//Dev C++中要为Sample类编写无参构造函数，visual 2010中不要  
```

### 4.常量成员函数的重载

\(1\)两个成员函数，名字和参数表都一样，但是一个是const，一个不是，算重载

### 5.常引用

\(1\)引用前面加const，不能修改引用的变量  
\(2\)对象作为函数的参数时，生成该参数需要调用复制构造函数，效率低； 用指针做参数代码难看，所以用常引用

### 6.常指针

(1)const int * 和 const int & 一样都不能改变变量的内容

```
const int * intPtr1; // Declares a pointer whose contents cannot be changed.
int * const intPtr2; // Declares a pointer that cannot be changed.
```


