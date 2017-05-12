### Functor 函数算子

```
struct Comparator
{
  bool operator()(const Record& lhs, const Record& rhs)
  {
    return lhs.count>rhs.count;
  }
};

std::priority_queue<Record, std::vector<Record>, Comparator> myQ;
```

[http://stackoverflow.com/questions/7912595/initialization-for-stl-priority-queue](http://stackoverflow.com/questions/7912595/initialization-for-stl-priority-queue)



http://stackoverflow.com/questions/356950/c-functors-and-their-uses

### function pointer 函数指针

```
void qsort(void *base, size_t nmemb, size_t size,
            int(*compare)(const void *, const void *));
 
//compare function pointer
int int_sorter( const void *first_arg, const void *second_arg )
{
    int first = *(int*)first_arg; //cast (void *) to (int *) and dereference
    int second = *(int*)second_arg;
    if ( first < second )
    {
        return -1;
    }
    else if ( first == second )
    {
        return 0;
    }
    else
    {
        return 1;
    }
}

```

