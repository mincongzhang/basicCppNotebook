## Exception

```
#include <string>
#include <iostream>
#include <vector>
#include <typeinfo>       // operator typeid
#include <exception>      // std::exception

/* exception 1*/
void exception1(){
  try {
    throw 1.2;
    throw 20;
  } catch (int e) {
    std::cout<<"exception1 int:"<<e<<std::endl;
  } catch (double e) {
    std::cout<<"exception1: double"<<e<<std::endl;
  }
}

/* exception 2*/
//Exception specification
double myfunction (char param) throw (int);//only catch int
int myfunction (int param) throw();        //catch all exceptions

class A{};
void throwA() throw(A){
  throw A();
}
void exception2(){
  try {
    throwA();
  }
  catch (A & e){
    std::cout<<"exception2:throw A"<<std::endl;
  }
}

/* exception 3*/
class myexception : public std::exception {
  virtual const char * what() const throw(){
    return "exception3: my exception throw";
  }

};

void exception3(){
  try {
    myexception me;
    throw me;
  }
  catch (std::exception & e){
    std::cout<<e.what()<<std::endl;
  }
}

int main() {
  exception1();
  exception2();
  exception3();

  return 0;
}

```