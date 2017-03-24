[http://stackoverflow.com/questions/86582/singleton-how-should-it-be-used](http://stackoverflow.com/questions/86582/singleton-how-should-it-be-used)

There's one issue I've never seen mentioned, something I ran into at a previous job. We had C++ singletons that were shared between DLLs, and the usual mechanics of ensuring a single instance of a class just don't work. The problem is that each DLL gets its own set of static variables, along with the EXE. If your get\_instance function is inline or part of a static library, each DLL will wind up with its own copy of the "singleton".

The solution is to make sure the singleton code is only defined in one DLL or EXE, or create a singleton manager with those properties to parcel out instances.





The first example isn't thread safe - if two threads call getInstance at the same time, that static is going to be a PITA. Some form of mutex would help.

