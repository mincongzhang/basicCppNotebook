### two situations where const_cast is safe and useful

```
void log(char* text);   // Won't change text -- just const-incorrect

void my_func(const std::string& message)
{
    log(const_cast<char*>(&message.c_str()));
}
```

```
class MyClass
{
    char cached_data[10000]; // should be mutable
    bool cache_dirty;        // should also be mutable

  public:

    char getData(int index) const
    {
        if (cache_dirty)
        {
          MyClass* thisptr = const_cast<MyClass*>(this);
          update_cache(thisptr->cached_data);
        }
        return cached_data[index];
    }
};
```

https://stackoverflow.com/questions/357600/is-const-cast-safe