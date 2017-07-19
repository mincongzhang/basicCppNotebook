### virtual function const vs virtual function non-const

```
 virtual void func() const  //in Base
 virtual void func()        //in Derived
```

const part is actually a part of the function signature, which means the derived class defines a new function rather than overriding the base class function. It is because their signatures don't match.

When you remove the const part, then their signature matches, and then compiler sees the derived class definition of func as overridden version of the base class function func, hence the derived class function is called if the runtime type of the object is Derived type. This behavior is called runtime polymorphism.

https://stackoverflow.com/questions/9488168/virtual-function-const-vs-virtual-function-non-const

