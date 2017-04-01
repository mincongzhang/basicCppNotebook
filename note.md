map/set/unordered\* insert can return an iterator

Assembly language: pointer, reference which is more efficient

volatile

atomic/lock free

IPC: ctrl+c, signal, shared memory, socket

IPC methods include pipes and named pipes; message queueing;semaphores; shared memory; and sockets.

condition variable, notify all, notify one, consumer

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

