### logically const vs bitwise const

"Physical"(bitwise) constness comes from declaring an object const, and could, in principle, be enforced by placing the object in read-only memory, so it cannot change. Attempting to change it will cause undefined behaviour; it might change, or it might not, or it might trigger a protection fault, or it might melt the memory chip.

"Logical" constness comes from declaring a reference or pointer const, and is enforced by the compiler. The object itself may or may not be "physically" const, but the reference cannot be used to modify it without a cast. If the object is not "physically" const, then C++ allows you to modify it, using const_cast to circumvent the protection.