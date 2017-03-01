## this指针

1.其作用就是指向成员函数所作用的对象\(就是指向它自己\)  
2.this指针和静态成员函数  
静态成员函数中不能使用this指针，因为静态成员函数并不具体作用于某个对象  
因此，静态成员函数的真实的参数的个数，就是程序中写出的参数个数

### C++到C的翻译

类\(class\)到C的结构体\(struct\)的翻译

```
//C++
class CCar{
    public:
    int price;
    void SetPrice(int p);
};

int main(){
    CCar car;
    car.SetPrice(200);
    return 0;
}

//C
struct CCar{
    int price;
}

void SetPrice(struct CCar * this, int p){
    this->price = p;
}

int main(){
    struct CCar car;
    SetPrice(CCar & car, 2000);
    return 0;
}
```

### this的作用

```
class A{
    public:
    void Hello(){
        cout<<"hello"<<endl;
    }
};

int main(){
    A * p = NULL;
    p->Hello();//结果如何? 是可以跑的
    //翻译成C语言是 
    //Hello(A * this){cout<<"hello"<<endl;}
}
```



