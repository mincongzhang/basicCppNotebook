### Calling virtual functions from constructors

The basic problem is that in all languages the Base type(s) must be constructed previous to the Derived type.

So the virtual function will be called when constructing base type object.

https://www.securecoding.cert.org/confluence/display/cplusplus/OOP50-CPP.+Do+not+invoke+virtual+functions+from+constructors+or+destructors
http://stackoverflow.com/questions/962132/calling-virtual-functions-inside-constructors

The same for destructors, the virtual function will be called when destructing derived object