### 泛型程序设计(generic programming)
1.算法实现时不指定具体要操作的数据的类型

2.泛型：算法实现一遍；适用于多种数据结构
*优势：减少重复代码的编写

3.(资深程序员)大量编写模板，使用模板的程序设计
(1)函数模板
(2)类模板

### 函数模板(function template)
1.

```
template<class 类型参数1，class 类型参数2，...> //写出会出现的类型参数？
返回值类型 模板名(形参表)
{}
```

2.swap函数写个模板

```
template <class T>
void Swap(T & x, T & y)
{
	T tmp = x;
	x=y;
	y=tmp;
}

int main(){
	int n=1,m=2;
	Swap(n,m);//编译器自动生成void Swap(int &,int &)函数
	double f=1.2,g=2.3;
	Swap(f,g);//编译器自动生成void Swap(double &,double &)函数
	return 0;
}

```

3.不止一个类型参数

```
template<class T1,class T2>
T2 print(T1 arg1,T2 arg2)
{
	cout<<arg1<<" "<<arg2<<endl;
	return arg2;
}
```

4.求数组最大元素

```
template<class T>
T MaxElement(T a[],int size)
{
	T tmpMax=a[0];
	for(int i=1;i<size;++i)
	{
		if(tmpMax<a[i]) tmpMax=a[i];
	}
	return tmpMax;
}
```

5.函数模板重载(只要形参表不同即可)

```
template<class T1,class T2>
void print(T1 arg1,T2 arg2)
{}

template<class T>
void print(T arg1,T arg2)
{}
```

6.C++编译器遵循的优先顺序
(1)先找参数完全匹配的普通函数
(2)再找参数完全匹配的模板函数
(3)再找实参经过自动类型转换后能够匹配的普通函数
(4)都找不到,报错

7.避免类型参数的二义性

```
template<class T>
T myFunction(T arg1,T arg2)
{
	return arg1;
}
```

```
myFunction(5,7);//T is int
myFunction(5.8,5.7);//T is double
myFunction(5,8.4)//error T is double?int?
```

二义性出现，需要修改

```
template<class T1,class T2>
T1 myFunction(T1 arg1,T2 arg2)
{}
```


