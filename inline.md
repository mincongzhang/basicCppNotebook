## 内联成员函数\(Inline\)和重载成员函数\(overload\)

1.内联成员函数  
\(1\)inline+成员函数  
\(2\)整个函数体出现在类定义内部

```
 class B{  
     inline void func1();  
     void func2()  
    {  
    };  
}     
 void B::func1(){}  
```

2.成员函数的重载\(overload\)及参数缺省\(default arguments\)  
\(1\)重载成员函数: 和普通的重载函数没区别, 参考第一章里的重载函数  
\(2\)成员函数 - 带缺省参数

```
#include <iostream>  
 using namespace std;  
 class Location{  
     private:  
           int x,y;  
     public:  
     void init(int x=0,int y=0);  
     void valueX(int val){x=val;}  
     int  valueX(){return x;}  
}  
 void Location::init(int X,int Y){  
     x = X;  
     y = Y;  
}  
```

\(3\)使用缺省参数要避免函数重载时的二义性

```
 class Location{  
     private:  
           int x,y;  
     public:  
           void init(int x=0,int y=0);  
           void valueX(int val=0){x = val;}  
           int valueX(){return x;}  
};  
 A.valueX();//错误，编译器无法判断调用哪个valueX 
```



