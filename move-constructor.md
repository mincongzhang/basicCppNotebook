C++0x introduces a new mechanism called "rvalue reference" which, among other things, allows us to detect rvalue arguments via function overloading. All we have to do is write a constructor with an rvalue reference parameter. Inside that constructor we can do anything we want with the source, as long as we leave it in some valid state:

```
    string(string&& that)   // string&& is an rvalue reference to a string
    {
        data = that.data;
        that.data = nullptr;
    }
```

What have we done here? Instead of deeply copying the heap data, we have just copied the pointer and then set the original pointer to null. In effect, we have "stolen" the data that originally belonged to the source string. Again, the key insight is that under no circumstance could the client detect that the source had been modified. Since we don't really do a copy here, we call this constructor a "move constructor". Its job is to move resources from one object to another instead of copying them.