## Open/closed principle

“software entities … should be open for extension, but closed for modification.” ...

such an entity can allow its behaviour to be extended without modifying its source code.

OPEN: 
If it is still available for extension. For example, it should be possible to add fields to the data structures it contains, or new elements to the set of functions it performs.

CLOSED:
If it is available for use by other modules. This assumes that the module has been given a well-defined, stable description (the interface in the sense of information hiding).