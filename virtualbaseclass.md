## Virtual Base Class

the possibility of ambiguity

Virtual inheritance is there to solve this problem. When you specify virtual when inheriting your classes, you're telling the compiler that you only want a single instance.

```
class A { public: void Foo() {} };
class B : public virtual A {};
class C : public virtual A {};
class D : public B, public C {};
```

This means that there is only one "instance" of A included in the hierarchy. Hence

```
D d;
d.Foo(); // no longer ambiguous
```

[http://stackoverflow.com/questions/21558/in-c-what-is-a-virtual-base-class](http://stackoverflow.com/questions/21558/in-c-what-is-a-virtual-base-class)

