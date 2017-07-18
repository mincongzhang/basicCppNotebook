## Why do we need to use weak pointer sometimes?

Issue: shared\_ptr circular referencing

"Weak\_ptr" is called "weak" because it points to a shared instance without incrementing the instance reference counter. Conversely, a "shared\_ptr" is "strong" because it increments such counter.


Example: 

So how do we break the circular referencing here?

```
#include <memory>
#include <iostream>

struct B;
struct A {
  std::shared_ptr<B> b;  
  ~A() { std::cout << "~A()\n"; }
};

struct B {
  std::shared_ptr<A> a; //Make this a weak pointer, std::weak_ptr<A> a;
  ~B() { std::cout << "~B()\n"; }  
};

void useAnB() {
  auto a = std::make_shared<A>();
  auto b = std::make_shared<B>();
  a->b = b;
  b->a = a;
}

int main() {
   useAnB();
   std::cout << "Finished using A and B\n";
}
```

https://stackoverflow.com/questions/27085782/how-to-break-shared-ptr-cyclic-reference-using-weak-ptr

