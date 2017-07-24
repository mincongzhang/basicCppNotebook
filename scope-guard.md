### Unique Pointer (scoped pointer) and Scope Guard

It's more of a design pattern than a particular class. It is a way of aquiring/releasing resources (such as files, memory, or mutexes) that is exception safe. unique_lock in c++11 follows this pattern.

For example, with unique_lock, instead of writing code like this:

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

In the first case, what if bar throws an exception? Then, myMutex will never be unlocked, and your program would be left in an invalid state. In the second case, however, unique_lock is programmed to lock the mutex in its constructor, and unlock it in its destructor. Even if bar throws an exception, the unique_lock will be destructed as the stack unwinds when the exception travels upward, and so the lock will be released. This saves you having to wrap every call to bar in a try/catch block and handle exceptions manually.

https://stackoverflow.com/questions/31365013/what-is-scopeguard-in-c