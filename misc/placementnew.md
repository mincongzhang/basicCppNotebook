```
char* ptr = new char[sizeof(T)]; // allocate memory
T* tptr = new(ptr) T;            // construct in allocated storage ("place")
tptr->~T();                      // destruct
delete[] ptr;                    // deallocate memory
```

http://en.cppreference.com/w/cpp/language/new