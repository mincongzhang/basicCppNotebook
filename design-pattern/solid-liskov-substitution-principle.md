### Liskov substitution principle

里氏替换原则（Liskov Substitution principle）是对子类型的特别定义.

派生类（子类）对象能够替换其基类（超类）对象被使用.

A typical example that violates LSP is a Square class that derives from a Rectangle class, assuming getter and setter methods exist for both width and height. 