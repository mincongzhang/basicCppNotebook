## 引用 \(reference\)和指针\(pointer\)

## 引用：

引用就像变量的别名，你对引用的操作与对变量直接操作完全一样。\(reference is like a alias of origin variable\)

\(1\)必须初始化成引用某个变量

\(2\)初始化后一直引用，不会再变

\(3\)只能引用**变量**

\(4\)例子
```
int n = 4;
int & ref = n; 

//这里ref的类型是int &,也有习惯写在一起的int&,
//表示这是个int的引用
```

### 指针：

### 指针和引用对比：

\(1\)指针

```
void swap(int *a,int *b) //获得指针(个人理解)
 { 
    int tmp; 
    tmp = *a;*a = *b;*b = tmp; 
 } 
 int n1,n2; 
 swap(&n1,&n2);  //传地址(个人理解)
```

\(2\)引用

```
void swap(int &a,int &b)  //直接传引用
 { 
    int tmp; 
    tmp = a; a = b; b = tmp; 
 } 
int n1,n2; 
swap(n1,n2);
```



