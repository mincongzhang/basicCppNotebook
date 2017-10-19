https://stackoverflow.com/questions/20895648/difference-in-make-shared-and-normal-shared-ptr-in-c

```
std::shared_ptr<Object> p1 = std::make_shared<Object>("foo");
std::shared_ptr<Object> p2(new Object("foo"));
```

The difference is that std::make_shared performs one heap-allocation, whereas calling the std::shared_ptr constructor performs two.