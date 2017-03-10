## 常量对象、常量成员函数和常引用

### 1.如果不希望某个对象的值被改变，则定义该对象的时候在前面加const

### 2.在类的成员函数说明后面加const，该成员函数成为常量成员函数

\(1\)常量成员函数执行期间**不应该修改其所作用的对象**  
\(2\)因此，常量成员函数中**不能修改成员变量的值**\(静态成员除外，不属于对象一部分\)  
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

```
#include <iostream>
#include <string>

class A{
    private:
    int m_a;
    public:
    int func(int a) const {
        a = 1; //valid, it's not member var
        a++;   //valid, it's not member var
        //m_a=a; no, member var cannot be modified
        return a;
    }    
};

int main(){
  A o_a;
  std::cout<<o_a.func(2);
}
```

### 4.很有意思的一个const function问题

以下是编译不过的, 因为const function针对的不是member function, 但为什么编译不过呢?

查到的解释可能是member function的const处理的是"this"对象, 然而这样的static function没有"this", 所以编译器不知道哪个不能改变.

```
void f const (int & sth){
    sth = 2;    
}

int main()
{
    int a = 2;
    f(a);
}
```

What is meant by const at the end of a function?

It means that the **member** function can be called on a const object \(or via a reference-or-pointer-to-const\), and that the member function cannot modify data members \(unless they're marked mutable \).

参考this指针里对成员函数的处理

```
class A{
    void const func();
};

//就等于
void func(const struct A * this){
//...
};

main(){
    struct A;
    func(& A);
}
```

可以看出这样的函数const只能针对对象里的member vars, 而不能针对其他的变量.

### 5.常量成员函数的重载

\(1\)两个成员函数，名字和参数表都一样，但是一个是const，一个不是，算重载

### 6.常引用

\(1\)引用前面加const，不能修改引用的变量  
\(2\)对象作为函数的参数时，生成该参数需要调用复制构造函数，效率低； 用指针做参数代码难看，所以用常引用

### 7.常指针

\(1\)const int \* 和 const int & 一样都不能改变变量的内容

```
const int * intPtr1; // Declares a pointer whose contents cannot be changed.
int * const intPtr2; // Declares a pointer that cannot be changed.
```

### 



