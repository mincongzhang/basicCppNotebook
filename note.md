map/set/unordered\* insert can return an iterator

Assembly language: pointer, reference which is more efficient

volatile

atomic/lock free

IPC: ctrl+c, signal, shared memory, socket

IPC methods include pipes and named pipes; message queueing;semaphores; shared memory; and sockets.

condition variable, notify all, notify one, consumer/producer,deadlock/race condition

[https://en.wikipedia.org/wiki/Monitor\_\(synchronization\](https://en.wikipedia.org/wiki/Monitor_%28synchronization%29\)

notify\_all vs notify one:

[http://stackoverflow.com/questions/9015748/whats-the-difference-between-notify-all-and-notify-one-of-stdcondition-va](http://stackoverflow.com/questions/9015748/whats-the-difference-between-notify-all-and-notify-one-of-stdcondition-va)

join:

[http://stackoverflow.com/questions/15956231/what-does-this-thread-join-code-mean](http://stackoverflow.com/questions/15956231/what-does-this-thread-join-code-mean)

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

Design pattern:  
S.O.L.I.D  
Adapter pattern

latency, benchmark\(measure the latency\)

futures, FX, mainly equities

Mutable

```
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
    void initCache() const {
      m_cache = new int [100];
      //int * const m_cache;
    }
};

const int * const value;
const int * value;
int * const value;
const * int value;
```



