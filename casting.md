##### const\_cast

const\_cast\(expression\) The const\_cast&lt;&gt;\(\) is used to add/remove const\(ness\) \(or volatile-ness\) of a variable.

##### static\_cast

static\_cast\(expression\) The static\_cast&lt;&gt;\(\) is used to cast between the integer types. 'e.g.' char-&gt;long, int-&gt;short etc.

Static cast is also used to cast pointers to related types, for example casting void\* to the appropriate type.

static_cast<>() gives you a compile time checking ability, C-Style cast doesn't.
static_cast<>() is more readable and can be spotted easily anywhere inside a C++ source code, C_Style cast is'nt.

##### dynamic\_cast

Dynamic cast is used to convert pointers and references at run-time, generally for the purpose of casting a pointer or reference up or down an inheritance chain \(inheritance hierarchy\).

dynamic\_cast\(expression\)

The target type must be a pointer or reference type, and the expression must evaluate to a pointer or reference. Dynamic cast works only when the type of object to which the expression refers is compatible with the target type and the base class has at least one virtual member function. If not, and the type of expression being cast is a pointer, __NULL__ is returned, if a dynamic cast on a reference fails, __a bad\_cast exception is thrown__. When it doesn't fail, dynamic cast returns a pointer or reference of the target type to the object to which expression referred.

##### reinterpret\_cast

Reinterpret cast simply casts one type bitwise to another. Any pointer or integral type can be casted to any other with reinterpret cast, easily allowing for misuse. For instance, with reinterpret cast one might, unsafely, cast an integer pointer to a string pointer.



https://en.wikibooks.org/wiki/C%2B%2B\_Programming/Programming\_Languages/C%2B%2B/Code/Statements/Variables/Type\_Casting

