### Open/closed principle

“software entities … should be open for extension, but closed for modification.” ...

such an entity can allow its behaviour to be extended without modifying its source code.

OPEN:   
If it is still available for extension. For example, it should be possible to add fields to the data structures it contains, or new elements to the set of functions it performs.

CLOSED:  
If it is available for use by other modules. This assumes that the module has been given a well-defined, stable description \(the interface in the sense of information hiding\).

A class is closed, since it may be compiled, stored in a library, baselined, and used by client classes. But it is also open, since any new class may use it as parent, adding new features. When a descendant class is defined, there is no need to change the original or to disturb its clients.



![](/assets/open_close.png)


#### Chinese ver
http://blog.csdn.net/yunhua_lee/article/details/25772449

