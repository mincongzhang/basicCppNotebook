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

