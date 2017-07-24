## What is Scope Guard

### Example Scope Guard for mutex
It's more of a design pattern than a particular class. It is a way of aquiring/releasing resources \(such as files, memory, or mutexes\) that is exception safe. unique\_lock in c++11 follows this pattern.

For example, with unique\_lock, instead of writing code like this:

```
void foo()
{
    myMutex.lock();
    bar();
    myMutex.unlock();
}
```

You write code like this:

```
void foo()
{
    unique_lock<mutex> ulock(myMutex);
    bar();
}
```

In the first case, what if bar throws an exception? Then, myMutex will never be unlocked, and your program would be left in an invalid state. In the second case, however, unique\_lock is programmed to lock the mutex in its constructor, and unlock it in its destructor. Even if bar throws an exception, the unique\_lock will be destructed as the stack unwinds when the exception travels upward, and so the lock will be released. This saves you having to wrap every call to bar in a try/catch block and handle exceptions manually.

[https://stackoverflow.com/questions/31365013/what-is-scopeguard-in-c](https://stackoverflow.com/questions/31365013/what-is-scopeguard-in-c)

### Scope Guard Purpose

##### Intent
To ensure that resources are always released in face of an exception but __not while returning normally__

To provide basic __exception safety__ guarantee

##### Motivation

Resource Acquisition is Initialization (RAII) idiom allows us to acquire resources in the constructor and release them in the destructor when scope ends successfully or due to an exception. It will always release resources. This is not very flexible. Sometime __we don't want to release resources if no exception is thrown__ but we do want to release them if exception is thrown.

Solution and Sample Code[edit]


https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/Scope_Guard