Assembly language: pointer, reference which is more efficient

[http://stackoverflow.com/questions/6167285/may-a-reference-be-more-efficient-than-a-pointer](http://stackoverflow.com/questions/6167285/may-a-reference-be-more-efficient-than-a-pointer)

volatile

destructor, throw expection? at the beginning surely not good  
what about at the end? not good as well. If you throw 2 exceptions, program will be killed

```
#include <stdio.h>
#include <iostream>
void clean1() {
  throw "clean1 Error!";
}
void clean2() {
  throw "clean2 Error!";
}


class A{
public:
  ~A(){
    try{
      clean1();
      clean2();
    } catch(const char * msg) {
      std::cout << "in catch" << msg << std::endl;
    }
    std::cout << "after catch" << std::endl;
  }
};

int main() {
  A a;
}
```

latency, benchmark\(measure the latency\)

futures, FX, mainly equities

Mutable

```
mutable int *　m_value;
int getValue() const {
  if(compute){
    m_value = doSomeComputation();//a static function within class
    return m_value;
  }
}
//problem? changed member var
//but still want to only update it when call getValue

//Think about use mutable
```

const

```
class A{
  int m_value;
  int myFun() const {
  }
};
//that means add const to mem: const int m_value;

class A{
  int * m_value;
  int myFun() const {
  }
};
//that means add const to mem: int * const m_value;

class A{
    int * m_cache;

public:
    void initCache(){
        m_cache = new int [100];
        //int * const m_cache;
    }

    void updateCache(int index, int value) const {
        m_cache[index] = value;
        //int * const m_cache; 
        //pointer unchanged, but content changed
    }
};


const int * const value;
const int * value;
int * const value;
const * int value;
```



