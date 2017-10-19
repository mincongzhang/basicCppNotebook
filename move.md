
https://stackoverflow.com/questions/3106110/what-are-move-semantics

https://stackoverflow.com/questions/3413470/what-is-stdmove-and-when-should-it-be-used

A typical use is 'moving' resources from one object to another instead of copying. @Guillaume links to this page which has a straightforward short example: swapping two objects with less copying.

```
template <class T>
swap(T& a, T& b) {
    T tmp(a);   // we now have two copies of a
    a = b;      // we now have two copies of b (+ discarded a copy of a)
    b = tmp;    // we now have two copies of tmp (+ discarded a copy of b)
}
```

using move allows you to swap the resources instead of copying them around:

```
template <class T>
swap(T& a, T& b) {
    T tmp(std::move(a));
    a = std::move(b);   
    b = std::move(tmp);
}
```