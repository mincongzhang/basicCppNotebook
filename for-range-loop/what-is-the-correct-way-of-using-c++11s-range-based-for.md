### What is the correct way of using C++11's range-based for?

https://stackoverflow.com/questions/15927033/what-is-the-correct-way-of-using-c11s-range-based-for


邓颖Factset :
&& is the rvalue reference , which allows us to optimize code and implement stricter ownership semantics
邓颖Factset :
Rvalue refs bind to temporaries, this means that no one else is referring to them, giving the developer more freedom
邓颖Factset :
It is used in the 11 move constructor, which is basically a static cast with rvalue ref, after which you can't touch the original object