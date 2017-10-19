std::for_each ignores the return value of the function, and guarantees order of execution.
std::transform assigns the return value to the iterator, and does not guarantee the order of execution.

https://stackoverflow.com/questions/31064749/what-is-the-difference-stdtransform-and-stdfor-each