### Liskov substitution principle

里氏替换原则（Liskov Substitution principle）是对子类型的特别定义.

派生类（子类）对象能够替换其基类（超类）对象被使用.

A typical example that violates LSP is a **Square class** that derives from a **Rectangle class**, assuming getter and setter methods exist for both width and height.

**setter** violate Liskov principle in some context, because the dimensions of a Square cannot \(or rather should not\) be modified independently

**getter**  no violation of LSP could occur.



![](/assets/liskov.png)

